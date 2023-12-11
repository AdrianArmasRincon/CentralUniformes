# CentralUniformes

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#Readme-Eng">Readme on English</a>
      <ul>
        <li><a href="#About-the-project">About theproject</a></li>
      </ul>
    </li>
    <li>
      <a href="#Readme-Esp">Readme en español</a>
      <ul>
        <li><a href="#Sobre-el-proyecto">Sobre el proyecto</a></li>
        <ul>
          <a href="#¿De-dónde-surje-la-necesidad?">¿De dónde surje la necesidad?</a>
          <a href="#¿Para-qué-empresa-se-desarrolla?">¿Para qué empresa se desarrolla?</a>
          <a href="#¿En-qué-consiste-el-proyecto?">¿En qué consiste el proyecto?</a>
          <a href="#Otro">Otro</a>
          <ul>
            <a href="#Diagrama-de-casos-de-uso">Diagrama de casos de uso</a>
          </ul>
        </ul>
         <li><a href="#Diagramas-y-justificación-del-modelo-de-datos">Diagramas y justificación del modelo de datos</a></li>
        <ul>
           <li><a href="#Resumen"></a></li>
        </ul>
      </ul>
    </li>
    <li>
      <a href="#PostMan">PostMan</a>
    </li>
    <li>
      <a href="#contact">Contact</a>
    </li>
  </ol>
</details>


### Readme-Eng
### About-the-project
This project is made to 

This project is made because of the neccesity of an intranet to redirect to their own apps with an user and access control to the enterprise Central Uniformes


### Readme-Esp
### Sobre-el-proyecto


## ¿De-dónde-surje-la-necesidad?
Este proyecto está hecho para ayudar al acceso y gestión de usuarios, roles y links de una empresa, para facilitar tanto la gestión como el uso de la intranet y sus apps.


## ¿Para-qué-empresa-se-desarrolla?
Se desarrolla para la empresa Central Uniformes, una empresa líder en la venta de uniformes en Canarias.


## ¿En-qué-consiste-el-proyecto?
El proyecto consiste en un portal para su intranet que permita accede a los usuarios de la empresa a diferentes aplicaciones a las que tienen permiso mediante un enlace.

## Otro
# Diagrama-de-casos-de-uso
![UseCaseDiagramCentralUniformes](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/c47f03be-34e2-40d6-8020-dc1b42270bdb)


En estas aplicaciones habrá un menú lateral que contendrá los enlaces de dichas aplicaciones. Este menú será gestionable por un rol de administrador que podrá añadir/borrar/modificar las entradas del menú y dar permiso a los usuarios que tienen acceso a ellas, además el portal deberá mostrar información sobre cada aplicación, siendo esta una imágen, título, descrición y enlace, que será gestionable por el administrador.

### Diagramas-y-justificación-del-modelo-de-datos 
## Resumen 
En esta documentación se va a explicar las tablas generadas y la relación entre ellas y sus atributos dadas las especificaciones pedidas por la empresa.

## Diagramas
# Entidad-relación
![erdCentralUniformes](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/afca52ea-9fac-4629-9edd-a2f045c65546)

las entidades de esta base de datos son; Module; Rol; Admin; New y Customer.

New tiene los siguientes atributos:
  new_id            Integer(10)  Unique Auto_increment  Primary_Key,
  title             varchar(255) Not Null,
  text              varchar(500) Not Null,
  image             file  Not Null,
  
Module tiene los siguientes atributos:
  module_id        Integer(10)  Unique Auto_increment  Primary_Key,
  name             varchar(255) Not Null,
  rol              varchar(255) Not Null,
  Column           Integer(10)  Not Null,

Rol tiene los siguientes atributos:
  rol_id           Integer(10)  Unique Auto_increment  Primary_Key,
  name             varchar(255) Not Null

Customer tiene los siguientes atributos:
  customer_id      Integer(10)  Unique Auto_increment  Primary_Key,
  fullName         varchar(255) Not Null,
  email            varchar(255) Not Null,
  password         varchar(255) Not Null

Admin tiene los siguientes atributos:
  admin_id         Integer(10)  Unique Auto_increment  Primary_Key,
  fullName         varchar(255) Not Null,
  email            varchar(255) Not Null,
  password         varchar(255) Not Null,
  Rol_id           Integer(10)  Not Null Foreign_Key references Rol(rol_id)

La tabla intermedia Cutomer_Rol debido a la relación muchos a muchos entre Customer y Rol, tiene los siguientes atributos:
  customerRolId    Integer(10)  Unique Auto_increment  Primary_Key,
  crrol_id         Integer(10)  Not Null,
  crcustomer_id    Integer(10)  Not Null

La tabla intermedia Module_Rol debido a la relación muchos a muchos entre Module y Rol, tiene los siguientes atributos:
  moduleRolId     Integer(10)  Unique Auto_increment  Primary_Key,
  crrol_id        Integer(10)  Not Null,
  crmodule_id     Integer(10)  Not Null

