# CentralUniformes

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
<!--     <li>
      <a href="#Readme-Eng">Readme on English</a>
      <ul>
        <li><a href="#About-the-project">About theproject</a></li>
      </ul>
    </li> -->
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
En estas aplicaciones habrá un menú lateral que contendrá los enlaces de dichas aplicaciones. Este menú será gestionable por un rol de administrador que podrá añadir/borrar/modificar las entradas del menú y dar permiso a los usuarios que tienen acceso a ellas, además el portal deberá mostrar información sobre cada aplicación, siendo esta una imagen, título, descrición y enlace, que será gestionable por el administrador.

### Diagramas-y-justificación-del-modelo-de-datos 
## Resumen 
En esta documentación se va a explicar las tablas generadas y la relación entre ellas y sus atributos dadas las especificaciones pedidas por la empresa.

## Diagramas
# Entidad-relación
![Entity Relationship diagram](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/bf1a6bb0-d2a8-4bf4-8250-733a59225e74)


las entidades de esta base de datos son; Apps; Roles; User y News.
~~~
News tiene los siguientes atributos:
  id                Integer(10)  Unique Auto_increment  Primary_Key,
  title             varchar(255) Not Null,
  content           varchar(500) Not Null,
  image             file  Not Null,
~~~
~~~
Apps tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,
  icon             varchar(255) Not Null,
  URL              varchar(255) Not Null,
~~~
~~~
Roles tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,
  name             varchar(255) Not Null
~~~
~~~
User tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,
  name             varchar(255) Not Null,
  email            varchar(255) Not Null,
  password         varchar(255) Not Null
~~~
~~~
La tabla intermedia rol_app debido a la relación muchos a muchos entre Roles y Apps, tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,
  Rol_id           Integer(10)  Not Null Foreign_Key references Rol(id)
  app_id           Integer(10)  Not Null Foreign_Key references Apps(id)
~~~
~~~
La tabla intermedia rol_user debido a la relación muchos a muchos entre Roles y Users, tiene los siguientes atributos:
  id               Integer(10)  Unique Auto_increment  Primary_Key,
  Rol_id           Integer(10)  Not Null Foreign_Key references Rol(id)
  app_id           Integer(10)  Not Null Foreign_Key references User(id)
~~~

Las tablas estás relacionadas entre sí de la siguiente manera:
Roles y Apps están relacionadas muchos a muchos, y Roles y User, están relacionadas muchos a muchos entre sí también, mientras que news es una tabla no relacionada.


# Diagrama-de-clases
![cdCU](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/cde8858c-9ae7-4852-bfcc-8d7a3363503e)


Entidades son User; App; Rol y New.
~~~
New tiene los siguientes atributos:
  -new_id            Integer(10)  Unique Auto_increment  Primary_Key,
  -title             varchar(255) Not Null,
  -content           varchar(500) Not Null,
  -image             file  Not Null,
~~~
~~~
New tiene los siguientes métodos:
  +addNew();
  +getNew();
  +updateNew();
  +deleteNew();
~~~
~~~
App tiene los siguientes atributos:
  -id               Integer(10)  Unique Auto_increment  Primary_Key,
  -icon             varchar(255) Not Null,
  -url              varchar(255) Not Null,
~~~
~~~
App tiene los siguientes métodos:
  +addApp();
  +getApp();
  +updatepp();
  +deleteApp();
~~~
~~~  
Rol tiene los siguientes atributos:
  -id               Integer(10)  Unique Auto_increment  Primary_Key,
  -name             varchar(255) Not Null
~~~
~~~ 
Rol tiene los siguientes métodos:
  +addRol();
  +getRol();
  +updateRol();
  +deleteRol();
~~~
~~~  
User tiene los siguientes atributos:
  -id               Integer(10)  Unique Auto_increment  Primary_Key,
  -name             varchar(255) Not Null,
  -email            varchar(255) Not Null,
  -password         varchar(255) Not Null
~~~
~~~
User tiene los siguientes métodos:
  +register();
  +logIn();
  +logout();
  +addCustomer();
  +getCustomer();
  +updateCustomer();
  +deleteCustomer();
~~~
  
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
El presente apartado tiene como objetivo definir los requisitos de usuario para el desarrollo de la aplicación de intranet de Central Uniformes, abarca los requisitos funcionales y no funcionales de la intranet, destinada a mejorar la eficiencia y la colaboración interna en Central Uniformes.

Central Uniformes es una empresa líder en la fabricación y distribución de uniformes para diversos sectores, incluyendo servicios médicos, educación y empresas corporativas.
La intranet se desarrollará para mejorar la comunicación interna entre las aplicacones de la empresa, la gestión de enlaces y usuarios y la colaboración entre los diferentes departamentos de Central Uniformes.

Como tipos de usuarios encontramos el usuario administrador que tiene permitido acceder a home, modules, users y role, y gestionar los datos relacionados a estos, así como crear nuevas entradas de datos, y el usuario básico que tiene permitido el acceso a home y la capacidad de acceder a los enlaces básicos. Además de estos el administrador puede crear nuevos roles para los usuarios el cual permite modificar el acceso individual de cada uno a un determinado área, pero no modificar los datos.

