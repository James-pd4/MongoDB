# 1. Operadores de consulta de comparação

### $eq

Especifica a condição de igualdade. O operador $eq corresponde a documentos em que o valor de um campo é igual ao valor especificado.

### Sintaxe

```bash
{ <field>: { $eq: <value> } }
```
Exemplo:

````bash
Alura_Series> 
db.Series.find({"Ano de lançamento":{$eq: 2014}})
````

### $gt (greater than)
seleciona os documentos em que o valor do campo especificado é maior que (ou seja >) o valor especificado

### Sintaxe

```bash
{ field: { $gt: value } }
```

Exemplo:

````bash
Alura_Series> 
db.Series.find({"IMDb Avaliação":{$gt: 8}})
````

````bash
db.Series.countDocuments({"IMDb Avaliação": {$gt: 8}})
````

Esse comando retornará o número total de documentos que atendem ao critério da consulta, ou seja, onde o campo "IMDb Avaliação" é maior que 8.