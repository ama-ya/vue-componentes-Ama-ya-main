# Gestión de usuarios y repositorios de GitHub

Práctica realizada en el módulo **Desarrollo Web en Entorno Cliente**, donde se desarrolla una **aplicación Vue compleja** a través de componentes de un solo archivo. Es una aplicación de página única que permite al usuario visualizar determinados datos disponibles a través de la **API de GitHub**.

La aplicación utiliza **dos componentes** que se encargan de formatear los datos provenientes de dicha API (en formato JSON). Para el formato visual se utiliza la librería Bootstrap.

Se utilizan las siguientes **URLs** de la **API de GitHub**:
- https://api.github.com/users/{USER} - Al hacer una petición **GET** a este punto de destino sustituyendo `{USER}` por un usuario concreto, se obtienen los **datos de dicho usuario**. Para la práctica se utilizan los siguientes campos del objeto de datos devuelto:
  - *login* - Login del usuario para mostrarlo por pantalla.
  - *avatar_url* - URL de la imagen del avatar del usuario.
  - *html_url* - URL de la página de GitHub del usuario.
  - *repos_url* - URL para obtener la lista de repositorios del usuario.
- https://api.github.com/users/{USER}/repos - Al hacer una petición **GET** a este punto de destino sustituyendo `{USER}` por un usuario concreto, se obtiene el **listado de los repositorios** de dicho usuario. En este caso los datos devueltos tienen formato de **array**. De cada elemento (repositorio) del array tenemos las siguientes propiedades:
  - *full_name* - Nombre completo del repositorio
  - *html_url* - URL para acceder al repositorio a través de la web de GitHub
  - *description* Descripción del repositorio
  - *forks_count* - Número de forks que tiene el repositorio



# VueJS

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
