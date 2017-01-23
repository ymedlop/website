+++
draft = true
title = "Introducción a webpack"
showcomments = true
showpagemeta = true
comments = false
slug = ""
date = "2017-01-21T19:48:01+01:00"
categories = []
tags = []
type = "post"
+++

[![alt text][1]][2]

  [1]: https://sitelabs.es/wp-content/uploads/2015/08/what-is-webpack.png
  [2]: https://sitelabs.es/wp-content/uploads/2015/08/what-is-webpack.png(hover text)

[**Webpack**](https://webpack.github.io) es un module bundler (empaquetador de módulos). Permite generar una distribución única a partir de un conjunto de recursos requeridos por nuestra aplicación.

Como es normal en cualquier desarrollo a partir de cierto tamaño se complica   demasiado la gestión del mismo. Se incrementa el numero de recursos / dependencias de nuestra aplicación. El número de peticiones que el navegador debe realizar al servidor para cargar la página será mayor. **Esto provocara una caída de rendimiento.**

Con [**Webpack**](https://webpack.github.io) definiremos un **único pipeline** con un punto de entrada y un punto de salida. Obteniendo así un único archivo de distribución con todo los recursos procesados en el mismo.

Todos los recursos utilizados en la aplicación debe definirse y ser tratado como un módulo ( independiente del tipo de archivo ). Deberemos hacer un **require** de estos ficheros desde el punto de entrada principal

## [Loaders](http://webpack.github.io/docs/loaders.html) 

[**Webpack**](https://webpack.github.io) sólo puede procesar JavaScript de forma nativa, por ello los [**loaders**](http://webpack.github.io/docs/loaders.html)  se utilizan para procesar otros recursos a Javascript.

## [**CommonJS**](http://wiki.commonjs.org/wiki/Modules/1.1) y [**AMD**](http://webpack.github.io/docs/amd.html)

Podremos **exportar/importar** funciones y objetos complejos desde un fichero JavaScript o módulo. Permitiéndonos la carga de librerías de terceros como modulos de la aplicación.

## [Plugins](http://webpack.github.io/docs/plugins.html)

[**Webpack**](https://webpack.github.io) nos proporciona un listado de [**plugins**](http://webpack.github.io/docs/plugins.html) para customizar el comportamiento de nuestro **pipeline**.

## Herramientas de desarrollo

[**Webpack**](https://webpack.github.io) nos ofrece para trabajar en **local**. El paquete [**webpack-dev-server**](https://webpack.github.io/docs/webpack-dev-server.html), el cual nos permite levantar un servidor local con [**Express**](http://expressjs.com/). Notificando al navegador cuando halla cambios en el código. Evitando la incomodidad de tener que recargarlo manualmente.

A la hora de realizar la recarga de una página, para conservar el estado de las variables en ese punto, se nos ofrece:

* [**Hot Module Replacement (HMR)**](https://webpack.github.io/docs/hot-module-replacement.html): recargará los cambios manteniendo el estado actual de nuestras variables.

## Ejemplo sencillo

Como podemos ver en este [**ejemplo**](https://github.com/ymedlop-sandbox/webpack/tree/master/basic), tenemos un [**archivo de configuración**](https://github.com/ymedlop-sandbox/webpack/blob/master/basic/webpack.config.js) de [**webpack**](https://webpack.github.io):

```
module.exports = {
    entry: './index.js',
    output: {
        filename: 'bundle.js'
    }
};
``` 

Podemos ver el campo **entry** donde se indica el archivo, desde donde [**webpack**](https://webpack.github.io) empezara a construir nuestro archivo **bundle.js** declarado en el campo **output**.

Mirando nuestro archivo [**index.js**](https://github.com/ymedlop-sandbox/webpack/blob/master/basic/index.js):

```
var _ = require('lodash');

document.write('<h1>' + _.camelCase('We are using Lodash here!!') + '</h1>');
```

Necesitaremos definir nuestras dependencias en nuestro [**package.json**](https://github.com/ymedlop-sandbox/webpack/blob/master/basic/package.json):

```
{
  "name": "basic-web-01",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "webpack",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^1.13.1"
  },
  "dependencies": {
    "lodash": "^4.13.1"
  }
}
```

Ahora ejecutando:

```
npm run build
```
Veremos la magia de [**webpack**](https://webpack.github.io) en acción.

[![alt text][3]][4]

  [3]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/assets/images/webpack/build01.png
  [4]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/assets/images/webpack/build01.png(hover text)

Podremos ver nuestra aplicación funcionando en nuestro [**index.html**](https://github.com/ymedlop-sandbox/webpack/blob/master/basic/index.html):

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Webpack: Entry file and CommonJS</title>
</head>
<body>
    <script type="text/javascript" src="bundle.js"></script>
</body>
</html>
```
[![alt text][5]][6]

  [5]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/assets/images/webpack/html01.png
  [6]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/assets/images/webpack/html01.png(hover text)

# Conclusion

Se ha convertido en una herramienta indispensable en mi día a día. Simplificando la gestión y empaquetado de las dependencias de mis aplicaciones.  

Como tratar toda la potencia de la herramienta me podría llevar toda la vida y soy más de predicar con el ejemplo. Empezare a documentar distintos casos de uso en este [**repositorio**](https://github.com/ymedlop-sandbox/webpack).

## Fuentes

* [**GENBETA:dev**](http://www.genbetadev.com/javascript/webpack-gestion-integrada-y-eficiente-de-tus-assets)
* [**Webpack**](https://webpack.github.io)

**Nota:** Articulo y [**repositorio**](https://github.com/ymedlop-sandbox/webpack) en constante actualización.

