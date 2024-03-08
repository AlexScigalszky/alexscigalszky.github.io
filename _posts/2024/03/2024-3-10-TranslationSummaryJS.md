---
layout: post
title: "Librería: TranslationSummaryJS (Javascript)"
---
# Link
(link to nopm package)[https://www.npmjs.com/package/@translation-summary/core]

Librería que permite visualizar un resumen los archivos de traducción dentro de una carpeta.
Ayuda a encontrar los archivos de traducción faltantes dentro de la carpeta `docs`

## Salida

<p> <img src="https://github.com/AlexScigalszky/TranslationSummaryJS/raw/main/assets/capture.png" alt="capture" /> </p>

## Cómo usar

Instalación
```bash
npm i @translation-summary/core -g
```

Crea un archivo llamado `translation-summary-config.js` con la siguiente configuración, se puede ajustar las propiedad a cualquier forma.

```javascript 
module.exports = {
    folderPath: './i18n',
    filePattern: '_...md$',
    filePatternForReplace: '_LANGUAGE.md',
    fileExtension: '.md',
    extractLanguage: (file) => {
        return file.substring(file.length - 5, file.length - 3);
    },
    replaceExtension: (file, lang, pattern, fileExtension) => {
        return file.replace(fileExtension, pattern.replace('LANGUAGE', lang));
    },
};
```

Ejecutar el comando ts
```bash
translation-summary --config translation-summary-config.js
```
o más simplificado
```bash
ts -c translation-summary-config.js
```

## Instalar el plugin en el proyecto

node (JS)
```javascript
const ts = require('@translation-summary/core');

const helper = new ts.TranslationSummary();
const summary = helper.getSummary();

console.table(summary);
```

## Mostrar los datos en consola

```typescript
import { TranslationSummary } from './translation-summay';

const helper = new TranslationSummary();
const summary = helper.getSummary();

console.table(summary);
```

# Tabla de resultados

```typescript
export interface FileSummary {
    file: string;
    [key: string]: string;
}
```

# Opciones

Se pueden definir las opciones por archivo, extensión o funciones para reemplazar.

```typescript
const options = new Options();

options.folderPath = './docs';
options.filePattern = '_...md$';
options.filePatternForReplace = '_param.md';
options.fileExtension = '.md';
options.extractLanguage = (file: string): string => {
    return file.substring(file.length - 5, file.length - 3);
};
options.replaceExtension = (file: string, lang: string, pattern: string, fileExtension: string): string => {
    return file.replace(fileExtension, pattern.replace('param', lang));
};

const helper = new TranslationSummary(options);
const summary = helper.getSummary();
```

## Opciones Disponibles

| Opciones               | Descripcion                                                                                                            | Valor por defecto     |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------- | --------------------- |
| `folderPath`           | Carpeta dónde empezará a buscar archivos                                                                               | `./docs`              |
| `filePattern`          | Extresión regular como string usada para encontrar archivos                                                            | `_...md$`             |
| `filePatternForReplace`| Expresión regular con un parametro con lo que reemplazará el valor en el archivo                                       | `_param.md`           |
| `fileExtension`        | Extensión de archivo para los archivos (vacío buscará todos los archivos)                                              | `.md`                 |
| `extractLanguage`      | Función que devuelve el idioma para un archivo (ejemplo: `doc_en.md` devuelve `en`)                                    |                       |
| `replaceExtension`     | Función que reemplaza el nombre del archivo por el correspondiente al idioma (ejemplo: `doc.md` devuelve `doc_en.d`)   |                       |


## Solucionar problemas

Algunas libreías tal vez necesitan instalarse globalmente

ts-node
```bash
npm i ts-node -g
```

tsutils
```bash
npm i tsutils -g
```

typescript
```bash
npm i typescript -g
```
