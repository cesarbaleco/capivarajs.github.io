## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<h1 cp-style="{CSSAttribute: }"></h1>`
})
```
## Descrição

Podemos utilizar a diretiva `cp-style` para modificar dinamicamente o `style` do seu componente, eles podem ser ativados ou desativados, através de variáveis `booleanas`, condicionais e até utilizando outras diretivas em conjunto, como `cp-click` e `cp-mouse`, ou `<input>` de texto.<br>
A diretiva possui superte a múltiplos atributos, basta apenas utilizar vírgula para separá-los.

## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização com valor direto.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
  tag: 'simple-component',
  template: `
   <p cp-style="{color: $ctrl.color}">Example</p>
  `
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.color = 'blue';
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/418/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/93/)
* [React]()

Exemplo de utilização com comparação.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
  tag: 'simple-component', 
  template: `
   <h1 cp-style="{color: $ctrl.firstValue == 70 ? 'red' : 'green'}"> 
     [[ $ctrl.firstValue + $ctrl.secondValue ]] 
   </h1>`
})

class simpleComponent extends Controller implements OnInit{
  $onInit() {
    this.firstValue = 50;
    this.secondValue = 80;
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/421/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/94/)
* [React]()