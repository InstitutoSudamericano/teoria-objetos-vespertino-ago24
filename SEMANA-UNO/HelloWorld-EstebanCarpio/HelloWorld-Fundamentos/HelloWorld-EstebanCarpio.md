# Hello World y algunos fundamentos de <font color="red"><font color="red">NestJS</font></font> 
## Teoría
### Fundamentos y Concepto
**<font color="red">NestJS</font>**, es uno de los Frameworks Backend de Nodejs que más cerca está de ser productivo, Este framework te permite crear aplicaciones backend como REST APIs, GraphQL APIs, WebSockets y Microservicios, con facilidad, al ya proporcionarte integracion con modulos como express, fastify, multer, jsonwebtokens, class-validator, apollo graphql, swagger para documentación y muchos otros modulos Adicionales.

El framework esta basado principalmente en <font color="skyblue">Typescript</font>, y modulos relacionados como *ORMs* tipo *TypeORM*, *Prisma ORM* o *MicroORM*, ademas de usar mucho la orientacion a Objetos, inyecccion de dependencias y un diseño modular para estructura los archivos, inspirado en el framework de Frontend **Angular**.

<font color="red">NestJS</font> es un framework para el desarrollo de aplicaciones del lado del servidor. Ofrece un marco de trabajo y una serie de herramientas preconfiguradas, en el que podemos basarnos para desarrollar proyectos backend con mayor agilidad y homogeneidad.

Dentro de las herramientas ya configuradas en proyectos Nest encontramos <font color="skyblue">Typescript</font> así como todo un sistema para compilado del código en modo desarrollo que nos ahorrará mucho tiempo.
----

### Hello World

#### **Basta de conceptos** es hora de explicar cómo crear un proyecto con <font color="red">NestJS</font> y nuestro primer *"Hola Mundo"*.

En la documentación de <font color="red">NestJS</font> encontramos un tutorial que lo explica muy bien.

1. Primero que nada se debe instalar el framework de <font color="red">NestJS</font> de forma **global** con el comando:
`npm i -g @<font color="red">NestJS</font>/cli` 

2. Luego lo que tenemos que hacer es crear un nuevo proyecto con el comando:
**`nest new project-NOMBRE_DEL_PROYECTO`**

3. Con esto el directorio de tu nuevo proyecto será creado junto con otras carpetas de Package.json, dependencias de producción, de desarrollo y una carpeta llamada **/src** que contiene archivos con terminación en *.ts* 
4. Para poder iniciar nuestro proyecto podemos utilizar el comando que se encuentra en Package.json:
`npm run start:dev` que inicializará un proyecto con su respectivo puerto local **Localhost:3000**

5. Se ejecutará un mensaje de *Hello World* por defecto, y ese mensaje se imprime desde <font color="yellow">app.service.ts</font>  que contiene una función llamada 
`getHello(): string{return 'Hello World!'};`

6. Y así por defecto imprimiríamos un Hello World en nuestro Primer Proyecto en <font color="red"><font color="red">NestJS</font></font> !

## Reflexión

Es **fascinante** ver cómo <font color="red"><font color="red">NestJS</font></font> simplifica el proceso de desarrollo backend en Node.js al proporcionar un conjunto de herramientas preconfiguradas y una estructura modular que fomenta la agilidad y la homogeneidad en los proyectos. Su enfoque en <font color="skyblue">Typescript</font>, junto con la integración de diversos módulos y librerías populares, permite a los desarrolladores construir aplicaciones robustas y escalables de manera más eficiente.

Al seguir el tutorial para crear un simple "Hola Mundo" en <font color="red">NestJS</font>, se puede apreciar la rapidez con la que se puede comenzar a desarrollar con este framework. La instalación global del CLI de <font color="red">NestJS</font> y la generación de un nuevo proyecto con un solo comando demuestran la simplicidad y la facilidad de inicio que ofrece este entorno de desarrollo.

## Analogía
El hecho de que <font color="red">NestJS</font> esté basado en <font color="skyblue">Typescript</font> y utilice módulos relacionados como TypeORM o Prisma ORM se asemeja a tener arquitectos y diseñadores expertos que planifican meticulosamente cada detalle del proyecto, desde los cimientos hasta el techo, utilizando los últimos avances en tecnología de construcción.

La estructura modular y la orientación a objetos de <font color="red">NestJS</font> se compararían con la organización del equipo de construcción en diferentes equipos especializados: uno se encarga de la estructura básica, otro del diseño de interiores, otro del sistema eléctrico y así sucesivamente. Esta división del trabajo facilita la colaboración y la eficiencia, ya que cada equipo puede concentrarse en su área de especialización sin interferencias.

## Resumen
En resumen, <font color="red">NestJS</font> es un framework backend para <font color="green">Node.js</font> que simplifica el desarrollo de aplicaciones al ofrecer una serie de herramientas preconfiguradas y una estructura modular. Basado en TypeScript y orientado a objetos, permite crear fácilmente REST APIs, GraphQL APIs, WebSockets y Microservicios. Su enfoque en la inyección de dependencias y el diseño modular, inspirado en Angular, promueve buenas prácticas de programación y facilita la colaboración en equipos de desarrollo. Con solo unos pocos comandos, como la instalación global del CLI y la generación de un nuevo proyecto, los desarrolladores pueden comenzar rápidamente a construir aplicaciones backend con NestJS.


## Referenciado.
- *Documentación NestJS* <https://docs.nestjs.com/first-steps>
- *¿Qué es Nestjs?, Un Framework pensado para Producción a gran escala* : <https://www.youtube.com/watch?v=CCfdb0C9bCA&ab_channel=Fazt>
- *06. Nest.js Series: Hello World*:<https://www.youtube.com/watch?v=NjIlyR_s_0o&ab_channel=MarluanEspiritusanto>