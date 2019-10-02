## Create React App y Tipos de Componentes
Inicialización de un proyecto en React
Creación de nuestro sitio web usando la plantilla por defecto de create-react-app:

`npx create-react-app nombre-de-tu-proyecto`

iniciamos el proyecto:
`npm run start`

abrir  el codigo en visual code
`code .`



Iniciar el servidor de desarrollo:

`npm start`
No olvides que puedes aprender a manejar de forma las diferentes herramientas de desarrollo en el Curso de Prework: Buenas Prácticas y Entorno de Desarrollo.

Creación y Tipos de Componentes
Los nombres de nuestros componentes deben empezar con una letra mayúscula, al igual que cada nueva palabra del componente. Esto lo conocemos como Pascal Case o Upper Camel Case.

Los componentes Stateful son los más robustos de React. Los usamos creando clases que extiendan de React.Component. Nos permiten manejar estado y ciclo de vida (más adelante los estudiaremos a profundidad).

import React, { Component } from 'react';

class Stateful extends Component {
  constructor(props) {
    super(props);

    this.state = { hello: 'hello world' };
  }

  render() {
    return (
      <h1>{this.state.hello}h1>
    );
  }
}

export default Stateful;
También tenemos componentes Stateless o Presentacionales. Los usamos creando funciones que devuelvan código en formato JSX (del cual hablaremos en la próxima clase).

import React from 'react';

const Stateless = () => {
  return (
    <h1>¡Hola!h1>
  );
}

// Otra forma de crearlos:
const Stateless = () => <h1>¡Hola!h1>;

export default Stateless;

## si despues de apagar el server no vueve a prender hay que correr  

ejecuté dentro del ployecto:
`npm install` 
`npm update`

# ¿Qué son los métodos del ciclo vida?
## ¿Qué son los métodos del ciclo vida?
Todos los componentes en React pasan por una serie de fases que generalmente se denominan “Ciclo de Vida del componente” es un proceso que React hace en cada componente, en algunos casos no podemos verlos como un bloque de código y en otros podemos llamarlos en nuestro componente para asignar una actividad según sea el caso necesario.

Los componentes en react pasan por un Montaje, Actualización, Desmontaje y Manejo de errores.

## Montaje:
En esta fase nuestro componente se crea junto a la lógica y los componentes internos y luego es insertado en el DOM.

## Actualización:
En esta fase nuestro componente está al pendiente de cambios que pueden venir a través de un cambio en “state” o “props” esto en consecuencia realizan una acción dentro de un componente.

## Desmontaje:
En esta etapa nuestro componente “Muere” cuando nosotros no necesitamos un elemento de nuestra aplicación, podemos pasar por este ciclo de vida y de esta forma eliminar el componente de la representación que tiene en el DOM.

## Manejo de Errores:
Cuando nuestro código se ejecuta y tiene un error, podemos entrar en una fase donde se puede entender mejor qué está sucediendo con la aplicación.

Algo que debemos tener en cuenta es que un componente NO debe pasar por toda las fases, un componente puede ser montado y desmontado sin pasar por la fase de actualización o manejo de errores.

Ahora que entendemos las fases que cumple el ciclo de vida en React vamos a entrar a detalle en cada uno de ellos para ver qué piezas de código se ejecutan y nos ayudarán a crear aplicaciones en React pasando por un ciclo de vida bien estructurado.

## Montado:
## `Constructor()`

Este es el primer método al que se hace un llamado, aquí es donde se inicializan los métodos controladores, eventos del estado.

## getDerivedStateFromProps()

Este método se llama antes de presentarse en el DOM y nos permite actualizar el estado interno en respuesta a un cambio en las propiedades, es considerado un método de cuidado, ya que su implementación puede causar errores sutiles.

## render()

Si queremos representar elementos en el DOM en este método es donde se escribe esta lógica, usualmente utilizamos JSX para trabajar y presentar nuestra aplicación.

## ComponentDidMount()

Este método se llama inmediatamente que ha sido montado en el DOM, aquí es donde trabajamos con eventos que permitan interactuar con nuestro componente.

## Actualización:
`getDerivedStateFromProps()`

Este método es el primero en ejecutarse en la fase de actualización y funciona de la misma forma que en el montaje.

## shouldComponentUpdate()

Dentro de este método se puede controlar la fase de actualización, podemos devolver un valor entre verdadero o falso si queremos actualizar o no el componente y es utilizado principalmente para optimización.

render()

Se llama el método render que representa los cambios en el DOM.

