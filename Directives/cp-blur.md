## Utilização

```js
@Component({
  tag: 'simple-component',
  template: `<input type="text" cp-blur="">`
})
```

## Descrição

A diretiva `cp-blur` é acionada para executar funções ou ações quando um determinado `input` perder o foco.

## Exemplo

A chamada HTML do componente é feita da seguinte forma:

```HTML
<simple-component></simple-component>
```

Exemplo de utilização do atributo `blur`.

```js
const { Component, Controller } = capivara.core;

@Component({
	tag: 'simple-component',
  template: `<input type="text" cp-blur="$ctrl.onBlur()"">`,
})

class MyComponent extends Controller {
	
  onBlur() {
    alert('Blur input.');
  }
}
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/331/)
