# Exemplos Básicos

## Criação dos Componentes

Vamos aprender alguns exemplos básicos de como criar e configurar seus primeiros componentes
para que isso te ajude lá na frente, para simplificar algumas coisas, vamos criar pequenos componentes da forma mais simples mesmo, sem a utilização do CLI.

```js
const {Component, Controller, OnInit} = capivara.core;

@Component({
  tag: 'simple-component',
  template: '<p>Olá Mundo</p>'
})

class FirstExample extends Controller implements OnInit {

  $onInit() {
      console.log('Olá Mundo')
  }
}
```

Vamos observar alguns pontos importantes dentro desse código em `JavaScript`:

* `tag`: Dentro dela deverá ter o nome da Tag HTML que o seu componente possui, no nosso caso `simple-component`.
* `template`: Aqui dentro estará todo código HTML que seu componente possui.

Questões mais aprofundadas sobre cada elemento dentro do `@Component` podem ser encontrados
[aqui](GettingStarted/Components)

O código HTML abaixo demonstra como deverá ser feita a chamada do componente dentro do HTML.

```html
<body>
  <simple-component></simple-component>
</body>
```

Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](http://jsfiddle.net/zde5kbjt/42/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/2/)
* [React]()
* [Angular]()

!> É importante ressaltar que não precisamos fazer qualquer chamada ou construção do componente,
apenas lembre de adicionar um `script` que chama o arquivo que possui o código `JavaScript` escrito
acima.

## Utilizando Variáveis

Claro que o código da seção anterior não faz absolutamente nada de legal, mas podemos com certeza
melhorar ele, vamos criar variáveis para serem exibidas na página web ao invés de apenas utilizar textos estáticos.


```js
const {Component, Controller, OnInit} = capivara.core;

@Component({
  tag: 'simple-component',
  template: `<h2> [[ $ctrl.message ]] </h2>`
})

class SecondExample extends Controller implements OnInit {
	
  $onInit() {
  	this.message = 'Olá Mundo'
  }
}
```

Alguns pontos que podemos ressaltar nesse código:

* `Variáveis`: Toda vez que formos utilizar variáveis para serem impressas no código HTML, elas 
devem estar na seguinte formatação `[[variável]]`.
* `$ctrl`: Assim como podemos utilizar o parâmetro `this` para referenciar variáveis de uma classe, 
dentro dos componentes do CapivaraJS, as variáveis devem **sempre** conter o prefixo `$ctrl.variavel`.

Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](http://jsfiddle.net/zde5kbjt/43/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/6/)
* [React]()
* [Angular]()


!> Vale lembrar que o código HTML fica exatamente o mesmo do exemplo anterior.

## Utilizando Condicionais

Neste exemplo iremos utilizar condicionais para mostrar texto dentro do HTML de forma dinâmica, alguns pontos serão destacados, mas um aprofundamento sobre todas as diretivas que o CapivaraJS tem suporte pode ser visualizado [aqui](GettingStarted/Components)

```js
const {Component, Controller, OnInit} = capivara.core;

@Component({
  tag: 'simple-component',
  template: `
    <p cp-if="$ctrl.isVisible">[[$ctrl.text]]</p>
    <p cp-else>[[$ctrl.otherText]]</p>
    <button cp-click="$ctrl.Visibility()">Click!</button>
    `
})

class ThirdExample extends Controller implements OnInit{
  
  $onInit(){
    this.text = 'Você está me vendo';
    this.otherText = "Você não está me vendo"
    this.isVisible = true;
   }

   Visibility = function(){
     this.isVisible = !this.isVisible;
   }
}
```
O que podemos observar com este exemplo:

* `cp-if` e `cp-else`: São condicionais como em qualquer linguagem de programação que exite, através dessas diretivas podemos criar formas dinâmicas de apresentar código HTML.
* `cp-click`: Sempre utilizado quando se quer disparar eventos utilizando mouse.
* `$ctrl.Visibility()`: **Tome cuidado** quando for utilizar funções em diretivas, se elas não possuírem `()` o CapivaraJS entenderá como uma variável.

Disponibilizamos o exemplo em diferentes ambientes.
* [CapivaraJS](http://jsfiddle.net/zde5kbjt/41/)
* [VueJS](http://jsfiddle.net/jcanabarro/ygznj9mt/7/)
* [React]()
* [Angular]()

!> Vale lembrar que o código HTML fica exatamente o mesmo do exemplo anterior.

Esperamos que isso tenta te dado uma pequena ideia de como o **CapivaraJS** funciona, e se você chegou até aqui, espero que tenha gostado. Nós ficamos muito felizes com isso 😃.