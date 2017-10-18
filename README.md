# MongoDB tutorials

## NoSQL 
* NoSQL är "non relational"
* NoSQL används vid mer ostrukturerat data
* Principen är Key-Value-Modell liknande JSON-modellen
* I NoSQL kallas tabell för _Collection_
* _Document_ motsvaras av Post (record)
* _Document_ är ett JSON objekt
* Kräver ingen uppsättning med typdefinitioner eller relationer
* MongoDB är NoSQL

## MongoDB
* MongoDB är gratis
* MongoDB körs på Mac/Win/Linux
* Fältet ```_id``` är primär nyckel och genereras automatiskt varje _collection_

## Installera MongoDB
* Följ anvisningarna på https://www.mongodb.com/download

### Starta MongoDB med sökväg till data
* Skapa mapp för data på ```data/db```
* Se till att denna har skriv/läsrättigheter
* ```Mongodb --dbpath "\program files\mongodb\data\db"``` (Windows)
* ```mongod --dbpath <path to data directory>```(Mac)
* Mongodb lyssnar på TCP-port 27017

## Skapa användarkonto på Mongo
```javascript
use admin
db.createUser(
   {
     user: "user",
     pwd: "password",
     roles: [
       { role: "readWrite", db: "<db>" }
    ]
  }
)
```

## Databaser i Mongo

### Visa databaser
```show dbs``` - Visar befintliga databaser

### Välj välj/skapa databas
```use example_db``` - skapar ny db och/eller switchar till befintlig

### Radera databas
```db.example_db.drop()```


## Collections

### Skapa databasen OLF
```use OLF```

### Visa Collections
```javascript
show collections          //visar alla Collections
```

### Skapa Collection
```javascript
db.kunder.insert({ company: "Anders", adress: "Storgatan", rabattKod: 2 })
```

### Visa Collections
```javascript
show collections          //visar alla Collections
```

### Sökdefinition
* Det går att söka definitioner enligt - db.collection.find(query, projection)

### Visa Collection
```javascript
db.kunder.find()          //Visar alla Documents i Collection
```

### Visa Collection
```javascript
db.kunder.find().pretty()  //Visar alla Documents i Collection
```

| Name	| Description                                  |
|-------|----------------------------------------------|
| $eq	  | lika med ett specifikt värde                 |
| $gt	  | större än ett specifikt värde                |
| $gte	| större än eller lika med ett specifikt värde |
| $lt	  | mindre än ett specifikt värde                |
| $lte	| mindre än eller lika med ett specifikt värde |
| $ne	  | inte lika med ett specifikt värde            |
| $in	  | värdet finns i en array                      |
| $nin	| värdet finns inte i en array                 |


### Visa Collection med sökkriterie
```javascript
db.kunder.find(               //sök i Collection
  { rabattKod: { $gt: 1 }}    //Sökkriteria "greater than"
)
```

### Visa Collection med sökkriterie och returerade fält
```javascript
db.kunder.find(                //sök i Collection
  { rabattKod: { $gt: 1 }},    //Sökkriteria "greater than"
  { _id: 0, rabattKod: 0 }}    //projection (returnerade fält)
)
```

### Visa Collection med sökkriterie och returerade fält och begränsat sökresultat
```javascript
db.kunder.find(               //sök i Collection
  { rabattKod: { $gt: 1 }},   //Sökkriteria "greater than"
  { _id: 0, status: 0 }}      //projection (returnerade fält)
).limit(5)
```

## Uppdatera Collection
```javascript
db.kunder.update(              //collection
  { rabattKod: { $gt: 1 }},   //update criteria  { $set: { status: "A" }},   //update actio
  { multi: true }           //update option
)
```

## Radera Collection med kriteria
```javascript
db.kunder.remove(
  { rabattKod: 2}            //Remove criteria
)
```


## Insert date
```javascript
Date('Dec 12, 2014 14:12:00')
```

## Get Last record
```javascript
db.kunder.find().skip(db.kunder.count()-1).forEach(printjson)
```



## Connection string
```javascript
mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]
```

# Anslut till fjärr MongoDB
```javascript
mongo mongodb://be9.asuscomm.com:27017/temp
```
