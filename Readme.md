<h2 style="color: pink">This read Me for setting up replica set for mongo krub</h2>

<p style=""> 1. Install kubernete <p>
<p style=""> 2. Install Metallb system <p>
<p style=""> 3 Run file .yaml <p>
 
``` 
$ kubectl create -f .
``` 
<p>4.connect mongo pod together </p>

> Set primary node

```
$ kubectl exec -it mongo-0.mongo:27017
> rs.initiate()
> var ctx = rs.conf()
> ctx.members[0].host="mongo-0.mongo:27017"
```
<p>re-save config</p>

```
> rs.reconfig(ctx)
```
> connect rest node to primary node :3

```
> rs.add("mongo-1.mongo:27017")
> rs.add("mongi-2.mongo:27017")
```

> check it with creeate new mongo shell pod

```
$ mongo mongodb://mongo-0.mongo,mongo-1.mongo,mongo-2.mongo

```
> and check with

```
> rs.status()
```

Sirawich Voungchuy :3
