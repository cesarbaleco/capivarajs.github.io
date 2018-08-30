## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<h1 cp-if=""></h1>`
})
```
## Descrição

O `cp-if` possibilita mostrar ou ocultar elementos de acordo com uma condição ou valore booleanos, nessa diretiva os elementos são removidos do documento e construídos dinamicamente, toda vez que for chamado.

!> Por isso tenha cuidado quando o elemento precisa carregar algo muito custoso computacionalmente e for destruído e construído com muita frequência, isso pode acarretar lentidão ao site, uma alternativa para o problema é utilizar [cp-show](/Diretives/cp-show).

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
    <button cp-click="$ctrl.change()">Click me</button>
  `
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.showText = false
  }
  change() {
    this.showText = !this.showText;
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/387/)

Exemplo de utilização de operações lógicas.

```js
const {Component, Controller, OnInit} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `<h1 cp-if="$ctrl.firstValue <= $ctrl.secondValue">A simple text</h1>`
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.firstValue = 10
    this.secondValue = 20
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/389/)