## componentDidUpdate()

Este método es invocado inmediatamente después de que el componente se actualiza y recibe como argumentos las propiedades y el estado y es donde podemos manejar nuestro componente.

## Desmontado
## componentWillUnmount()

Este método se llama justo antes de que el componente sea destruido o eliminado del DOM.

## Manejo de Errores:
## getDerivedStateFromError()

Una vez que se lanza un error este es el primer método que se llama, el cual recibe el error como argumento y cualquier valor devuelto en este método es utilizado para actualizar el estado del componente.

## componentDidCatch()

Este método es llamado después de lanzarse un error y pasa como argumento el error y la información representada sobre el error.

Ahora que entendemos cada una de las fases que tiene el ciclo de vida de react, podemos utilizarlas según sea necesario en nuestra aplicación y de esta forma crear las interacciones que necesitemos.

# INICIACION DEL PROYECTO PLATZIVIDEO 
Crear un carpeta y instalar npm con yes a todo
`npm init -y`

Luego creamos las carpetas: 
"public" --> contega `index.html`  y la carpeta "src" --> contenga "components"--> `index.js`

Luego instalamos React:
`npm install react react-dom`

## Agregando compatibilidad con todos los navegadores usando Babel
Babel es una herramienta muy popular para escribir JavaScript moderno y transformarlo en código que pueda entender cualquier navegador.

Instalación de Babel y otras herramientas para que funcione con React:
`npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev`
Configuración de Babel (.babelrc):

```
{
  ""presets"": [
    ""@babel/preset-env"",
    ""@babel/preset-react""
  ],
}
```
# Webpack: Empaquetando nuestros módulos
Webpack es una herramienta que nos ayuda a transformar multiples archivos (JavaScript, HTML, CSS, imágenes) en uno solo (o a veces un poco más) que tendrá todo nuestro código listo para producción.

Instalación de Webpack y algunos plugins:

`npm install webpack webpack-cli html-webpack-plugin html-loader  --save-dev`

cuando instaste creamos un archivo en la raiz del projecto con el nombre: 
'webpack.config.js'

```JavaScript
const path = require('path');
const HtmlWebPackPlugin = require('html-webpack-plugin');

module.exports = {
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'        
    },
    resolve: {
        extensions: ['.js', '.jsx']
    },
    module: {
        rules: [
            {
                test: /\.(js|jsx)$/,
                exclude: /node_modules/,
                use: {
                    loader: "babel-loader"
                }
            },
            {
                test: /\.html$/,
                use: [
                    {
                        loader: 'html-loader'
                    }
                ]
            }

        ]
    },
    plugins: [
        new HtmlWebPackPlugin({
            template: './public/index.html',
            filename: './index.html'
        }),
    ]
};
```

creamos el script para packege.json
`
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack --mode production"
  },
`
## corremos el constructor build 
`npm run build`

```JavaScript
> webpack --mode production

Hash: 08e2e0d125a4c85969a5
Version: webpack 4.41.0
Time: 9116ms
Built at: 2019-09-25 7:49:06 PM
       Asset       Size  Chunks             Chunk Names
./index.html  361 bytes          [emitted]  
   bundle.js    124 KiB       0  [emitted]  main
Entrypoint main = bundle.js
[7] ./src/index.js + 1 modules 370 bytes {0} [built]
    | ./src/index.js 196 bytes [built]
    |     + 1 hidden module
    + 7 hidden modules
Child html-webpack-plugin for "index.html":
     1 asset
    Entrypoint undefined = ./index.html
    [0] ./node_modules/html-webpack-plugin/lib/loader.js!./public/index.html 352 bytes {0} [built]

```
## Webpack Dev Server: Reporte de errores y Cambios en tiempo real
Instalación de Webpack Dev Server:
`npm install webpack-dev-server --save-dev` 
Script para ejecutar el servidor de Webpack y visualizar los cambios en tiempo real (package.json):
`
 "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack --mode production"
    "start": "webpack-dev-server --open --mode development"
  },
`
## Estilos con SASS
Los preprocesadores como Sass son herramientas que nos permiten escribir CSS con una sintaxis un poco diferente y más amigable que luego se transformará en CSS normal. Gracias a Sass podemos escribir CSS con variables, mixins, bucles, entre otras características.
Instalación de Sass:
`npm install --save-dev mini-css-extract-plugin css-loader node-sass sass-loader`
Configuración de Sass en Webpack (webpack.config.js):
const MiniCssExtractPlugin = require('mini-css-extract-plugin');

