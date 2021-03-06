# EXPLICACAO DO DESENVOLVIMENTO

### 1. Criacao dos arquivos Index e Consultas

### 2. Recuperar o valos dos campos da pagina Index

1. Colocar o evento Onclick no botao Index
2. Criar uma funcao Cadastrar Despesas
3. Capiturar os dados dos campos com getelementbyid 
   > uma dica que ao inves de colocar o .value no final do get
   > Podemos colocar ele exemplo console.log(ano.value)

### 3. Criando a classe que representa o Objeto Despesa
 1. Criando a class Despesas
 2. Criar um objeto com base na classe utilizando os parametros atribuidos na viw

### 4. Realizar a integracao com o Local Storage

```JavaScript

/**
 * 
 * No local storage temos o setitem que permite passar dois parametros, o primeiro 
 * parametro e a identificacao do objeto que vamos armazenar, e o segundo e o dado que
 * queremos armazenar. Sendo que esse dado ele precisa ser encaminhado com uma notacao JSON
 * e como estamos trabalhando com objetos literais devemos converter ele para uma notacao JSON
 * para converter podemos usar o objeto nativo do JS chamado JSON 
 */

function gravar(d){
    localStorage.setItem('despesa', JSON.stringify(d)) //como colocamos o setItem sempre que preencher ele ira sobreescrever o item anterior
}


```

## 5. Desenvolvendo Indices Dinamicos

1.  Criar uma classe chamada BD que vai permitir Instanciar um objeto para lidar com o banco de dados (local Storage)

Porque indices dinamicos, pois se nao mudarmos como no codigo acima o indice e despesas sempre que salvarmos vai ter sobreposicao porem quando aleteramos para algo dinamico ajuda que seja salvo esses arquivos


## 6. Implementando da validacao dos dados antes do regristro dessa informacao

usando um dilog do bootstrap

https://getbootstrap.com/docs/4.0/components/modal/

Se inpecionar o bottao ele vai de display none para display bloc onde fiz de maneira programatica acontecer

usando um jQuery que ja e implementado dentro do bootstrap

## 7. Utilizando dom para o Modal


## 8. Listando as despesas na pagina consulta

Com a funcao Carrega Lista Despesas

## 9. Filtrando as despesas

## 10. Inserino as Despesas

## 11. Excluindo Despesas

usando o icone do font awesome

primeira coisa para exclusao devemos ver os valores ou seja os atributos de cada objeto que representam despesas no momento que sao criados como elemento tbody,
ou seja precisamos incluir nas despesas uma maneira de ser linkada Key das despesas para fazer a excluisao.


como o i no for do recuperar todos os registros, que corre incrementando ate achar o o valor semelhante ao id <=  ou seja podemos recuperar o id associando esse atributo o valor de i, utilizado para recuperar o documento em questao.

### Explicacao Sobre Web Storage

Os navegadores modernos em geral, tem recursos de armazenamento de dados em geral dentro do proprio browser que podem ser:

**- Local Storage:** Esse tipo de armazenamento quando realizado os dados armazenados eles nao sao anexados na requizicao HTTP, ou seja ficam no navegados de maneira analoga a um banco de dados. E ele suporta uma quantidade maior de dados que o recurso de Cookie. O LOCAL STORAGE e um armazenamento persistente, nos podemos armazenas as informacoes, fechar a instancia do navegador e reiniciar a maquina e os dados irao ficar armazenados a nao ser que eles sejam intencionalmente removidos.

**- Session Storage:** Esse tipo de armazenamento quando realizado os dados armazenados eles nao sao anexados na requizicao HTTP, ou seja ficam no navegados de maneira analoga a um banco de dados. E ele suporta uma quantidade maior de dados que o recurso de Cookie. O SESSION STORAGE Armazena o dado enquanto a sessao ainda esta ativa, ou seja quando fechamos a instancia do navegador todas as informacoes armazenadas sao perdidas.