Las tablas estás relacionadas entre sí de la siguiente manera:
Admin y Rol están relacionadas uno a uno, mientrasque Rol y Module, y Rol Customer, están relacionadas muchos a muchos entre sí.


# Diagrama-de-clases
![classDiaCentralUniformes](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/dc26f17a-74d6-47ca-aed5-884c857ecaa5)

Entidades son Admin; Module; Rol; New y Customer.

New tiene los siguientes atributos:
  -new_id            Integer(10)  Unique Auto_increment  Primary_Key,
  -title             varchar(255) Not Null,
  -text              varchar(500) Not Null,
  -image             file  Not Null,

New tiene los siguientes métodos:
  +getNew();
  
Module tiene los siguientes atributos:
  -module_id        Integer(10)  Unique Auto_increment  Primary_Key,
  -name             varchar(255) Not Null,
  -rol              varchar(255) Not Null,
  -Column           Integer(10)  Not Null,
  
Module tiene los siguientes métodos:
  +getModule();
  
Rol tiene los siguientes atributos:
  -rol_id           Integer(10)  Unique Auto_increment  Primary_Key,
  -name             varchar(255) Not Null
  
Rol tiene los siguientes métodos:
  getRol();
  
Customer tiene los siguientes atributos:
  -customer_id      Integer(10)  Unique Auto_increment  Primary_Key,
  -fullName         varchar(255) Not Null,
  -email            varchar(255) Not Null,
  -password         varchar(255) Not Null

Customer tiene los siguientes métodos:
  +register();
  +logIn();
  +updateCustomer();
  
Admin tiene los siguientes atributos:
  -admin_id         Integer(10)  Unique Auto_increment  Primary_Key,
  -fullName         varchar(255) Not Null,
  -email            varchar(255) Not Null,
  -password         varchar(255) Not Null,
  -Rol_id           Integer(10)  Not Null Foreign_Key references Rol(rol_id)

Admin tiene los siguientes métodos:
  +logIn();
  +getNew();
  +addNew();
  +updateNew();
  +deleteNew();
  +getRol();
  +addRol();
  +updateRol();
  +deleteRol();
  +getCustomer();
  +addCustomer();
  +updateCustomer();
  +deleteCustomer();
  +getModule();
  +addModule();
  +updateModule();
  +deleteModule();
  
La tabla intermedia Cutomer_Rol debido a la relación muchos a muchos entre Customer y Rol, tiene los siguientes atributos:
  -customerRolId    Integer(10)  Unique Auto_increment  Primary_Key,
  -crrol_id         Integer(10)  Not Null,
  -crcustomer_id    Integer(10)  Not Null

La tabla intermedia Cutomer_Rol debido a la relación muchos a muchos entre Customer y Rol, tiene los siguientes atributos:
  -customerRolId    Integer(10)  Unique Auto_increment  Primary_Key,
  -crrol_id         Integer(10)  Not Null,
  -crcustomer_id    Integer(10)  Not Null

La tabla intermedia Module_Rol debido a la relación muchos a muchos entre Module y Rol, tiene los siguientes atributos:
  -moduleRolId     Integer(10)  Unique Auto_increment  Primary_Key,
  -crrol_id        Integer(10)  Not Null,
  -crmodule_id     Integer(10)  Not Null
#SQL

Create database:
```sh
  CREATE DATABASE db_centraluniformes;
  USE db_centraluniformes;
```
Create tables:
```sh
  CREATE TABLE Role (
      roleId INT PRIMARY KEY,
      name VARCHAR(100) NOT NULL
  );

  CREATE TABLE admin (
    adminId INT PRIMARY KEY AUTO_INCREMENT,
    fullname VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(100) NOT NULL,
    Roleid INT NOT NULL,
    FOREIGN KEY (Roleid) REFERENCES Role(roleId) ON DELETE CASCADE ON UPDATE CASCADE
  );

  CREATE TABLE module (
    moduleid INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    role VARCHAR(100) NOT NULL,
    roleid INT NOT NULL,
    FOREIGN KEY (roleid) REFERENCES Role(roleId) ON DELETE CASCADE ON UPDATE CASCADE
  );

  CREATE TABLE customer (
    customerId INT PRIMARY KEY,
    fullName VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(100) NOT NULL,
    username VARCHAR(100) NOT NULL
  );

  CREATE TABLE customer_Role (
    customerid INT NOT NULL,
    roleid INT NOT NULL,
    FOREIGN KEY (customerid) REFERENCES customer(customerId) ON DELETE CASCADE ON UPDATE CASCADE,
    FOREIGN KEY (roleid) REFERENCES Role(roleId) ON DELETE CASCADE ON UPDATE CASCADE
  );
```
### Requisitos-de-usuario







