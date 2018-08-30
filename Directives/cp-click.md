## Utilização

```js
@Component({
  tag: 'simple-component',
  template: `<button cp-click=""></button>`,
})
```

## Descrição

A diretiva `cp-click` faz com que seja possível executar funções do seu escopo através do disparo de eventos de clique em locais específicos da sua página `HTML`, usualmente utilizando o botão primário do mouse.<br>
O evento é disparado quando o clique é pressionado e depois solto.

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
  template: `<button cp-click="$ctrl.clickFunction()">Click me</button>`
})

class simpleComponent extends Controller {
  clickFunction() {
    alert('Hello World');
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/346/)

Exemplo de utilização da mesma função em mais de um elemento

```js
const {Component, Controller} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `
  	<button cp-click="$ctrl.clickFunction()">
        Click me
    </button>
    <p>Some random Text</p>
    <button cp-click="$ctrl.clickFunction()">
        Click me Too
    </button>`
})

class simpleComponent extends Controller {
  clickFunction() {
    alert('Hello World');
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/347/)