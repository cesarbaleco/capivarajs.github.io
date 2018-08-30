## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<div cp-hide=""></div>`
})
```
## Descrição

A diretiva `cp-hide` faz com que seja possível ocultar dinamicamente elementos na tela, seja através de valores `booleanos` diretos, ou utilizando comparações. É mais aconselhado utilizar a diretiva para demonstrar que algo ainda não está pronto, ou já não está mais disponível. Não é de boa prática utilizar a diretiva para não mostrar conteúdo que possa ser utilizado em outras páginas.


## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização do `cp-hide` utilizando comparações.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
  tag: 'simple-component',
  template: `
    <p>Type <b>red</b> to hide the div</p>
    <input type="text" cp-model="$ctrl.color">
    <div cp-hide="$ctrl.color == 'red'"> Hi </div>`
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.color = '';
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/384/)