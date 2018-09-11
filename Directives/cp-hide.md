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
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/384/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/74/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/362/)
* [Angular](https://jsfiddle.net/t0b8xxfj/146/)