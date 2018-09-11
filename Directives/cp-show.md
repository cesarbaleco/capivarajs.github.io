## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<h1 cp-show=""></h1>`
})
```
## Descrição

Podemos utilizar a diretiva `cp-show` para mostrar ou ocultar elementos de acordo com uma condição ou valores `booleanos`, nessa diretiva os elementos **não** são removidos do documento e construídos toda vez que a diretiva for chamada.


## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização de valor direto.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
	tag: 'simple-component', 
  template: `
    <h1 cp-show="$ctrl.showText">A simple text</h1>
    <button cp-click="$ctrl.change()">Click me</button>`
})

class simpleComponent extends Controller implements OnInit {
    $onInit(){
        this.showText = false;
    }
    change() {
        this.showText = !this.showText;
    }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/425/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/89/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/374/)
* [Angular](https://jsfiddle.net/t0b8xxfj/155/)

Exemplo de utilização de operações lógicas.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
	tag: 'simple-component', 
  template: `
	<h1 cp-show="$ctrl.firstValue <= $ctrl.secondValue">A simple text</h1>
  `
})

class simpleComponent extends Controller implements OnInit{
    $onInit(){
        this.firstValue = 10;
        this.secondValue = 20;
    }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/415/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/91/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/376/)
* [Angular](https://jsfiddle.net/t0b8xxfj/156/)