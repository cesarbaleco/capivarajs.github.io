## Utilização

```js
@Component({
  tag: 'simple-component',
  template: ` <p cp-class="{className: }"></p>`,
})
```

## Descrição

Com a diretiva `cp-class` é possível modificar dinamicamente as classes dentro do seu componente, podem ser utilizadas operações aritméticas e lógicas para escolher classes, ou operações de negação. Para instanciar a classe basta apenas colocar no formato `{NomeClasse: Condição}`.<br>
A diretiva tem suporte para múltiplas classes, portanto, não é necessário utilizar uma diretiva para uma classe, basta apenas utilizar a vírgula para diferenciar uma classe de outra. Também não existem problemas em adicionar a diretiva `cp-class` em um elemento HTML que já possui uma `class` como atributo.

## Exemplos

A chamada HTML de todos os componentes é feita da seguinte forma:

```HTML
<simple-component></simple-component>
```

Exemplo de utilização com variável `bool`

```js
const { Component, Controller, OnInit } = capivara.core;

@Component({
  tag: 'simple-component',
  template: ` <p cp-class="{ 'myClass' : $ctrl.visible }">A Simple Example</p>`,
})

class MyComponent extends Controller implements OnInit {
  $onInit() {
  	this.visible = true
  }
}
```

Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/429/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/31/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/325/)
* [Angular](https://jsfiddle.net/t0b8xxfj/110/)

Exemplo de utilização com condicionais

```js
const { Component, Controller, OnInit } = capivara.core;

@Component({
  tag: 'simple-component',
  template: `
      <p cp-class="{ 'myClass' : $ctrl.firstValue === $ctrl.secondValue }">
        A Simple Example
      </p>`,
})

class MyComponent extends Controller implements OnInit {
  $onInit() {
    this.firstValue = 10;
    this.secondValue = 90;
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/342/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/98/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/330/)
* [Angular](https://jsfiddle.net/t0b8xxfj/113/)

Exemplo de utilização com condicionais e operações aritméticas

```js
const { Component, Controller, OnInit } = capivara.core;

@Component({
  tag: 'simple-component',
  template: `
    <p cp-class="{ 'myClass' : $ctrl.firstValue + $ctrl.secondValue == 100 }">
      A Simple Example
    </p>`,
})

class MyComponent extends Controller implements OnInit {
  $onInit() {
    this.firstValue = 10;
    this.secondValue = 90;
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/343/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/36/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/331/)
* [Angular](https://jsfiddle.net/t0b8xxfj/114/)r
