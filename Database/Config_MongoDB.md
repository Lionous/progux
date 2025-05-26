## INSTALL

How to install mongoDB 
---
	yay -Sy mongodb-bin
---


## Config Users
Verificar el archibo mongod.conf


sudo nano /etc/mongod.conf

---
    security:
     authorization: "enabled"
---
 
## entrar al Shell de mongodb 
---
	mongosh
---

## Copiar y pergar este script
---
use admin
db.createUser({
  user: "admin",
  pwd: "password",
  roles: [{ role: "userAdminAnyDatabase", db: "admin" }]
})
---


## Ahora entrar como admin
---
mongosh -u "admin" -p "password" --authenticationDatabase "admin"
---
or
---
mongosh -u admin -p --authenticationDatabase "admin"
---

## Añadir nuevo usuario
---
use admin
db.createUser({
  user: "username",
  pwd: "password",
  roles: [
    { role: "readWriteAnyDatabase", db: "admin" },
    { role: "dbAdminAnyDatabase", db: "admin" }
  ],
  mechanisms: ["SCRAM-SHA-1"]
})
---

systemctl restart mongodb