Como requisitos funcionales, los usuarios deberán registrarse bajo credenciales seguras, además la aplicación cuenta con menús intuitivos y accesibles para cada tipo de usuario y una barra de búsqueda que facilita la búsqueda de información, en cuanto a la gestión de contenidos, podemos encontrar una subida y descarga segura de datos y archivos cuyo acceso está basado en roles.

Como requisitos no funcionales tenemos la velocidad de carga que no es mayor a 3 segundos, la seguridad de encriptación y contraseñas robustas, la compatibilidad entre navegadores y el diseño responsive entre tablet, movil y pc. Además tiene una buena escalabilidad debido a que al permitir crear modulos, roles y usuarios, crecerá y se adptará con el uso de la empresa. 

### Casos-de-uso
Este es el diagrama que define los casos de uso del sistema:
![UseCaseDiagramCentralUniformes](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/c47f03be-34e2-40d6-8020-dc1b42270bdb)
En este diagrama podemos ver que todos los usuarios pueden ver la vista general y sus módulos asociados anteriormente por el usuario administrador, mientras que el administrador puede gestionar, crear, modificar y eliminar permisos, usuarios y aplicaciones.

### Funcionamiento
La aplicación de intranet de Central Uniformes está diseñada para mejorar la eficiencia operativa y la colaboración interna. El sistema consta de una aplicación web. Aquí se describe el funcionamiento general: 
El inicio de sesión se realizará a traves de la aplicación, y se ha implementado un sistema de inicio de sesión seguro con autenticación de dos factores para garantizar la seguridad, todo esto a través de una interfa de usuario intuitiva y menús de usuario personalizados a cada uno con sus entradas relacionadasa.
El acceso a documentos estará controlado por roles, garantizando la privacidad y seguridad de la información.

En cuanto a las espicificaciones técnicas, se ha desarrollado en un entorno en la nube para facilitar la accesibilidad desde cualquier ubicación, se han utilizado tecnologías modernas y de gran capacidad para asegurar la actualización futura y seguridad de esta. El almacenamiento se realiza en MySQL una de las tecnnologías mas seguras de bases de datos. Además hay protocolos de seguridad básicos para garantizar la seguridad de los usuarios.

