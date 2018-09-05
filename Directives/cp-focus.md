## Utilização
```js
@Component({
    tag: 'simple-component',
    template: `<input cp-focus="">`
})
```
## Descrição

O elemento com o atributo `focus` refere-se ao elemento que atualmente recebe eventos de `<input>`. Se houver múltiplos `<input>` de texto, a que tem o foco é aquela na qual o usuário pode inserir texto. Apenas um elemento tem o foco de cada vez.
A diretiva `cp-focus` fará com que seja possível executar funções ou ações quando o elemento `<input>` for selecionado através do clique do usuário.

## Exemplos

```HTML
<simple-component></simple-component>
```

Exemplo de utilização do `cp-focus` para execução de uma função.

```js
const {Component, Controller} = capivara.core

@Component({
  tag: 'simple-component',
  template: `<input type="text" placeholder="Click Here" cp-focus="$ctrl.onFocus()">`
})

class simpleComponent extends Controller {
  onFocus() {
    console.log('Focused');
  }
}
```
Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](https://jsfiddle.net/jcanabarro/zf8gqh0d/385/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/73/)
* [React]()