- IndexdDB: 

- Web SQL:

**- Cookies:** Funcionam como dados que sao armazenados no lado do cliente portanto no browser. E sempre que existe uma requizicao HTTP, ou seja sempre que acessamos determinada pagina os cookies sao anexados a essa requisicao, de forma que o servidor possa extrair esse cookie, analisar e trabalhar a sua logica com base nas informacoes cadastradas no lado do cliente, e apos esse processamento fazer o retorno da requizicao solicitada pelo cliente.

Antes do HTML5 usamos muito o recurso de Cookies, mas apos a criacao dele os browsers em geral passaram a incorporar outros locais de armazenamento de dados.


### EXPLICANDO SOBRE NOTACAO JSON

Como objetos literais e notacao JSON causam certa confusao por se parecer muito, porem sao usados em conceitos totalmente diferentes. 

Objeto Literal

```JavaScript

let produto = {
    categoria: 'Eletrodomestico',
    descricao: 'Geladeira',
    preco: 1999.00,
}

```

JSON  - (lembrando que json e uma string)

```JS

let produto JSON = '{ "categoria": "Eletrodomestico", "descricao" : "Geladeira", "preco" : "1999.00"}'



```

Lembrando que no JSON precisamos encapsular as Strings internamente tambem.


No caso de comunicacoes com aplicacoes externas ou com servidores, precisamos criar um protocolo de comunicacao, e nesse protocolo precisamos transitar os dados, porem objetos literais eles nao podem ser transitados nesse processo, isso porque eles sao objetos e esses objetos existem apenas na instancia da aplicacao. logo precisamos de alguma forma transofrmar esse objeto numa notacao de texto que e o caso da notacao jeson, para que esse texto seja anexada a essa comunicacao que sera feita, seja com o proprio backend da aplicacao web ou com outras aplicacoes.

apartir da biblioteca JSON nativa do JS convertamos os objetos em notacao json com o ```JSON.stringify()```.  E o inverso  podemos converter o contrario, usando a lib ```JSON.parce()``` que converte o json em JS


### ARRAY FILTER

```JS

let funcionarios = [{nome: 'Fernanda', cargo: 'Analista de RH', salario: 3100, status: 'Ativo'}, {nome: 'Miguel', cargo: 'Analista Administrativo', salario: 1700, status: 'Ativo'}, {nome: 'Rosa', cargo: 'Auxiliar de contabilidade', salario: 1600, status: 'Intativo'}, {nome: 'Roberto', cargo: 'Desenvolvedor PHP', salario: 4400, status: 'Ativo'}, {nome: 'Maria', cargo: 'Engenheira Mecanica', salario: 7500, status: 'Ativo'}]

```

ou seja utilizar o mentodo filter que espera sempre uma funcao de callback, funciona de maneira analoga ao forEach, ele vai percorrer os indices, recuperando o valor de determinado indice.

```JS
funcionarios.filter(function(f) { return true })

// se o retorno for true ele ira retornar o array inteiro
// se o retorno for false siginifica que para aquele determinado indice o retorno nao atendeu ao criterio


```

podemos colocar uma logica se aquele valor x deve ou nao retonar no filet 

```JS
funcionarios.filter(function(f) { return f.salario < 2000 })

```

para saber se aquele determinado objego se ele atende o requisito ou seja true our false

podemos tambem combinar os filtros

```JS
funcionarios.filter(function(f) { return f.salario < 2000 }).filter(function(f){ return f.status == 'ativo'})

```
E podemos melhorar a sintaxe do codigo usando arrow functions como faremos sempre

```JS

funcionario.filter(f => f.salario < 2000)filter(f => f.salario < 2000)

/**
 * 
 * Como esatmos recebendo um unico paramentro omiti os pareteses e como se trata de uma unica expressa
 * podemos utilizar o recurso de retorno implicito.
 * */

```