La funcionalidad de la app se resume en las posibilidades del uso de las rutas:                                                                        
![image](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/91c6cafa-739b-40ca-b024-1d8637e36609)
Y el [postman](https://documenter.getpostman.com/view/29846283/2s9YkjB3zq)


### Interfaces
## Diseño-Inicial
El diseño de la interfaz la he realizado en Figma, una herramienta de diseño de aplicaciones, haz click [Aquí](https://www.figma.com/file/a9WsPZAvFzBYSJ3IYo0i4r/Central-uniformes?type=design&node-id=0%3A1&mode=design&t=4GP51U1oCj83aGM6-1) para ver la interfaz en funcionamiento y su diseño.

## Usabilidad-y-accesibilidad
# Usabilidad
Tras realizar la implementación de la aplicación, he procedido a estudiar sus aspectos de usbilidad y son los siguientes:

La interfaz resulta atractiva debido a su simplicidad, homogeneidad y la implementación de colores de la empresa, lo que facilita la identidad de su marca, así como la atracción del usuario debido a sus colores suaves y su diseño minimalista.
  ![1](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/c145f1ca-32af-43ef-ae89-a5f30f3ab741)

Además de esto, cuenta con un menu simple basado en iconos para no saturar de información al usuario:                                                                       
  ![2](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/0e8b7cb8-a94d-4650-9643-273d90c1533d)

Los iconos también resultan homogéneos con el diseño de la empresa debido a que predominan las curvas:                                                                                            
  ![3](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/d40feb28-0b2c-4a00-a14f-ac4969b9e6bc)

En cuanto a los botones, tienen un diseño redondeado y con los colores de la empresa, lo que fortalece la identidad de la marca y la familiaridad para el usuario:                                                 
  ![4](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/57f42dc8-dd72-4a77-878e-4a83c9c6d5f8)

El apartado de noticias busca resaltar a la vista del usuario y ser una manera intuitiva y atractiva para el usuario, por lo que he decidido hacer un carousel de imágenes y texto que se redirigen a la noticia a través de un botón:                           
  ![5](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/35f7c6ac-e9cf-4692-a211-3041ce54c42a)

En la versión de móvil y tablet he decidido ocultar las imágenes para mejorar la experiencia de usuario y simplificar la vista y no saturar la pantalla de información debido a su tamaño reducido:          
  ![6](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/6aea4cb9-d5da-440f-bda1-25966bf1ce74)

En la versión de móvil he decidido ocultar el icono superior del login para mejorar la experiencia de usuario y simplificar la vista, ya que este dato también se encuentra en el menú lateral:              
  ![7](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/ac9a2219-055d-4ef2-90ee-1b739b40ec1b)

En la versión estandar para la empresa según se nos ha solicitado, que es la de pc, destacan los iconos de login y logout con la información del estado de manera llamativa por el estado del icono:              
  ![8logout](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/8c172ab3-bdd0-45bf-9c40-3ff612fadc24)
  ![8login](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/081f8f45-aadb-499a-a0b8-0a726e18b420)

También hay un elemento bastante llamativo, que es la barra de filtrado de datos, la cual coincide con el resto del diseo homogéneo:                  
  ![9bb](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/889d61ea-a942-4788-a6e9-880b0be28c3d)

Hay otros elementos de diseño menos notorios, pero que favorecen la experiencia de usuario, tales como el nav dentro del carousel, el cual es homogéneo y ayuda al usuario a ver la infirmación deseada:            
  ![10](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/13fdbaab-5f6a-4334-8ce9-52b243de5f0b)

Otro elemento diseñado para facilitar la experiencia favorable del usuario es que la barra lateral permanece oculta en el login y register para no llenar la pantalla con información no relevante para el usuario en ese proceso, en cambio se ha cambiado por un icono más simple que redirige a home:
  ![11](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/240a3291-983e-4c0c-b936-1c13d9d9dcdc)

En cuanto a la experiencia del administrador, podemos encontrar el diseño de formularios, que es intuitivo y continua con el estilo de diseño:
  ![12](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/b2ad3b57-d39a-4bce-9f2c-d0d740775eaf)

El boton de log out, puede comunicar ideas de forma más rápida y estética al usuario, aumentando la
eficiencia del sistema:
  ![13](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/a39e4f96-00db-48e4-9c4e-50f79b3b77a3)

La fuente de la aplicación favorece el entendimiento de la jerarquía y al equilibrio y la interacción entre los distintos caracteres de la pantalla:                          
  ![14](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/b806ff8c-08e9-4632-b190-e28c2174bd01)




# Accesibilidad 
En cuanto al estudio de la accesibilidad, podemos encontrar lo siguiente:

El texto es adecuado a la resolución de la pantalla y varía dependiendo de esta, podemos verlo en la imagen, como no pone px, si no que tamaño, este varía al cambiar la resolución:                     
![15](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/0535d20a-72ac-4e5a-928c-85cece8d49ba)

El tamaño de los iconos cambia dependiendo de la resolución de la pantalla, ya que modifica el porcentaje del tamaño de la barra lateral que se rellena, además, la barra varía según el ancho de la pantalla:             
![16](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/6c6a600c-8031-4d9e-9680-a19f295c9af2)

Otro aspecto de la accesibilidad es la etiqueta descriptiva de las imágenes, la cuál permite mediante aplicaciones saber que realiza el click de la imagen:                    
![17](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/1fc61353-a631-46b9-98fc-a9865e6b947a)

Un aspecto de accesibilidad podría ser el contraste de colores entre el  el texto y el fondo puede dificultar la lectura para personas con discapacidades visuales o cognitivas:                   
![18](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/b3f17369-fbd1-42ca-bb6a-dd8e5a60c993)

Además de esto, toda la aplicación se puede utilizar únicamente con el teclado, lo que favorece el uso para algunas personas con discapacidades motoras.                        
![19](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/2c6e48d9-b17a-4c54-a2bf-c063a632a4bf)

Los iconos de la aplicación tienen un gran tamaño y separación entre ellos para facilitar su uso a personas con enfermedades como el parkingson y similares:                          
![20](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/be0577bb-aca8-475b-bf0f-da471c0af9bd)

Los botones son grandes y están separados de otras opciones para asegurar su correcto uso a personas con discapacidades motoras:                      
![21](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/b29ce5b5-b78a-4411-8ffa-ab96cc441c0b)

Los inputs tienen un tamaño acorde y un espacio entre ellos para facilitar su uso ante discapacidades motoras:                           
![image](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/e417d833-f112-4afd-99b7-780d22a96e43)

También tengo control de errores que facilitan la introducción de los requisitos de los inputs para el usuario y que tenga un feedback sobre sus errores:                        
![image](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/0bc6bbd8-2848-4588-9159-19bd6ec0d1ac)


### Manuales
## Manual de usuario

### Test-de-prueba 
El test de prueba lo hice en el backend, el código es el siguiente:

Y las capturas de prueba son las siguientes:

![test tdd](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/6395b5b9-70ad-436a-8453-275c3dd418a0)

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
Este proyecto ha sido realizado por [Adrián Armas](https://github.com/AdrianArmasRincon) en el repositorio de git: [https://github.com/AdrianArmasRincon/CentralUniformes](https://
github.com/AdrianArmasRincon/CentralUniformes)

La prueba del backend es la siguiente: [https://documenter.getpostman.com/view/29846283/2s9YkjB3zq](https://documenter.getpostman.com/view/29846283/2s9YkjB3zq)

### Planificación
Para la organización del proyecto he seguido la recomendación de la distribución de trabajo de [Tiburcio Cruz](https://github.com/tcrurav) y es la siguiente:
![image](https://github.com/AdrianArmasRincon/CentralUniformes/assets/146866842/50d57767-9160-4453-ac67-eb6f43c38a93)


### Conclusiones
