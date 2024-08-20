# pybr-tutorial-proposal-db-optmization
A 3-hour tutorial on how to optimize a Django Database, focused on Postgres.

- [pybr-tutorial-proposal-db-optmization](#pybr-tutorial-proposal-db-optmization)


## Título Proposto
Banco tá lento né? Vamo otimizar isso aí!

## Resumo
Utilizando os dados do Censo de 2022 do IBGE, aprenderemos a avaliar performance de um banco de dados transacionais (com Postgres, mas os conceitos servem para os demais), melhorar e prever gargalos.


## Descrição
Este tutorial vai te ensinar como analisar queries lentas, identificar estruturas de tabelas problemáticas, otimizá-las e mitigar problemas futuros. E o melhor de tudo? Usando nossa querida Django ORM (e uns brinquedinhos especiais).

- Como a Django ORM abstrai as interações com o banco de dados
- Otimizações básicas para o dia a dia
- N+1: Por que ainda falamos sobre ele?
- O estranho relacionamento do Postgres e o count()
- Diferença prática entre select_related e prefetch_related
- Indexação de Banco de Dados (BTree vs BRIN vs Hash)
- Plano de Execução de Queries (Ou: Como o Dalibo mudou minha vida)
- Transações e suas peculiaridades
- Estratégias de Cacheamento
- O parente distante: Particionamento de tabelas


## Descreva mais prolixamente o que será abordado na sua atividade, a sua motivação para criá-la e informações que considere relevantes.
Incrivelmente quando falamos de Python/Django sinto que estamos uns anos atrás em boas práticas. É muito fácil encontrar aplicações com estrutura de models feitas as pressas, visando provar o valor do produto o mais rápido possível e mais e mais vemos empresas cujo sistemas crescem tendo que enfrentar os problemas de otimizar um banco de dados feito em um final de semana. Por vezes demais a decisão é "não vamos pensar nisso, vamos levar esses dados para uma aplicação nova" - mas sabemos que esses legados duram mais tempo que as próprias empresas. 

Pretendo dar ferramentas para que qualquer desenvolvedor seja capaz de tomar melhores decisões no dia a dia para que se torne menos comum esse cenário. Veremos aqui os gargalos que temos no dia a dia como models mau estruturados, queries N+1, planos de execução, indices, overindexing, database level caching, django query caching e particionamento de tabelas.


## O que as pessoas que participarem podem esperar aprender na sua atividade?
- Como funciona o query builder do Django e seu comportamento.
- O que evitar ao modelar seus dados (com a ajuda do dbdiagram.io).
- Otimizações básicas: `only`, `defer`, `values`, `values_list` e `annotations`.
- Diferenças entre `prefetch_related` e `select_related`, e quando usá-los.
- Comportamento do Django com `.first()` e a dificuldade do Postgres em contar.
- Indexação e os tipos básicos de índices no Postgres (BTree, BRIN e HASH).
- Explicação sobre planos de execução de queries, como encontrá-los e como interpretá-los (com o auxílio do explain.dalibo.com).
- O papel das transações na otimização de bancos.
- Estratégias de cacheamento (Materialized Views e Django Cache).
- Particionamento de tabelas: casos de uso e como fazer (usando django-postgres-extras).

## Escolha até 3 palavras-chave para representar sua atividade
Django, Banco de Dados, ORM

## Quais conhecimentos prévios são necessários para que seja possível acompanhar bem a sua atividade?
Monto minhas talks com a intenção que possam ser consumidas por pessoas com o menor nível de conhecimento possível, portanto acredito que sejam:

- Conhecimento básico de Django e da Django ORM
- Noções de Banco de Dados Relacionais
- Entender o básico de tipos de dados dos models
- Entender o básico de relacionamento entre Models (OneToMany e ManyToMany)
- Entender o mínimo de transações de banco de dados
- Saber executar um serviço no docker compose.
  
## Tabela de conteúdo
Representando por tempo total (180 minutos)

Todos os tópicos serão apresentados diretamente no código e seus resultados serão vistos na hora.

[0-5] Apresentação
[5-15] Setup
[15-20] Estrutura dos dados do IBGE.
[20-30] Apresentando a aplicação de exemplo.
[30-50] Plano de Execução de Queries
[50-60] Query builder e como ele se comporta em alguns cenários
[60-70] Falhas na arquitetura dos dados e como isso afeta performance
[70-80] Otimizações para o dia a dia.
[80-90] Postgres não sabe contar :(
[90-120] Index - Tipos, algoritmos e overindexing.
[120-130] Comportamentos dentro de uma transação
[130-150] Particionando tabelas
[150-170] Materialized views
[150-180] Caching