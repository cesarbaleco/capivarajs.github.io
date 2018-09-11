## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `
        <h1 cp-if=""></h1>
        <h1 cp-else-if=""></h1>`
})
```
## Descrição

O `cp-else-if` deve ser utilizado logo após a diretiva `cp-if`, ela é visível quando a condição do `cp-if` for falsa e sua condição for verdadeira. Podem ser utilizados vários `cp-else-if` em sequência, desde que a primeira chamada seja um `cp-if`, não é possível chamar a diretiva com condições vazias, portanto, junto a ela deve estar sempre atrelado um variável ou função.

## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização de valor direto.

```js
const {Component, Controller, OnInit} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `
    <h1 cp-if="$ctrl.showText">A simple text</h1>
    <h1 cp-else-if="!$ctrl.showText">Other simple text</h1>
  `
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.showText = false
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/367/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/67/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/351/)
* [Angular](https://jsfiddle.net/t0b8xxfj/129/)


Exemplo de utilização de operações lógicas.

```js
const {Component, Controller, OnInit} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `
    <h1 cp-if="$ctrl.firstValue > $ctrl.secondValue">A simple text</h1>
    <h1 cp-else-if="$ctrl.firstValue < $ctrl.secondValue">Other simple text</h1>
  `
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.firstValue = 10
    this.secondValue = 20
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/369/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/65/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/353/)
* [Angular](https://jsfiddle.net/t0b8xxfj/131/)