---
layout: post
title: "Crear un paquete Typescript en NPM"
---

Pasos para crear un paquete npm en npmjs.com<!--more-->.

# Crear un repositorio GitHub
Crear el repositorio localmente y vincularlo con github.com

# Iniciar npm
Iniciar el projecto especificando.
- package name: angular-test-extensions
- version: 1.0.0
- Description: A set of helper methods to improve development velocity
- entry-point: lib/angular-test-extensions.js
- test-command: empty
- git repository: url to repository
- keywords: jest, test, angular, extensions, helper
- author: Alex P. Scigalszky
- licence: ISC (default)

```bash
npm init
```

# Instalar dependecias
```bash
npm install typescript ts-node --save-dev
npm -g install @angular/cli
npm install @angular/core --save
npm install @jest/globals --save
```

# Configurar el compilador de Typescript
```bash
npx tsc --init
```
Agregar la carpeta destino: `outDir: dist`

# Agregar lógica
Crear una carpeta `src` en el proyecto y agregar dentro toda la lógica del paquete en archivos `.ts` o `.js`


# Agregar tsup
instalar
```bash
npm install tsup -D
```
agregar archivo `tsup.config.ts`
```typescript
import { defineConfig } from "tsup";

export default defineConfig({
  entry: ["src/index.ts"],
  format: ["cjs", "esm"], // Build for commonJS and ESmodules
  dts: true, // Generate declaration file (.d.ts)
  splitting: false,
  sourcemap: true,
  clean: true,
});
```

Agregar script en el package.json
```json
"build": "tsup",
```

agregar propiedades al propiedades al package.json
```json
    "main": "./dist/index.js",
    "module": "./dist/index.mjs",
    "types": "./dist/index.d.ts",
    "files": [
        "dist"
    ],
```
# Compilar
Validar que compile
```bash
npm run build
```

# Publicar el paquete
Conectarse a npm
```bash
npm login # require usuario, password e email
```
Publicar paquete
```bash
npm publish
```

# Paquete listo para usar
[NPM Link](https://www.npmjs.com/package/angular-test-extensions)