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

### $gte
$gte seleciona os documentos nos quais o valor do campo especificado é maior ou igual a (ou seja, >=) um valor especificado (por exemplo, value.)

### Sintaxe

```bash
{ field: { $gte: value } }
```

Exemplo:

````bash
Alura_Series> 
Alura_Series> db.Series.find({'Temporadas disponíveis':{$gte: 4}})
````

### $in
O operador $in seleciona os documentos onde o valor de um campo é igual a qualquer valor na array especificada.

### Sintaxe

```bash
{ field: { $in: [<value1>, <value2>, ... <valueN> ] } }
```

Exemplo:

````bash
Alura_Series> db.Series.find({"Genero":{$in:['Ação', 'Cultura']}})
````

***Obs:*** método distinct. Esse método retorna uma lista com todos os valores únicos de um campo específico em uma coleção.

Exemplo:

````bash
Alura_Series> db.Series.distinct("Genero")
[
  'Animação',          'Artes',
  'Aventura',          'Ação',
  'Comédia',           'Cultura',
  'Documentário',      'Drama',
  'Drama, Ação',       'Entretenimento',
  'Esportes',          'Fantasia',
  'Ficção científica', 'Horror',
  'Romance',           'Suspense'
]
````



### $lt (less than)
 seleciona os documentos em que o valor de field é menor que (ou seja, <) o value especificado.

### Sintaxe

```bash
{ field: { $lt: value } }
```

Exemplo:

````bash
Alura_Series> 
db.Series.find({"IMDb Avaliação":{$lt: 8}})
````

````bash
db.Series.countDocuments({"IMDb Avaliação": {$lt: 8}})
````

### $ne
$ne seleciona os documentos onde o valor do campo especificado não é igual ao valor especificado. Isso inclui documentos que não contêm o campo especificado.

### Sintaxe

```bash
{ field: { $ne: value } }
```

Exemplo:

````bash
Alura_Series> 
db.Series.find({"IMDb Avaliação":{$ne: 8}})
````

### $nin (not in)
$nin seleciona os documentos onde:

- o valor de campo especificado não está na array especificada ou

- o campo especificado não existe.

### Sintaxe

```bash
{ field: { $nin: [ <value1>, <value2> ... <valueN> ] } }
```

Exemplo:

````bash
db.Series.find({
    Genero: { $nin: ['Drama'] }
})
````

# 2. Operadores de consulta de array

- $all
- $elemMatch
- $size
