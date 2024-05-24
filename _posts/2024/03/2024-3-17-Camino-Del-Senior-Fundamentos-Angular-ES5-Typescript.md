---
layout: post
title: "Fundamentos de Angular: ES5 y TypeScript"
categories: ["senior"]
---

La diferencia de codigo entre funciones Javascript y clases de TypeScript son: <!--more-->

# Funciones Javascript

Si tenemos una función

```ts
function ShopingList() {
  this.groceries = [];
}
```

Podemos crear una lista así:

```ts
var myList = new ShopingList();
```

pero si queremos agregar una funcion a la lista.

```ts
function ShopingList() {
  this.groceries = [];
}

ShopingList.prototype.addItem = function (item) {
  this.groseries.concat([item]); // idenpotente
};
```

entonces podemos hacer algo como esto

```ts
var myList = new ShopingList();
myList.addItem("banana");
console.log(myList.groseries);
```

Ahora si quiero agregar el método remove

```ts
function ShopingList() {
  this.groceries = [];
}

ShopingList.prototype.addItem = function (item) {
  this.groseries.concat([item]); // idenpotente
};
ShopingList.prototype.remove = function (item) {
  this.groseries = this.groseries.filter(function (grocery) {
    return grocery !== item;
  }); // idenpotente
};
```

entonces podemos hacer algo como esto

```ts
var myList = new ShopingList();
myList.addItem("banana");
myList.addItem("apple");
console.log(myList.groseries);
myList.remove("banana");
console.log(myList.groseries);
```

# Utilizando una clase

```ts
class ShopingList() {
    groceries: string[];
    contructor(){
        this.groceries = [];
    }

    addItem(item) {
        this.groseries = [...this.groseries, item]; // idenpotente
    }
    remove(item) {
        this.groseries = this.groseries.filter(grocery => grocery !== item); // idenpotente
    }
}

const myList = new ShopingList();
console.log(myList);
myList.addItem("banana");
myList.addItem("pear");
console.log(myList);
myList.remove("banana");
console.log(myList);
```
