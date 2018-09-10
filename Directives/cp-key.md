## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `
        <h1 cp-keypress=""></h1>
        <h1 cp-keyup=""></h1>
        <h1 cp-keydown=""></h1>`
})
```
## Descrição

O `cp-key` dispara eventos através de teclas, no entanto, existem três variantes para essa diretiva, sendo elas:

 * `cp-keypress`: O evento será disparado quando a tecla for pressionada e depois solta.  
 * `cp-keyup`: O evento será disparado apenas quando a tecla for solta.
 * `cp-keydown`: O evento será disparado apenas quando a tecla for pressionada.

Para que seja vinculada a tecla que irá disparar o evento, basta concatenar a tecla com a diretiva utilizando ponto, como alguns exemplos abaixo:
 * `cp-keypress.Enter`
 * `cp-keypress.q`
 * `cp-keypress.Space.q`
 * `cp-keypress.Digit2`

Caso você queira encontrar o `key code` de todas as teclas do teclado pode clicar
<a href="http://keycode.info/" target="_blank">aqui</a>.

A diretiva tem suporte a múltiplas teclas, basta apenas continuar a concatenação com o ponto.

## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização da diretiva `cp-keypress` e `key-up`.

```js
const {Component, Controller} = capivara.core

@Component({
	tag: 'simple-component',
  template: `
   <input cp-keypress.enter="$ctrl.onPressEnter($event)" placeholder="Press Enter">
   <input cp-keyup.u="$ctrl.onUp($event)" placeholder="Press and Release U">
`
})

class simpleComponent extends Controller {
  onPressEnter(evt) {
    alert('onPressEnter.');
  }
  onUp(evt){
    alert('onUpEnter.');
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/398/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/79/)
* [React](http://jsfiddle.net/jcanabarro/td4v7qqd/367/)
