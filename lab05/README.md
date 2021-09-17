# Modelo para Apresentação do Lab05 - Marcadores e Taxonomia em Cypher

# Aluno
* `233686`: `Eduardo Carvalheira Teixeira de Aguiar`

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

### Resolução
~~~cypher
MATCH(c:Categoria {id:"Serviços"})--(m:Marcador)
RETURN m
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH (c:Categoria {id:"Serviços"})
MATCH (d:Categoria)-[:Superior*1..3]->(c)
MATCH (m:Marcador)
WHERE (m)--(d) OR (m)--(c)
RETURN m
~~~
