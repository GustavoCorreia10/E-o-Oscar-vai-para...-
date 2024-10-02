# Nomeados ao Oscar

Contém a base de indicados ao Oscar em formato JSON para treinar comandos de consulta no MongoDB. 

* Quantas vezes Natalie Portman foi indicada ao Oscar?

R: 3 vezes

Q:
```js
 db.registros.countDocuments({"nome_do_indicado": "Natalie Portman"})
```

* Quantos Oscars Natalie Portman ganhou?

R: 1 vez

Q:
```js
 db.registros.countDocuments({nome_do_indicado: "Natalie Portman", vencedor: "true"})
```

* Amy Adams já ganhou algum Oscar?

R: Nunca ganhou.

Q:
```js
 db.registros.countDocuments({nome_do_indicado: "Amy Adams", vencedor: "true"})
```

* A série de filmes Toy Story ganhou um Oscar em quais anos?

R: Ganhou 2 Oscar nos anos: 2011 e 2020

Q:
```js
 db.registros.find({ nome_do_filme: { $in: ["Toy Story", "Toy Story 2", "Toy Story 3", "Toy Story 4"] } });
```

* A partir de que ano que a categoria "Actress" deixa de existir? 

R: 1976

Q:
```js
  db.registros.find({categoria:"ACTRESS",vencedor:"true"}).sort({ano_cerimonia:-1}).limit(1)
```

* Quem ganhou o primeiro Oscar para Melhor Atriz? Em que ano?

R: Janet Gaynor, ganhou em 1928

Q:
```js
 db.registros.find({categoria:"ACTRESS",vencedor:"true"}).limit(1)
```

* Na campo "Vencedor", altere todos os valores com "true" para 1 e todos os valores "false" para 0.

Q:
```js
 db.registros.updateMany({ vencedor: "true" }, { $set: { vencedor: 1 } })
```

```js
 db.registros.updateMany({ vencedor: "false" }, { $set: { vencedor: 0 } } )
```

* Em qual edição do Oscar "Crash" concorreu ao Oscar?

R: 2006

```js
 db.registros.find({ nome_do_filme: "Crash" }, { ano_cerimonia: -1, vencedor: 1 } )
```

* Bom... dê um Oscar para um filme que merece muito, mas não ganhou.

R: Um filme que que merecia ter vencido o Oscar de Melhor Filme foi "O Resgate do Soldado Ryan"

```js
db.registros.insertOne({ ano_filmagem: 1997, ano_cerimonia: 1998, cerimonia: 51, categoria: "filme de guerra", nome_do_indicado: "Tom Hanks", nome_do_filme: "O Resgate do Soldado Ryan", vencedor: 1 })
```

* O filme Central do Brasil aparece no Oscar?

R: Não aparece no Oscar

```js
 db.registros.countDocuments({ nome_do_filme: /Central do Brasil/i })
```

* Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser. 

R: "A Fantástica Fábrica de Chocolate", "Os Goonies" e "Clube da Luta"

```js
 db.registros.insertMany([
  {
    nome_do_filme: "A Fantástica Fábrica de Chocolate",
    ano_cerimonia: null,
    categoria: "Filme Musical",
    vencedor: "0"
  },
  {
    nome_do_filme: "Os Goonies",
    ano_cerimonia: null,      
    categoria: "Aventura",
    vencedor: "0"
  },
  {
    nome_do_filme: "Clube da Luta",
    ano_cerimonia: null,
    categoria: "Drama",
    vencedor: "0"
  }
])

```

* Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?

R: Melhor Filme: "Crash", Melhor Atriz: Reese Witherspoon por "Johnny & June" (Walk the Line), Melhor Diretor: Ang Lee por "O Segredo de Brokeback Mountain" (Brokeback Mountain)

```js
 db.registros.insertMany([
  {
    nome_do_filme: "Crash",
    ano_cerimonia: 2005,
    categoria: "CINEMATOGRAPHY",
    vencedor: "1"
  },
  {
    nome_do_filme: "Johnny & June",
    ano_cerimonia: 2005,
    categoria: "ACTRESS",
    vencedor: "1"
  },
  {
    nome_do_filme: "O Segredo de Brokeback Mountain",
    ano_cerimonia: 2005,
    categoria: "DIRECTING",
    vencedor: "1"
  }
])

```


