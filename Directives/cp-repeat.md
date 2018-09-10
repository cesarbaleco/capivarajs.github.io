## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<li cp-repeat=""></li>`
});
```
## Descrição

Podemos usar a diretiva `cp-repeat` para renderizar uma lista de itens. A diretiva `cp-repeat` requer uma sintaxe especial na forma de `item em itens`, em que `itens` é a lista que contém os dados de origem e `item` é um **alias** para o elemento da lista que está sendo iterado.

## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização do `cp-repeat`.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
  tag: 'simple-component', 
  template: `
   <ul>
     <li cp-repeat="person in $ctrl.persons">
      [[person.name]]
     </li>
   </ul>`
})

class simpleComponent extends Controller implements OnInit {
  $onInit() {
    this.persons = [
      {name: 'João'},
      {name: 'Maria'},
      {name: 'Bob'},
      {name: 'Carlos'},
    ];
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/410/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/87/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/372/)