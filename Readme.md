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

#### $all 
O operador $all no MongoDB é usado para verificar se um array contém todos os elementos especificados. Ele é particularmente útil quando você quer buscar documentos onde um campo do tipo array contém todos os valores de uma lista específica, independentemente da ordem.

Exrmplo:

```bash
{
    _id: ObjectId('67b6f289de4c1fe6bff73f18'),
    'Série': 'The Man in the High Castle',
    'Ano de lançamento': 2015,
    'Temporadas disponíveis': 4,
    Linguagem: 'Inglês',
    Genero: [ 'Drama', 'Suspense' ],
    'IMDb Avaliação': 8,
    'Classificação': '18+'
}
```
Se você quiser buscar todas as séries cujo campo Genero contenha tanto 'Drama' quanto 'Suspense', você pode usar o operador $all no mongosh assim:

```bash
db.series.find({
    Genero: { $all: ['Drama', 'Suspense'] }
})
```


# 3. Atualizar documentos em uma coleção

####  updateOne

O método updateOne permite que você especifique um filtro para encontrar o documento que deseja atualizar e, em seguida, aplicar as modificações desejadas. Aqui está um exemplo básico de como usar updateOne:

```bash
db.collection.updateOne(
    { _id: ObjectId('67b6f289de4c1fe6bff73f18') }, // Filtro para encontrar o documento
    { $set: { 'Série': 'The Man in the High Castle - Updated' } } // Atualização a ser aplicada
)
```

posso usar o updateOne para inserir um campo que não existe, por exemplo

```bash
 {
    _id: ObjectId('67b6f289de4c1fe6bff73f5e'),
    'Série': 'Grimm',
    'Ano de lançamento': 2012,
    'Temporadas disponíveis': 7,
    Linguagem: 'Inglês',
    Genero: [ 'Drama', 'Ação', 'Aventura' ]
  }
  ```

  vamos iserir o campo classicação nesse documento.

  ```bash
  db.Series.updateOne({'Série': 'Grimm'}, {$set: {'Classicação': '16+'}})
  ```