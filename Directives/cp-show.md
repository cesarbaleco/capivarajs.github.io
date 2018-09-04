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
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/425/)

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
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/415/)