## Utilização

```js
@Component({
  tag: 'simple-component'
  template: `<button cp-dblclick=""></button>`,
})
```

## Descrição

A diretiva `cp-dblclick` faz com que seja possível executar funções do seu escopo através do disparo de eventos de clique duplo em locais específicos da sua página `HTML`, usualmente utilizando o botão primário do mouse.

## Exemplos

A chamada HTML de todos os componentes é feita da seguinte forma:

```HTML
<simple-component></simple-component>
```

Exemplo de utilização em um elemento `<button>`

```js
const {Component, Controller} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `
    <button cp-dblclick="$ctrl.dblclickFunction()">
        Double Click me
    </button>`
})

class simpleComponent extends Controller {
  dblclickFunction() {
    alert('Double click Fired');
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/351/)

Exemplo de utilização da mesma função em mais de um elemento

```js
const {Component, Controller} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `
  	<button cp-dblclick="$ctrl.dblclickFunction()">
        Click me
    </button>
    <p>Some random Text</p>
    <button cp-dblclick="$ctrl.dblclickFunction()">
        Click me Too
    </button>`
})

class simpleComponent extends Controller {
  dblclickFunction() {
    alert('Hello World');
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/352/)
