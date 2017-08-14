````# mongoDB_tutor
MongoDB tutorials

##NoSQL 
* NoSQL är "non relational"
* Principen är Key-Value-Modell
* Document motsvaras av Post (record)
* Collection motsvaras av Tabell 
* 
* Documents are similar to JSON objects
* Kräver ingen uppsättning med type och relationer
* The _id Field acts as a primary key and is automatically generated
* MongoDB är NoSQL

##MongoDB
* MongoDB är gratis
* MongoDB köras på Mac, Win, Linux
* 
  
##Start Mongo with path to data
`Mongodb --dbpath "\program files\mongodb\data\db"` 

##Connect to remote MongoDB
`mongo mongodb://be9.asuscomm.com:27017/temp`

##Välj databas
use <db> //skapar ny db eller switchar till befintlig

  ##Connection string
mongodb://[username:password@]host1[:port1][,host2[:port2],...[,hostN[:portN]]][/[database][?options]]

##Create Collection
db.users.insert(
  {
    name: "Sue",
    age: 26,
    status: "A"
  }
)

##Read Collection
db.users.find(              //collection
  { age: { $gt: 18 }},      //search criteria
  { name: 1, address: 1 }}  //projection
).limit(5) 

##Update Collection
db.users.update(              //collection
  { age: { $gt: 18 }},        //update criteria
  { $set: { status: "A" }},   //update actio
  { multi: true }             //update option
)

##Remove Collection with Criteria
db.users.remove(
  { status: "D"}  //Remove criteria
)

##Drop DB
db.users.drop()

##Insert date
Date('Dec 12, 2014 14:12:00')

##Get Last record
db.users.find().skip(db.users.count()-1).forEach(printjson)

##Skapa användarkonto på Mongo
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
