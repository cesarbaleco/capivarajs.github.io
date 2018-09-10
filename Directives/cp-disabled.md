## Utilização

```js
@Component({
  tag: 'simple-component'
  template: `<button cp-disabled=""></button>`
});
```

## Descrição

Quando ativada, a diretiva `cp-disabled` indica que o elemento está desativado, ou seja, o elemento não irá responder qualquer tipo de ação, seja por clique ou por entradas de teclado, e todos os comandos do seu escopo não serão executados até que o atributo seja desativado. Quando o elemento encontra-se desativado, sua cor torna-se ligeiramente mais cinza para que seja sinalizado.<br>
A ativação pode ser feita utilizando valores diretos do tipo `booleanos` ou também pode ser utilizada comparações aritméticas e lógicas.


## Exemplos

A chamada HTML de todos os componentes é feita da seguinte forma:

```HTML
<simple-component></simple-component>
```

Exemplo de utilização em um elemento `<button>` com valor direto.

```js
const {Component, Controller, OnInit} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `<button cp-disabled="$ctrl.isDisabled">Click me</button>`
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.isDisabled = true;
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/364/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/55/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/340/)

Exemplo de utilização em um elemento `<button>` com operação lógica.

```js
const {Component, Controller, OnInit} = capivara.core

@Component( {
  tag: 'simple-component',
  template: `
  	<input type="text" cp-model="$ctrl.person.name">
    <button cp-disabled="$ctrl.person.name.length < 5">
        Click me
    </button>
  `
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
     this.person = { name: '' }
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/438/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/53/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/342/)