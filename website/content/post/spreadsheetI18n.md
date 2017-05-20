+++
title = "Spreadsheet i18n"
slug = ""
draft = true
categories = []
tags = []
comments = false
date = "2017-01-21T19:50:36+01:00"
showcomments = true
showpagemeta = true
type = "post"
+++

Normalmente cuando desarrollamos en [**frontend**](https://es.wikipedia.org/wiki/Front-end_y_back-end). Entre todos los requerimientos que tenemos, nuestra aplicación debe ser **multi-idioma**. 

Para ello dependiendo de las **librerías / framework** usados, tendremos distintas formas de implementarlo. Normalmente requieren tener archivos de traducción, posiblemente en [**JSON**](https://es.wikipedia.org/wiki/JSON).

El **"mayor dolor"** de las traducciones es el mantenimiento de las mismas. No tenemos una visión global de las traducciones. ¿ A quien no le ha pasado de olvidarse algún literal ?. ¿ A quien no le ha pedido una subida a producción un cliente para cambiar una frase por que no le gusta ?.

Para simplificar este proceso, dar visibilidad y permitir a terceros no técnicos la gestión de dichos archivos. Hemos apostado por [**Google Drive**](https://www.google.com/intl/es_es/drive/).

Estos nos planteara seguramente varias dudas....

### ¿ Por que Google Drive ?

Es un servicio de almacenamiento de archivos en línea.

* Accesible desde cualquier sitio 
* Uso compartido.
* Control de versiones de los documentos
* Comentarios en documentos
* Trabajo colaborativo.
* Podemos añadir programación para extender la funcionalidad de los documentos vía [**Google Apps Script**](https://developers.google.com/apps-script/).

### ¿ Que es Google Apps Script ?

Es un lenguaje de scripting basado en [**Javascript**](https://en.wikipedia.org/wiki/JavaScript) 1.6 ( con partes de 17, 1.8 ) y implementando [**ECMAScript**](https://en.wikipedia.org/wiki/ECMAScript) 5). El cual no se corre en cliente sino en la nube de **Google**. 

Ofrece maneras fáciles de automatizar las tareas a través de productos de Google y servicios de terceros.

Una vez tenemos nuestras dudas resueltas, nos ponemos manos a la obra:

### Trabajaremos en una Spreadsheet

Así podremos en única vista todos los literales de los diferentes idiomas que soporta nuestra aplicación, permitiendo de una forma fácil y automática exportarla a **JSON**.

Podemos ver una demo online [**aquí**](https://docs.google.com/spreadsheets/d/1tM9pNNK0t-hJyRw6uTdh3uW_wZMjE_xaY9Mq-uVt1Tw).

[![alt text][2]][1]

  [1]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/google-apps-scripts/spreadsheet-lang/lang.png
  [2]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/google-apps-scripts/spreadsheet-lang/lang.png (hover text)

**Estructura**

* "**KEY**", en esta columna es donde tendremos en plano separado por "**.**" la miga de keys, que tendría nuestro [**JSON**](https://es.wikipedia.org/wiki/JSON) final.

 Ejemplo:

 **models.project.business_owner** resultaría en:
```
{  
   "models":{  
      "project":{  
         "business_owner":"" # Depende del idioma
      }
   }
}
```

* **Códigos de idioma**, podemos añadir todas las columnas que queramos. Indicaremos los literales asociados a la columna "**KEY**".

**Acciones**

En el menú de pestañas se ha añadido, una pestaña llamada "**Apps Languages**. Donde tendremos las diferentes opciones de exportación.

[![alt text][4]][3]

  [3]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/google-apps-scripts/spreadsheet-lang/lang1.png
  [4]: https://storage.googleapis.com/ymedlop-sandbox.appspot.com/google-apps-scripts/spreadsheet-lang/lang1.png (hover text)

* **JSON Generator**: Generara un archivo zip en nuestra **unidad** con nuestras traducciones.

* **JSON Show**: Abrirá una barra lateral con un enlace a cada idioma en un [**editor de JSON Online**](http://www.jsoneditoronline.org/?json=%7B%22models%22%3A%7B%22project%22%3A%7B%22business_owner%22%3A%22Business%20Owner%22%2C%22created_at%22%3A%22Creado%20a%20las%22%2C%22created_by%22%3A%22Creado%20por%22%2C%22description%22%3A%22Descripci%C3%B3n%22%2C%22name%22%3A%22Nombre%22%2C%22owner%22%3A%22Due%C3%B1o%22%2C%22technical_owner%22%3A%22Technical%20Owner%22%7D%2C%22application%22%3A%7B%22description%22%3A%22Descripci%C3%B3n%22%2C%22name%22%3A%22Nombre%22%2C%22project%22%3A%22Proyecto%22%2C%22created_at%22%3A%22Creado%20a%20las%22%7D%2C%22user%22%3A%7B%22email%22%3A%22Email%22%7D%7D%2C%22view%22%3A%7B%22project%22%3A%7B%22navbar%22%3A%7B%22applications%22%3A%22Applications%22%2C%22dashboard%22%3A%22Dashboard%22%7D%7D%7D%2C%22views%22%3A%7B%22applications%22%3A%7B%22creation%22%3A%22Crear%22%2C%22index%22%3A%7B%22title%22%3A%22Listado%20de%20aplicaciones%22%7D%2C%22create%22%3A%7B%22title%22%3A%22Crear%20aplicaci%C3%B3n%22%2C%22cancel%22%3A%22Volver%22%7D%2C%22validations%22%3A%7B%22required%22%3A%22requerido%22%2C%22name%22%3A%7B%22length%22%3A%22nombre%20debe%20ser%20entre%20%7Bmin%7D%20y%20%7Bmax%7D%20caracteres%22%7D%7D%7D%2C%22projects%22%3A%7B%22validations%22%3A%7B%22name%22%3A%7B%22format%22%3A%22nombre%20s%C3%B3lo%20permite%20caracteres%20alfanum%C3%A9ricos%2C%20gui%C3%B3n%2C%20gui%C3%B3n%20bajo%20y%20el%20per%C3%ADodo%22%2C%22starts_with_alphanumeric%22%3A%22nombre%20debe%20comenzar%20con%20alfanum%C3%A9rico%22%2C%22ends_with_alphanumeric%22%3A%22nombre%20debe%20terminar%20con%20alfanum%C3%A9rico%22%2C%22length%22%3A%22nombre%20debe%20ser%20entre%20%7Bmin%7D%20y%20%7Bmax%7D%20caracteres%22%7D%2C%22required%22%3A%22requerido%22%2C%22owner%22%3A%7B%22length%22%3A%22due%C3%B1o%20debe%20ser%20entre%20%7Bmin%7D%20y%20%7Bmax%7D%20caracteres%22%2C%22format%22%3A%22due%C3%B1o%20solo%20permite%20caracteres%20alfanumericos%22%7D%7D%2C%22create%22%3A%7B%22create%22%3A%22Crear%22%2C%22title%22%3A%22Creaci%C3%B3n%20proyecto%22%2C%22cancel%22%3A%22Volver%22%7D%2C%22index%22%3A%7B%22create%22%3A%22Crear%20%20proyecto%22%2C%22title%22%3A%22Listado%20de%20proyectos%22%7D%2C%22show%22%3A%7B%22title%22%3A%22Mostrando%20proyecto%22%2C%22create_application%22%3A%22Crear%20aplicaci%C3%B3n%22%7D%7D%2C%22login%22%3A%7B%22title%22%3A%22Login%22%7D%7D%7D).

### Código Fuente

Puedes ver el código en [**Github**](https://github.com/ymedlop-sandbox/google-apps-scripts-samples/tree/master/spreadsheet-multilang), siéntete libre de jugar con el.

