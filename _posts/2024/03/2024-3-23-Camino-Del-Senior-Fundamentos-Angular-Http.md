---
layout: post
title: "Camino del Senior(.Net + Angular): Fundamentos de Angular: Http"
categories: senior
---

Para realizar peticiones Http se utiliza un cliente que <!--more-->nos permite ir al servidor a buscar los datos y obtenerlos como objetos.

Para hacer eso, se crea un servicio

```ts
import { HttpClient, HttpParams } from "@angular/common/http";
import { Injectable } from "@angular/core";
import { environment } from "@env";
import { Observable, throwError } from "rxjs";
import { catchError } from "rxjs/operators";

@Injectable()
export class ApiService {
  constructor(private http?: HttpClient) {}

  private formatErrors(error: any) {
    return throwError(error.error);
  }

  get(path: string, params: HttpParams = new HttpParams()): Observable<any> {
    return this.http.get(`${environment.API_URL}${path}`, { params }).pipe(catchError(this.formatErrors));
  }

  put(path: string, body: object = {}): Observable<any> {
    return this.http.put(`${environment.API_URL}${path}`, body).pipe(catchError(this.formatErrors));
  }

  post(path: string, body: object = {}): Observable<any> {
    return this.http.post(`${environment.API_URL}${path}`, body).pipe(catchError(this.formatErrors));
  }

  delete(path): Observable<any> {
    return this.http.delete(`${environment.API_URL}${path}`).pipe(catchError(this.formatErrors));
  }
}
```
 luego agregarlos al módulo como un `provider`
```ts
import { NgModule } from '@angular/core';
import { CommonModule } from '@angular/common';
import { ApiService } from './api.service';

@NgModule({
  declarations:[

  ],
  imports:[
    CommonModule
  ],
  providers:[
    ApiService
  ]
})
export class ChatModule {

}
```

y por último injectarlos en el componente
```ts
import { Component } from '@angular/core'
import { ApiService } from './api.service';

@Component({
    selector:'app-root',
    template: `
        <div>
            {{ title }}
        </div>
    `
}) 
export class AppComponent {
    title: string;

    contructor(private apiService: ApiServise){
        this.title = 'My first title';
    }
}
```

> *Nota 1:* Los métodos `get`, `post`,`put` y `delete` permiten utilizar un tipo generico (T) para especificar el dato de respuesta

```ts
return this.http.get<T>(`${environment.API_URL}${path}`, { params })...
return this.http.put<T>(`${environment.API_URL}${path}`, body)...
return this.http.post<T>(`${environment.API_URL}${path}`, body)...
return this.http.delete<T>(`${environment.API_URL}${path}`)...
```
