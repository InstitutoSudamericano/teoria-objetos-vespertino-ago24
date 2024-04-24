# Contenido de un proyecto de NestJS
## Teoría
### Carpetas y Archivos
Para familiarizarnos un poco con NestJS, vamos a ver el contenido que viene disponible en un proyecto.
Después de la creación del Proyecto de NestJS vamos a abrirlo en VSCode desde la terminal con `code .`.
Luego de esto podremos observar un montón de archivos y carpetas como en cualquier otro framework y vamos a describir qué contiene cada uno de ellos.

*Carpeta Dist*: Corresponde a la aplicación de NEST.  Esta carpeta se genera automáticamente cuando construyes tu aplicación y contiene el código JavaScript transpilado que se ejecutará en producción.
*Node_Modules*: Almacen de dependencias del proyecto incluidos los paquetes de NestJS y cualquier otra librería que hayas instalado.
*SRC* : Almacena el código Fuente funcional. Almacena los controladores y modulos.
1. main.ts: Este archivo es el punto de entrada de tu aplicación NestJS. Aquí se crea la instancia de la aplicación y se inicia.
2. app.module.ts: En este archivo defines el módulo principal de tu aplicación, donde importas otros módulos y controladores.
3. app.controller.ts: Este es un controlador de ejemplo. Los controladores son responsables de manejar las solicitudes HTTP y retornar respuestas.
4. app.service.ts: Este es un servicio de ejemplo. Los servicios contienen la lógica de negocio de tu aplicación y pueden ser inyectados en controladores u otros servicios.
5. /modules/: Esta carpeta puede contener módulos adicionales de tu aplicación, cada uno con su propio controlador, servicio, etc., si es necesario.

*Test*: Test point to point.Archivos de Prueba de nuestra aplicación.
*Eslintrc*: 
*Gitignore*: Archivos a ignorar para trabajar adecuadamente con el proyecto.
*Prettier*: Configuración para prettier
*Nest CLI*: Este archivo contiene la configuración específica para el CLI de NestJS, si has configurado alguna.
*Package-lock/PackageJSON*: Dependencias de desarrollo y almacen de script necesarios para interactuar con el proyecto.

**Cada archivo y carpeta en la estructura de tu proyecto NestJS tiene un propósito específico:**

1. Controladores (*.controller.ts): Contienen los métodos que manejan las solicitudes HTTP entrantes y devuelven respuestas al cliente.
2. Servicios (*.service.ts): Encapsulan la lógica de negocio y se utilizan para realizar operaciones como recuperar datos de la base de datos, interactuar con otros servicios, etc.
3. Módulos (*.module.ts): Agrupan controladores, servicios y otros módulos relacionados, proporcionando un contexto para la inyección de dependencias y la organización de tu aplicación.
4. Pruebas: En la carpeta de pruebas, puedes escribir pruebas unitarias y de integración para tu aplicación, asegurando que funcione como se espera en diferentes escenarios.
---


## Reflexión.

La estructura de un proyecto NestJS es como el esqueleto de una aplicación: proporciona el marco sobre el cual se construye todo el código. Cada archivo y carpeta es como un hueso que sostiene una parte específica de la aplicación. 
Sin una estructura clara y organizada, la aplicación sería como un cuerpo sin su esqueleto, sin forma ni soporte. 
La organización cuidadosa de los archivos en diferentes carpetas refleja una estrategia de diseño que facilita la navegación y comprensión del código. Cada componente tiene su lugar designado y está destinado a cumplir una función específica dentro del ecosistema de la aplicación. Esta estructura ordenada no solo mejora la legibilidad del código, sino que también facilita la colaboración entre desarrolladores, ya que todos pueden encontrar rápidamente dónde están los diferentes elementos de la aplicación.


## Analogía
La estructura de un proyecto NestJS se asemeja a la construcción de un edificio moderno y funcional.

Cada archivo y carpeta dentro del proyecto es como un componente clave en la construcción del edificio. El archivo `main.ts` actúa como la entrada principal al edificio, donde los visitantes ingresan y son dirigidos a diferentes áreas según sus necesidades.

Los controladores son como los pisos del edificio, cada uno dedicado a una función específica. Por ejemplo, un controlador puede manejar las solicitudes de usuarios, mientras que otro puede encargarse de la gestión de archivos estáticos.

Los servicios son como los sistemas internos del edificio, como la electricidad, la fontanería y el sistema de calefacción. Proporcionan funcionalidades esenciales para la aplicación, como acceso a bases de datos, autenticación de usuarios y lógica de negocios.

Los módulos son como las secciones del edificio que agrupan funciones relacionadas. Por ejemplo, puede haber un módulo para la autenticación de usuarios y otro para la gestión de productos.

## Resumen
En resumen, el proyecto NestJS sigue una estructura organizada que facilita el desarrollo y mantenimiento de la aplicación. En la carpeta src, encontramos archivos como main.ts, app.module.ts, app.controller.ts, y app.service.ts, que representan el punto de entrada, el módulo principal, los controladores y los servicios respectivamente. La carpeta test contiene archivos de prueba para la aplicación. La carpeta /dist se genera automáticamente al construir la aplicación y almacena el código JavaScript transpilado para producción. La carpeta node_modules alberga todas las dependencias del proyecto. tsconfig.json contiene la configuración del compilador TypeScript, mientras que package.json contiene información sobre el proyecto y sus dependencias. En resumen, esta estructura proporciona un marco claro y ordenado para el desarrollo y la implementación de aplicaciones NestJS.

## Referenciado.
- *Documentación NestJS* <https://docs.nestjs.com/first-steps>
- *Nest.js de 0 - 100: Estructura de un proyecto Nest.js* : <https://www.youtube.com/watch?v=iRPBC6tLrl8&ab_channel=MarluanEspiritusanto>
- *Nest.js - Patrón arquitectónico, controladores, proveedores y módulos*:<https://codigoencasa.com/nest-js-patron-arquitectonico-controladores-proveedores-y-modulos/#:~:text=Estructura%20del%20directorio%20del%20proyecto%20NestJS.%201%20app.controller.ts%3A,que%20realizar%C3%A1n%20una%20determinada%20operaci%C3%B3n.%20...%20M%C3%A1s%20elementos>
- *Qué es Nest.js? Un Vistazo al Framework Ligero de JavaScript*: <https://kinsta.com/es/base-de-conocimiento/nestjs/>
- Video en Youtube: <https://youtu.be/vLlFIQHoT18>



