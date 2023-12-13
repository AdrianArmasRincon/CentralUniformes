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
![Entity Relationship diagram](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/bf1a6bb0-d2a8-4bf4-8250-733a59225e74)


las entidades de esta base de datos son; Apps; Roles; User y News.

News tiene los siguientes atributos:
  id                Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  title             varchar(255) Not Null,<br/>
  content           varchar(500) Not Null,<br/>
  image             file  Not Null,<br/>
  
Apps tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  icon             varchar(255) Not Null,<br/>
  URL              varchar(255) Not Null,<br/>

Roles tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  name             varchar(255) Not Null<br/>

User tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  name             varchar(255) Not Null,<br/>
  email            varchar(255) Not Null,<br/>
  password         varchar(255) Not Null<br/>

La tabla intermedia rol_app debido a la relación muchos a muchos entre Roles y Apps, tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  Rol_id           Integer(10)  Not Null Foreign_Key references Rol(id)<br/>
  app_id           Integer(10)  Not Null Foreign_Key references Apps(id)<br/>

La tabla intermedia rol_user debido a la relación muchos a muchos entre Roles y Users, tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  Rol_id           Integer(10)  Not Null Foreign_Key references Rol(id)<br/>
  app_id           Integer(10)  Not Null Foreign_Key references User(id)<br/>


Las tablas estás relacionadas entre sí de la siguiente manera:
Roles y Apps están relacionadas muchos a muchos, y Roles y User, están relacionadas muchos a muchos entre sí también, mientras que news es una tabla no relacionada.


# Diagrama-de-clases
![cdCU](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/cde8858c-9ae7-4852-bfcc-8d7a3363503e)


Entidades son User; App; Rol y New.

New tiene los siguientes atributos:
  -new_id            Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  -title             varchar(255) Not Null,<br/>
  -content           varchar(500) Not Null,<br/>
  -image             file  Not Null,<br/>

New tiene los siguientes métodos:
  +addNew();
  +getNew();
  +updateNew();
  +deleteNew();
  
App tiene los siguientes atributos:
  -id               Integer(10)  Unique Auto_increment  Primary_Key,<br/>
  -icon             varchar(255) Not Null,<br/>
  -url              varchar(255) Not Null,<br/>
  
App tiene los siguientes métodos:
  +addApp();
  +getApp();
  +updatepp();
  +deleteApp();
  
Rol tiene los siguientes atributos:
  -id               Integer(10)  Unique Auto_increment  Primary_Key,
  -name             varchar(255) Not Null
  
Rol tiene los siguientes métodos:
  addRol();
  getRol();
  updateRol();
  deleteRol();
  
User tiene los siguientes atributos:
  -id               Integer(10)  Unique Auto_increment  Primary_Key,
  -name             varchar(255) Not Null,
  -email            varchar(255) Not Null,
  -password         varchar(255) Not Null

User tiene los siguientes métodos:
  +register();
  +logIn();
  +logout();
  +addCustomer();
  +getCustomer();
  +updateCustomer();
  +deleteCustomer();

  
  # ORM
  ![ORM Diagram](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/46edecb1-7471-4524-acbb-cc7dad6352a5)


#SQL
La base de datos se crea automaticamente al hacer un migrate de laravel, pero este es el código equivalente:
Create database:
```sh
  CREATE DATABASE db_centraluniformes;
  USE db_centraluniformes;
```
Create tables:
```sh
  CREATE TABLE apps (
    id int not null primary key auto_increment,
    icon varchar(255) not null,
    url varchar(255) not null
);

CREATE TABLE roles (
    id int not null primary key auto_increment,
    name varchar(255) not null
);

CREATE TABLE users (
    id int not null primary key auto_increment,
    name varchar(255) not null,
    email varchar(255) not null,
    password varchar(255) not null
);

CREATE TABLE role_apps (
    id int not null primary key auto_increment,
    apps_id int not null,
    role_id int not null,
    foreign key (apps_id) references apps(id),
    foreign key (role_id) references roles(id)
);

CREATE TABLE user_roles (
    id int not null primary key auto_increment,
    user_id int not null,
    role_id int not null,
    foreign key (user_id) references users(id),
    foreign key (role_id) references roles(id)
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
## Manual de usuario

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


