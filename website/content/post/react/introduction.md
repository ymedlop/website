+++
draft = false
date = "2017-05-20T18:42:34+02:00"
title = "Introdución a React.js"
categories = ["React.js"]
tags = ["React.js"]
type = "post"
Description = ""
menu = "main"

+++

![react](../../../img/react/react.png)

Bienvenidos a esta pequeña introdución a React.js, el origen de este articulo viene en relacion a una charla ninja que dare el dia 1 de Junio 2017 en BBVA. Espero poder subir luego el video.

# ¿ Que es React.js ?

Un error muy comun es pensar en React.js como un frameworks MVC. React es una libreria javascript para el desarrollo y representaciones de las interfaces de usuario de nuestras
aplicaciones web. 

## Componentes

En React el desarrollo esta orientado a componentes ( no confundir con componentes web ). Un componente en React.js tiene propiedades y estados.

#### Propiedades

Las propiedades de un componente son valores inmutables recibida normalmente por el padre del componente. Y como bien indica eso de ser inmutable, no deberian poder cambiar
desde el propio componente, sino al realizarse cambios en el padre recibir estos nuevos cambios... Esto tiene mucha relación con el estado asi que lo dejaremos por ahora..

En este ejemplo de codigo podemos ver como podemos pasar propiedades a un componente hijo de otro componente...

<iframe
src="https://codesandbox.io/embed/oYYxLLM4B"
style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;" 
sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin"
></iframe>

### Estado

El estado de un componente es gestionado por el mismo. El estado de un componente puede mutar durante la vida del componente.
Cambios en en el estado desencadenaran la ejecución del método render() del componente ( detallaremos esto más adelante) Hay que tener cuidado con su uso debido a:

* El estado complica los tests del componente al dificultar su previsibilidad.
* Complicados de entender
* La logica de negocio no deberia en la capa de representación.
* El estado complica compartir información con otras partes de la aplicación.

Esto no significa que debamos huir de uso del estado de un componente. Sino aplicarlo con cabeza. Por ello explicaremos los dos tipos recomendados de componentes:

* [Componentes sin estado o de presentación]()
* [Componentes con estado o contenedores]()

### Ciclos de vida de un componente

## Virtual Dom

React mantiene un virtual DOM propio, en lugar de confiar solamente en el DOM del navegador. Esto deja a la biblioteca determinar qué partes del DOM han cambiado comparando contenidos
entre la versión nueva y la almacenada en el virtual DOM, y utilizando el resultado para determinar cómo actualizar eficientemente el DOM del navegador.

Actualmente se conoce segun la documentacion de React.js como Reconciliacion, el cual detallaremos mas adelante.

## Puntos fuertes de React.js

* [Composición de componentes](../composition)
* [Desarrollo Declarativo Vs Imperativo](../declarative)
* [Flujo de datos unidireccional](../dataflow)

## Fuentes

* [tylermcginnis](https://tylermcginnis.com/imperative-vs-declarative-programming/)
* [desarrolloweb](https://www.desarrolloweb.com/articulos/caracteristicas-react.html)