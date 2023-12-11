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
           <li><a href="#¿De-dónde-surje-la-necesidad?">¿De dónde surje la necesidad?</a></li>
           <li><a href="#¿Para-qué-empresa-se-desarrolla?">¿Para qué empresa se desarrolla?</a></li>
           <li><a href="#¿En-qué-consiste-el-proyecto?">¿En qué consiste el proyecto?</a></li>
           <li><a href="#Otro">Otro</a></li>
        </ul>
         <li><a href="#Diagramas-y-justificación-del-modelo-de-datos">Diagramas y justificación del modelo de datos</a></li>
        <ul>
           <li><a href="#Resumen">Resumen</a></li>
           <li><a href="#Diagramas">Diagramas</a></li>
          <ul>
            <li><a href="#Entidad-relación">Entidad relación</a></li>
            <li><a href="#Diagrama-de-clases">Diagrama de clases</a></li>
          </ul>
        </ul>
        <li>
          <a href="#Requisitos-de-usuario">Requisitos de usuario</a>
        </li>
        <li>
          <a href="#Casos-de-uso">Casos de uso</a>
        </li>
        <li>
          <a href="#Funcionamiento">Funcionamiento</a>
        </li>
         <li>
          <a href="#Interfaces">Interfaces</a>
        </li>
        <ul> 
           <li><a href="#Diseño-Inicial">Diseño inicial</a></li>
           <li><a href="#Usabilidad-y-accesibilidad">Usabilidad y accesibilidad</a></li>
        </ul>
         <li><a href="#Manuales">Manuales</a></li>
        <li><a href="#Test-de-prueba ">Test de prueba</a></li>
        <li><a href="#Pila-tecnológica">Pila tecnológica</a></li>
        <li><a href="#Repositorios">Repositorios</a></li>
        <li><a href="#Planificación">Planificación</a></li>
        <li><a href="#Conclusiones">Conclusiones</a></li> 
        <li><a href="#Enlaces-y-referencias">Enlaces y referencias</a></li>  
      </ul>
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


### Casos-de-uso
Este es el diagrama que define los casos de uso del sistema:
![UseCaseDiagramCentralUniformes](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/c47f03be-34e2-40d6-8020-dc1b42270bdb)

### Funcionamiento

### Interfaces
## Diseño-Inicial
El diseño de la interfaz la he realizado en Figma, una herramienta de diseño de aplicaciones, haz click [Aquí](https://www.figma.com/file/a9WsPZAvFzBYSJ3IYo0i4r/Central-uniformes?type=design&node-id=0%3A1&mode=design&t=4GP51U1oCj83aGM6-1) para ver la interfaz en funcionamiento y su diseño.

## Usabilidad-y-accesibilidad
Hacer parte de Pino con la ayuda en su módulo

### Manuales


### Test-de-prueba 
El test de prueba lo hice en el frontend, el código es el siguiente:

Y las capturas de prueba son las siguientes:


### Pila-tecnológica
Para descargar y utilizar el proyecto y la pila tecnológica, lo primero es clonar el repositorio y entrar al proyecto:
  ```bash
    git clone https://github.com/AdrianArmasRincon/CentralUniformes.git
    cd CentralUniformes
  ```
<p>
  Para el frontend he utilizado Reactjs  
  <a href="https://ionicframework.com" target="_blank" rel="noreferrer"> 
    <img src="https://www.vectorlogo.zone/logos/reactjs/reactjs-icon.svg" alt="Reactjs" width="50" height="50"/> 
  </a>
</p>

Y para configurar e instalar React, lo primero que hay que hacer es descargar [Node.js](https://nodejs.org/en).
A continuación, deberas ir al frontend e instalar las dependencias.
```bash
  cd frontend
  npm install
```

Para iniciar el frontend, hay que meterse a él y poner este comando (se abrirá en http://localhost:3000):
```bash
  npm start
```

<p>
  Para el backend he utilizado Laravel
   <a href="https://ionicframework.com" target="_blank" rel="noreferrer"> 
    <img src="https://www.vectorlogo.zone/logos/laravel/laravel-icon.svg" alt="Reactjs" width="50" height="50"/> 
  </a>
</p>

Y para configurar e instalar Laravel, hay que descargar [Composer](https://getcomposer.org/download/).
A continuación, deberás ir al backend e instalar composer.
```bash
  cd backend
  composer install
  cp .env.example .env
  php artisan key:generate
```
Edita el archivo .env con la configuración de tu base de datos.

Para iniciar el backend, deberás meterte a él e introducir este comando:
```bash
  php artisan serve
```
<p>
  Como ORM he utilizado Eloquent de Laravel
 <a href="https://ionicframework.com" target="_blank" rel="noreferrer"> 
    <img src="https://www.vectorlogo.zone/logos/laravel/laravel-icon.svg" alt="Reactjs" width="50" height="50"/> 
  </a>
</p>

<p>
  Como base de datos he utilizado MySQL
   <a href="https://ionicframework.com" target="_blank" rel="noreferrer"> 
    <img src="https://www.vectorlogo.zone/logos/mysql/mysql-icon.svg" alt="Reactjs" width="50" height="50"/> 
  </a>
</p>
### Repositorios

### Planificación

### Conclusiones

### Enlaces-y-referencias


