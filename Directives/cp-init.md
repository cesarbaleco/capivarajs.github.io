## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<h1 cp-init=""></h1>`
})
```
## Descrição

A diretiva `cp-init` permite a execução de uma função quando o elemento que carrega a diretiva for renderizado.

## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização da diretiva `cp-init`.

```js
const { Component, Controller, OnInit } = capivara.core;

@Component({
	tag: 'my-component',
  template: ` <h1 cp-init="$ctrl.onMessageInit()"> [[ $ctrl.message ]] </h1> `
})

class MyComponent extends Controller implements OnInit {
  public message: string = 'Start message';
  
  $onInit() { }
  onMessageInit() {
  	console.log('teste');
  }
}
```

Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/1kbLruyq/160/)
