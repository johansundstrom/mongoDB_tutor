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
* Mongodb lyssnar på TCP-port 27017

## Visa databaser
```show dbs``` - Visar befintliga databaser

## Välj databas
```use {db}``` - skapar ny db och/eller switchar till befintlig

## Visa Collections
```show collections```

## Create Collection
```db.kunder.insert({ name: "Anders", alder: 40, status: "A" })```

## Read Collection
```db.kunder.find()         //Visar alla Documents```

```javascript
db.users.find(              //collection
  { age: { $gt: 18 }},      //search criteria
  { name: 1, address: 1 }}  //projection
).limit(5)
```

## Update Collection
```javascript
db.users.update(            //collection
  { age: { $gt: 18 }},      //update criteria  { $set: { status: "A" }},   //update actio
  { multi: true }           //update option
)
```

## Remove Collection with Criteria
```db.users.remove(
  { status: "D"}            //Remove criteria
)```

## Drop DB
```db.users.drop()```

## Insert date
```Date('Dec 12, 2014 14:12:00')```

## Get Last record
```db.users.find().skip(db.users.count()-1).forEach(printjson)```

## Skapa användarkonto på Mongo
```use admin
db.createUser(
   {
     user: "user",
     pwd: "password",
     roles: [
       { role: "readWrite", db: "<db>" }
    ]
  }
)```

## Connection string
```mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]```

# Anslut till fjärr MongoDB
```mongo mongodb://be9.asuscomm.com:27017/temp```