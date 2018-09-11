O CapivaraJS possui funções que trabalham com o ciclo de vida de uma página `HTML`, essas funções podem detectar o estado atual de cada componente e ações que devem ser tomadas quando determinados eventos acontecem.

## $onInit

Esse é o estado que será executado apenas quando o controlador do componente for criado, não é possível executar essa ação mais de uma vez com o mesmo componente.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
	tag: 'my-component',
    template: `<p> Olá Mundo </p>`
})

class myClass extends Controller implements OnInit{

	$onInit(){
  	    console.log('Controller Started!')
    }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](http://jsfiddle.net/jcanabarro/zde5kbjt/45/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/100/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/380/)
* [Angular](https://jsfiddle.net/t0b8xxfj/90/)

## $onViewInit
Ações definidas no escopo do `onViewInit` serão executados quando o componente for renderizado na tela, na maioria dos casos, existe uma diferença de tempo de execução das funções do `onViewInit`, visto que os componentes levam um certo tempo para serem visíveis.

```js
const {Component, Controller, OnViewInit} = capivara.core

@Component({
	tag: 'my-component',
    template: `<p> Olá Mundo </p>`
})

class myClass extends Controller implements OnViewInit {

	$OnViewInit(){
  	    console.log('Controller Started!')
    }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](http://jsfiddle.net/jcanabarro/zde5kbjt/46/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/101/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/382/)
* [Angular](https://jsfiddle.net/t0b8xxfj/92/)

## $onChanges

A função `$onChanges` será executada quando for identificado alguma mudança de valores no componente que a mesmas instância. Também é possível detectar quais foram as mudanças executadas.

```js
const {Component, Controller, OnChanges, OnInit} = capivara.core

@Component({
	tag: 'my-component',
  template: `
    <h1>[[$ctrl.value]]</h1>
    <input type="text" cp-model="$ctrl.value" />`,

})

class myClass extends Controller implements OnChanges, OnInit {
	
    $OnInit(){
        this.value = ''
    }
    $onChanges(changes){
  	    console.log('Changes Detected: ', changes);
    }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](http://jsfiddle.net/jcanabarro/zde5kbjt/50/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/102/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/384/)
* [Angular](https://jsfiddle.net/t0b8xxfj/93/)


## $onDestroy

A função é encarregada de executar todas as ações de seu escopo assim que o componente for destruído.

```js
const { Component, Controller, OnDestroy } = capivara.core;

@Component({
    tag: 'my-component',
    template: `<h1>[[ $ctrl.message ]]</h1>`
})
class MyComponent extends Controller implements OnDestroy {
    private message: string = 'My Component';

    $onDestroy() {
        alert('My Component Destroyed');
    }
}

class MyController {
    private showComponent: boolean = true;
  
    toogleComponent() {
        this.showComponent = !this.showComponent;
    }
}
capivara.controller(document.body, MyController);
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/mateusmiranda/1kbLruyq/184/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/104/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/387/)
* [Angular](https://jsfiddle.net/t0b8xxfj/95/)

!> É importante ressaltar que essas funções precisam acompanhar o prefixo **$** antes de seus nomes, para que o CapivaraJS possa identificar que são funções especiais.