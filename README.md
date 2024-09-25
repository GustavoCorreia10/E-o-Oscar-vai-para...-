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

R:

Q:
```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* Na campo "Vencedor", altere todos os valores com "true" para 1 e todos os valores "false" para 0.

R:

Q:
```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* Em qual edição do Oscar "Crash" concorreu ao Oscar?

R:

```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* O filme Central do Brasil aparece no Oscar?

R:

```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* Inclua no banco 3 filmes que nunca foram nem nomeados ao Oscar, mas que merecem ser. 

R:

```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* Denzel Washington já ganhou algum Oscar?

R:

```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* Quais os filmes que ganharam o Oscar de Melhor Filme?

R:

```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* Bonus: Quais os filmes que ganharam o Oscar de Melhor Filme e Melhor Diretor na mesma cerimonia?

R:

```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```

* Bonus: Denzel Washington e Jamie Foxx já concorreram ao Oscar no mesmo ano?

R:

```js
 db.oscar.find({"Nome": "Natalie Portman"}).countDocuments()
```