...

module: {
  rules: [
    {
      test: /\.(s*)css$/,
      use: [
        { loader: MiniCssExtractPlugin.loader },
        'css-loader',
        'sass-loader',
      ],
    }, 
  ],
},

// ...

plugins: [
  new MiniCssExtractPlugin({
    filename: 'assets/[name].css',
  }),
],

## Configuración final: ESLint y Git Ignore
El Git Ignore es un archivo que nos permite definir qué archivos NO queremos publicar en nuestros repositorios. Solo debemos crear el archivo .gitignore y escribir los nombres de los archivos y/o carpetas que no queremos publicar.
Los linters como ESLint son herramientas que nos ayudan a seguir buenas prácticas o guías de estilo de nuestro código.
Se encargan de revisar el código que escribimos para indicarnos dónde tenemos errores o posibles errores. En algunos casos también pueden solucionar los errores automáticamente. De esta manera podemos solucionar los errores incluso antes de que sucedan.
Instalación de ESLint:
`npm install --save-dev eslint babel-eslint eslint-config-airbnb eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y`

- se crea un archivo '.eslintrc'  y se copia este codigo:
https://gist.githubusercontent.com/gndx/60ae8b1807263e3a55f790ed17c4c57a/raw/0de495fc84df71ce97ef87c37505362f3512e1c3/eslintrc

- luego agregamos el '.gitingnore': https://gist.github.com/gndx/747a8913d12e96ff8374e2125efde544

## Añadiendo imágenes con Webpack  
Vamos a usar File Loader para acceder a las imágenes de nuestro proyecto desde el código.
Inicialmente, estos archivos estáticos se encuentran junto al código de desarrollo. Pero al momento de compilar, Webpack guardará las imágenes en una nueva carpeta junto al código para producción y actualizará nuestros componentes (o donde sea que usemos las imágenes) con los nuevos nombres y rutas de los archivos.
Instalación de File Loader: `npm install --save-dev file-loader`
Configuración de File Loader en Webpack (webpack.config.js):
rules:
```javascript
 [ 
  {
    test: /\.(png|gif|jpg)$/,
    use: [
      {
        loader: 'file-loader',
        options: { name: 'assets/[hash].[ext]' },
      }
    ],
  },
],
```
Uso de File Loader con React:
```javascript
import React from 'react';
import nombreDeLaImagen from '../assets/static/nombre-del-archivo';

const Component = () => (
  <img src={nombreDeLaImagen} />
);

export default Component;
```
### Imports, Variables y Fuentes de Google en Sass
Así como JavaScript, Sass nos permite almacenar valores en variables que podemos usar en cualquier otra parte de nuestras hojas de estilo.
```javascript
$theme-font: 'Muli, sans-serif;
$main-color: #8f57fd;

body {
  background: $main-color;
  font-family: $theme-font;
}
```
Podemos guardar nuestras variables en un archivo especial e importarlo desde los archivos de estilo donde queremos usar estas variables.

# Vars.scss
$theme-font: 'Muli, sans-serif;
$main-color: #8f57fd;

# App.scss
```javascript
@import ""./Vars.scss""

body {
  background: $main-color;
  font-family: $theme-font;
}
```
También podemos importar hojas de estilo externas a nuestra aplicación. Por ejemplo: las fuentes de Google.

`@import url(https://fonts.googleapis.com/css?family=Muli&display-swa`p)

Recuerda que puedes tomar el Curso de Sass para estudiar esta herramienta a profundidad.

 
### Creando una Fake API
https://gist.github.com/gndx/d4ca4739450afaa614efe4570ac362ee
Vamos a usar JSON Server para crear una Fake API: una API ““falsa”” construida a partir de un archivo JSON que nos permite preparar nuestro código para consumir una API de verdad en el futuro.

Instalación de JSON Server:
`sudo npm install json-server -g`

Recuerda que en Windows debes correr tu terminal de comandos en modo administrador.
Ejecutar el servidor de JSON Server:
`json-server archivoParaTuAPI.json`
## React Hooks: useEffect y useState
En esta clase el profesor Oscar Barajas nos enseña qué es y cómo implementar React Hooks: una característica de React disponible a partir de la versión 16.8 que nos permite agregar estado y ciclo de vida a nuestros componentes creados como funciones.
React es una librería desarrollada por Facebook que nos ayuda a construir interfaces de usuario interactivas para todo tipo de aplicaciones: páginas web, aplicaciones móviles o de escritorio, experiencias de realidad virtual, entre otr