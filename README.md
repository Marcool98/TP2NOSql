# Rapport TP MongoDB 

## 1. Vérifier que les données ont été importées
Pour vérifier que les données ont bien été importées, on va compter le nombre de documents dans la collection `films` avec la commande :

```javascript
db.films.countDocuments()
```

## 2. Comprendre la structure du document
Pour examiner un document de la collection `films` pour comprendre sa structure, on va utiliser la fonction `findOne()` qui nous retourne un film aléatoirement :

```javascript
db.films.findOne()
```

## 3. Afficher la liste des films d’action
Pour afficher les films d'action, on exécute la commande suivante :

```javascript
db.films.find({ "genre": "Action" })
```

## 4. Afficher le nombre de films d’action
Pour compter le nombre de films d’action, nous utilisons la commande suivante :

```javascript
db.films.countDocuments({ "genre": "Action" })
```

## 5. Afficher les films d’action produits en France
Pour afficher les films d’action produits en France, on fait la commande :

```javascript
db.films.find({ "genre": "Action", "pays": "France" })
```

## 6. Afficher les films d’action produits en France en 1963
Pour afficher les films d’action produits en France en 1963, on exécute la commande suivante :

```javascript
db.films.find({ "genre": "Action", "pays": "France", "annee": 1963 })
``` 

## 7. Afficher les films d’action réalisés en France sans les grades
Pour afficher les films d'action francais, sans les grades,  on fait la commande :

```javascript
db.films.find({ "genre": "Action", "pays": "France" }, { "grades": 0 })
```


## 8. Afficher les films d’action réalisés en France sans les identifiants
Pour afficher les films d'action francais, sans les identifiants,  on fait la commande :

```javascript
db.films.find({ "genre": "Action", "pays": "France" }, { "_id": 0 })
```

## 9. Afficher que les titres et les grades des films d’action réalisés en France sans les identifiants
Pour afficher seulement les titres et les grades des films d’action réalisés en France sans les identifiants, on utilise :

```javascript
db.films.find({ "genre": "Action", "pays": "France" }, { "_id": 0, "titre": 1, "grades": 1 })
```

## 10. Afficher les films d’action réalisés en France ayant une note supérieure à 10
Pour afficher les films d’action réalisés en France avec une note supérieure à 10, la commande est :

```javascript
db.films.find({ "genre": "Action", "pays": "France", "grades": { $gt: 10 } }, { "_id": 0, "titre": 1, "grades": 1 })
```

## 11. Afficher les films d’action réalisés en France ayant une note supérieure à 40
Pour afficher uniquement les films ayant une note supérieure à 40, la commande à utiliser est :

```javascript
db.films.find({ "genre": "Action", "pays": "France", "grades": { $gt: 40 } }, { "_id": 0, "titre": 1, "grades": 1 })
```

## 12. Afficher les différents genres de la base `lesfilms`
Pour afficher les différents genres présents dans la base de données, la commande est :

```javascript
db.films.distinct("genre")
```

## 13. Afficher les différents grades attribués
Pour afficher les différents grades attribués, la commande est :

```javascript
db.films.distinct("grades")
```

## 14. Afficher tous les films dans lesquels jouent au moins un des artistes suivants ["artist:4", "artist:18", "artist:11"]
Pour afficher tous les films avec les artistes spécifiés, la commande est :

```javascript
db.films.find({ "artistes": { $in: ["artist:4", "artist:18", "artist:11"] } })
```

## 15. Afficher tous les films qui n’ont pas de résumé
Pour afficher tous les films sans résumé, la commande est :

```javascript
db.films.find({ "resume": { $exists: false } })
```

## 16. Afficher tous les films tournés avec Leonardo DiCaprio en 1997
Pour afficher les films tournés avec Leonardo DiCaprio en 1997, la commande est :

```javascript
db.films.find({ "artistes": "Leonardo DiCaprio", "annee": 1997 })
```

## 17. Afficher les films tournés avec Leonardo DiCaprio ou en 1997
Pour afficher les films tournés avec Leonardo DiCaprio ou en 1997, la commande est :

```javascript
db.films.find({ $or: [{ "artistes": "Leonardo DiCaprio" }, { "annee": 1997 }] })
```
