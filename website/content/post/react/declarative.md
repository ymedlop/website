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

```javascript
$("#btn").click(function() {
  $(this).toggleClass("highlight")
  $(this).text() === 'Add Highlight'
    ? $(this).text('Remove Highlight')
    : $(this).text('Add Highlight')
})
```

El estilo de React es más declarativo, en el que nosotros contamos con un estado de la aplicación y sus componentes reaccionan ante el cambio de ese estado. Los componentes tienen una funcionalidad dada y cuando cambia una de sus propiedades ellos producen un cambio.

En el código de nuestra aplicación tendremos ese componente, y en él se declarará de donde vienen los datos que él necesita para realizar su comportamiento. Podremos usarlo tantas veces como queramos declarando que lo queremos usar y declarando también los datos que él necesita para funcionar.

```javascript
export default class HighlightButton extends React.Component {
  constructor(props) {
    super(props);
    const highlight = props.highlight || false;
    this.state = { highlight };
    this.handleOnclick = this.handleOnclick.bind(this);
  }
  handleOnclick() {
    this.setState(prevState => ({ highlight: !prevState.highlight }));
  }
  getClassName() {
    const { highlight } = this.state;
    return highlight ? 'highlight' : '';
  }
  renderText() {
    const { highlight } = this.state;
    let text = 'Add Highlight';
    if (highlight) text = 'Remove Highlight';
    return text;
  }
  render() {
    return (
      <button
        className={this.getClassName()}
        onClick={this.handleOnclick}
      >
         {this.renderText()}
      </button>
    )
  }
}
```

Puede parecer al principio que de esta forma escribimos mas codigo pero a la larga notaremos que es mas reusable.

```javascript
const App = () => (
  <div style={styles}>
    <h2>Declarative Example</h2>
    <p>
      The real beauty of React is that you can create these declarative user interfaces. By looking at our Btn component, I’m able to easily understand what the UI is going to look like. Another benefit is instead of state living in the DOM, it lives in the React component itself.
    </p>
    <HighlightButton />
    <HighlightButton highlight />
  </div>
);
```

<iframe
    src="https://codesandbox.io/embed/rvxk0E96"
    style="width:100%; height:500px; border:0; border-radius: 4px; overflow:hidden;"
    sandbox="allow-modals allow-forms allow-popups allow-scripts allow-same-origin" 
></iframe>

<iframe
width="100%"
height="300"
src="//jsfiddle.net/ymedlop/qzttu2av/embedded/"
allowfullscreen="allowfullscreen" frameborder="0">
</iframe>