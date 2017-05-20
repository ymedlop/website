+++
draft = false
date = "2017-05-20T19:51:45+02:00"
title = "React.js declarativo"
menu = "main"
categories = ["React.js"]
tags = ["React.js"]
type = "post"
Description = ""

+++

Desarrollando con librerías más sencillas como jQuery, realizamos un estilo de programación imperativo. En ese estilo se realizan scripts que paso por paso tienen que informar sobre qué acciones o cambios en el DOM se deben realizar.

La forma imperativa de declarar nos obliga a escribir mucho código, porque cada pequeño cambio se debe definir en un script y cuando el cambio puede ser provocado desde muchos sitios, cuando agregamos eventos, el código comienza a ser poco mantenible.

![imperative](../../../img/react/imperative.png)

El estilo de React es más declarativo, en el que nosotros contamos con un estado de la aplicación y sus componentes reaccionan ante el cambio de ese estado. Los componentes tienen una funcionalidad dada y cuando cambia una de sus propiedades ellos producen un cambio.

En el código de nuestra aplicación tendremos ese componente, y en él se declarará de donde vienen los datos que él necesita para realizar su comportamiento. Podremos usarlo tantas veces como queramos declarando que lo queremos usar y declarando también los datos que él necesita para funcionar.

![declarative](../../../img/react/declarative.png)

Puede parecer al principio que de esta forma escribimos mas codigo pero a la larga notaremos que es mas reusable.

![exampleDeclarative](../../../img/react/exampleDecla.png)


<iframe
    src="https://codesandbox.io/embed/rvxk0E96"
    style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
    sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin" 
></iframe>

<iframe
    src="https://jsfiddle.net/ymedlop/qzttu2av/5/embed/"
    style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
    sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin" 
></iframe>