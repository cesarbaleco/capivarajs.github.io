## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<input cp-model=""/>`,
});
```
## Descrição

A diretiva `cp-model` possibilita a interação do seu escopo com um elemento `<input>`, ou seja, todo valor digitado no elemento `<input>` será refletido na variável que o `cp-model` faz referência.

## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização do `cp-model`.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
  tag: 'simple-component', 
  template: `
    <p>Choose a name</p>
    <input type="text" cp-model="$ctrl.person.name">
    <p> Your name: [[$ctrl.person.name]] </p>`
})

class simpleComponent extends Controller implements OnInit {
    $onInit(){
        this.person = { name: '' }
    }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/402/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/82/)
* [React]()