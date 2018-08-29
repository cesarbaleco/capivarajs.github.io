# Eventos

É possível escutar e emitir eventos. O CapivaraJS possui as funções **$on** e **$emit** que são responsáveis pelas respectivas ações. O funcionamento e exemplos de utilização serão apresentados nas seções seguintes.

## $emit

A função **$emit** dispara eventos quando fora chamada, através dela enviamos os eventos todos os ouvintes que estão esperando alguma ação.
Primeiro precisamos declarar o `nome do evento` e em seguida como parâmetro opcional passarmos valores.

``` js
let parameter = 'CapivaraJS';
capivara.$emit('SimpleEvent', parameter);
```

## $on

A função **$on** escuta todos os eventos que são disparados, no entanto, vai aceitar apenas aquele evento que tem o mesmo nome que ela espera, isso pode ser bem aproveitado, pois assim podemos fazer com que mais de um receptor receba o mesmo evento, apenas atribuindo o mesmo `nome do evento` aos receptores.

``` js
let parameter = 'CapivaraJS';

capivara.$on('SimpleEvent', ( parameter ) => {
    console.log(parameter);
});
```

Um exemplo contendo os dois eventos está disponível no [JSFiddle]()

!> Observe que o nome dos eventos tanto no **$emit** quanto no **$on** possuem o mesmo nome, é através desse parâmetro que os eventos sabem quem são os emissores e quem são os receptores.

!> Importante ressaltar que as funções de **$on** quando colocadas dentro de uma classe, devem ser envelopadas por outra função, na maioria dos casos podemos colocar as chamadas do **$on** dentro do `constructor` da classe.