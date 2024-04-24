---
layout: post
title: "Angular: Request API"
---

<!--more-->

app.config

```typescript
import { HttpClient } from "@angular/common/http";
import { Injectable } from "@angular/core";
import { Todo } from "../models/todo";
import { environment } from "./environment";

@Injectable({
  providedIn: "root",
})
export class PostsService {
  constructor(private http: HttpClient) {}

  getAll = () => this.http.get<Todo[]>(`${environment.API_URL}/todos`);
}
```
