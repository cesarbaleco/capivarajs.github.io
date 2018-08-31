## Criação de Componentes

A criação de componentes utilizando CapivaraJS é feita de maneira simples, mais a frente serão apresentados maiores detalhes sobre os objetos de configuração que o Framework disponibiliza. O exemplo abaixo mostra como devemos criar um componente com conteúdo `HTML`.

```js
const {Component, Controller, OnInit} = capivara.core;

@Component({
	tag: 'my-component',
    template: `<p>Olá Mundo</p>` 
})

class myClass extends Controller implements OnInit {
	$onInit(){
    }
}
```
!> Note que o CapivaraJS não impõe as regras do W3C para nomes de etiquetas personalizadas (tudo-minúsculo, pode conter um hífen), embora seguir esta convenção é considerada boa prática.

Depois da criação do componente basta apenas chama-lo dentro do seu código `HTML`. 

```HTML
<my-component></my-component>
```

Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/310/)

## Objeto de Configuração

Quando declaramos um componente, é possível adicionar várias configurações, o objeto de configuração é responsável pela criação do componente declarado, é através dele que definimos questões de variáveis, templates que serão apresentados e várias outras funções.

```js
@Component({
    tag       : STRING,
    template  : STRING,
    constants : ARRAY,
    functions : ARRAY,
    bindings  : ARRAY,
    controller: FUNCTION
})
```
Vale lembrar que o objeto de configuração `tag` é a Tag HTML que o componente irá substituir.

## Template

Essa propriedade é responsável por conter todo código `HTML` presente no seu componente, é ela que será substituída no lugar da chamada do componente, não existe tamanho definido em questão de elementos `HTML` que ela suporta, apenas ressaltar que para facilitar a escrita do código, sempre que um componente possui mais de uma linha, utilizar ao invés de `aspas simples` para demarcar o código, deve ser utilizado `Crase`.

```js
@Component({
	tag: 'my-component',
    template: `
    	<h1>Meu Incrível Componente.</h1>
        <p>Essa é uma demostração do template.</p>`
})
```
Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/311/)


## Controller

Através dessa propriedade é possível receber o escopo do seu componente, todas as variáveis, funções serão definidas dentro do `Controller`, ele é o cérebro do seu componente. A sua `class` fará um `extends` do `Controller`, portanto, para adicionar as funcionalidades ao seu componente, ele deve ser chamado da seguinte forma.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
	tag: 'my-component',
    template: `<p>Hello [[ $ctrl.message ]]!</p>`
})

class myClass extends Controller implements OnInit {
	$onInit(){
        this.message = 'World';
    }
}
``` 
!>Importante destacar que as variáveis quando referenciarem o `controller` devem possuir o prefixo **$ctrl**.

Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/312/)

# Interpolação

A interpolação é usada pelo CapivaraJS para fornecer vinculação de dados para os elementos `HTML`, é através dela que conseguimos representar conteúdos de forma dinâmica, dentro do `HTML`.

Para compreendermos a interpolação, vamos criar um componente **counter** que a cada 1 segundo vai aumentar o valor e o capivarajs terá que automaticamente atualizar os elementos **HTML**.

```js
const { Component, Controller } = capivara.core;

@Component({
    tag: 'my-component',
    template: ` <h1> [[ $ctrl.counter ]] </h1> `
})
class MyComponent extends Controller {
	
  private counter: number = 1;
  
  $onInit() {
  	const self = this;
    setInterval(() => {
      self.counter++;
    }, 1000);
  }  
}
```
!> Sempre que quisermos utilizar a interpolação para representação de valores, ela deve aparecer entre **colchetes duplos**.

Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/1kbLruyq/172/)

# Constants
As constantes são parâmetros que você informa para um componente, o valor do parâmetro é lido apenas uma vez, então toda alteração do valor não será refletida no componente, ou seja, todos os parâmetros passados como `constants` para o componente **não mantêm a referência**.

Para demonstrar melhor o funcionamento do parâmetro, criaremos uma constante que terá o nome de **myName**, e gostaríamos que esse valor não fosse alterado.

```js
const {Component, Controller, OnInit} = capivara.core

@Component({
    tag: 'my-component',
    template: `<h1> Olá [[$ctrl.$constants.myName]]</h1>`,
    constants: ['myName']
})

class myClass extends Controller implements OnInit {
    $onInit(){
  	    console.log(this.$constants.myName)
    }
}
```

Logo em seguida precisamos informar o valor da constante no `HTML`, note que os parâmetros que possuem caracter maiúsculo devem ser informados por hífen e sendo tudo minúsculo.

``` HTML
<my-component my-name="'Mateus'"></my-component>
```
Pronto, sua constante foi passada para o componente, toda constante está disponível na propriedade **$constants** do seu **$ctrl**.

Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/zf8gqh0d/313/)

# Funções

As funções também podem ser passada para o componente, são bastante utilizadas quando o componente quer executar funções de `callback`. Podemos exemplificar a utilizações com um simples exemplo.

```js
const {Component} = capivara.core

@Component({
	tag: 'my-component',
    template: `
  	<button cp-click="$ctrl.$functions.onButtonClick()"> Clique aqui! </button>
  `,
  functions: ['onButtonClick']
})

class NotMyController {
    createAlertTest() {
        alert('Clicou');
    }
}
```

Na declaração do componente bastariamos passar a função por parâmetro, observe que nesse caso a classe `MyController` não faz um `extends`, pois ela não é o controlador do componente, e sim a classe que possui a função `createAlertTest` que é passada como parâmetro.
``` HTML
<my-component on-button-click="$ctrl.createAlertTest"></my-component>
```

Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/x3myhc85/17/)

# Bindings
Bindings são parâmetros informados à um componente, são utilizados quando quiser que o componente **mantenha a referência** do parâmetro, ou seja, toda alteração de valor feita pelo componente será refletido no contexto do parâmetro, assim como toda alteração feita no valor do parâmetro será refletida no componente.

Para entendermos como funciona os bindings do componente, vamos criar um exemplo onde iremos simular um objeto chamado `person` e nosso componente irá alterar o parâmetro `name`.

```js
const { Component, Controller } = capivara.core;

@Component({
    tag: 'my-component',
    bindings: ['name'],
    template: ` <input type="text" cp-model="$ctrl.$bindings.name"/> `
})

class MyComponent extends Controller {
}

class MyController {
  constructor() {
    this.person = {
      name: "Mateus Miranda"
    }
  }
}
capivara.controller(document.body, MyController);
``` 
Quando chamar o componente no código `HTML`, apenas será necessário informar a referência do atributo.

```HTML
<h1>Valor: [[ $ctrl.person.name ]]</h1>
<my-component name="$ctrl.person.name"></my-component>
```

Se quiser dar uma olhada, esse exemplo está no [JSFiddle](https://jsfiddle.net/jcanabarro/1kbLruyq/175/)
