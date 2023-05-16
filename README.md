# Teste para candidatos à vaga de DevOps


> Candidatos para vaga de DevOps na Kenlo devem responder este teste como parte do processo seletivo. A solução do teste deve estar disponível em um repositório online (Github, Bitbucket, etc) e o link deve ser encaminhado por **mensagem ou email**. Pode ser um repositório público ou um repositório privado com acesso para o avaliador. **Será desclassificado quem entregar a solução fazendo fork deste projeto ou criando uma issue no mesmo.**


## Desafio DevOps

Este teste tem como objetivo avaliar as capacidades do candidato em entregar uma aplicação web simples aplicando boas práticas de provisionamento. 

O desafio é dividido em 3 partes:
* Aplicação web
* Provisionamento da aplicação web na AWS (ec2, beanstalk, lambda, etc)
* Deploy (gitlab-ci)


### Aplicação web

A aplicação web consiste de uma API que executa as quatro operações básicas
da matemática: divisão, multiplicação, subtração, adição.

Devem existir 4 endpoints, 1 para cada operação:

Subtração:

`
GET /api/sub?term_one=<term_one>&term_two=<term_two>
`

Multiplicação:

`
GET /api/mul?term_one=<term_one>&term_two=<term_two>
`

Divisão:

`
GET /api/div?term_one=<term_one>&term_two=<term_two>
`

Adição:

`
GET /api/sum?term_one=<term_one>&term_two=<term_two>
`

Cada endpoint deve retornar um JSON contendo o resultado da operação na seguinte estrutura:

```
{'result': <int:result> }
```

Por exemplo:

`
GET /api/sub?term_one=4&term_two=1
`

deve retornar

```
{'result': 3}
```

#### Requisitos não funcionais

* A aplicação deve ser desenvolvida utilizando qualquer linguagem. Linguagens interpretadas e de tipagem dinâmica (como Python/NodeJS) receberão pontos extras por serem mais aderentes à nossa stack.
* Pode-se utilizar qualquer framework para desenvolver a aplicação. Também pode-se optar por não utilizar nenhum framework.
* Soluções que apresentem testes unitários e relatório de cobertura de testes receberão pontos extras. 

### Provisionamento da infraestrutura
 
A solução do teste deve ser capaz de criar de forma automatizada toda infraestrutura necessária para a aplicação web.

Para servir essa aplicação, pode-se utilizar serviços da AWS mais básicos como o EC2 ou mais instrumentados como o Beanstalk ou o Lambda. O desenvolvedor deve definir quais serviços da AWS serão utilizados.


#### Requisitos não funcionais

1. A infraestrutura onde irá rodar a aplicação web deverá ser provisionada em uma das seguintes formas:

    1.1 Ferramentas de automação como ansible, puppet, terraform, etc.

    1.2 Usando ferramentas de script como awscli.

2. A aplicação web deve rodar na porta `8000`.

**A documentação do projeto deve explicar como provisionar o servidor.**


### Deploy


Deverá ser possível fazer deploy da aplicação web na infraestrutura.
O deploy pode usar alguma ferramenta simples como rsync, scp ou outra ferramenta que você preferir.

**A documentação do projeto deverá mostrar como fazer o deploy da aplicação.**

## Critérios de avaliação

A solução do teste será avaliada segundo os requisitos funcionais e não funcionais propostos.

Em uma conta nossa da AWS, iremos:
* Indepotência na criação do servidor.
* Criar os serviços e fazer deploy da aplicação web seguindo a documentação entregue junto com o projeto.
* Validar se a API fornecida fornece os resultados esperados.
* Alterar a API e fazer um novo deploy.
* Remover os serviços provisionados seguindo a documentação entregue junto com o projeto.

Além disso, analisaremos o código do projeto entregue segundo algumas boas práticas de desenvolvimento, como:
* Facilidade para servir a aplicação, fazer deploy, criar e destruir serviços da AWS.
* Facilidade para dar manutenção na aplicação web e nos serviços da AWS
* Legibilidade do código.
* Cobertura relevante de testes unitários.
