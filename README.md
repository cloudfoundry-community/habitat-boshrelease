# Habitat Bosh Release
with this bosh release you should be able to run all habitat services
see [habitat.sh](https://habitat.sh)

this release uses bosh2 links

## example
we already provided a example that will deploy a wordpress setup

## properties

#### hab.service `required`
here you define your habitat service package

#### hab.config `optional`
here you can define enviroment variables thath will be placed in a user.toml for you habitat servivce

#### hab.binds `optional`
here you define can define your bind for example a database.
you will need to use a provide and consume link as well

## setup links

if you want to expose a database in our example a mysql database.
you will need to define a provide and consume for your habitat database instance

```
jobs:
- name: habitat
  release: habitat
  provides:
    habitat: {as: hab_mysql}
  consumes:
    habitat: {from: hab_mysql}
```

the service consumer needs
```
jobs:
- name: habitat
  release: habitat
  consumes:
    habitat: {from: hab_mysql}
```    

## Supervisor only
if you want to only use install the supervisor for some reason
please set the service to supervisor

example:
```
properties:
  hab:
    service: supervisor
```    
