# Concepto de Módulos en el framework NestJs

## Teoria

### Definición

Los módulos son una parte fundamental de la estructura de la aplicación. Un módulo es un contenedor para un grupo de componentes relacionados, como controladores, servicios, pipes, y otros módulos. Los módulos ayudan a organizar y modularizar el código, lo que facilita la reutilización, el mantenimiento y la escalabilidad de la aplicación.
Cada aplicación NestJS tiene al menos un módulo raíz, conocido como el módulo principal (app module), que sirve como punto de entrada de la aplicación. Este módulo principal se identifica con el decorador @Module() y especifica qué componentes y funcionalidades están disponibles en la aplicación.

### Organización de Módulos en un Proyecto NestJS

Dentro de un proyecto NestJS, los módulos se organizan de manera jerárquica y pueden tener dependencias entre sí. Algunas consideraciones clave sobre la organización de módulos incluyen:

#### Módulo Principal (App Module):

Es el primer módulo que se carga cuando la aplicación se inicia, este puede importar otros módulos para agregar funcionalidades a la aplicación; ademas define los controladores, servicios, middlewares, y otros elementos globales de la aplicación.

#### Ejemplo de un módulo principal en NestJS

import { Module } from '@nestjs/common';

import { AppController } from './app.controller';

import { AppService } from './app.service';

@Module({

  imports: [], // Importación de otros módulos
  controllers: [AppController], // Controladores del módulo
  providers: [AppService], // Servicios del módulo

})

export class AppModule {}

### Módulos Secundarios
Son módulos que se importan en el módulo principal o en otros módulos secundarios estos agrupan funcionalidades específicas de la aplicación y pueden exportar componentes para que estén disponibles en otros módulos.

#### Ejemplo de un módulo secundario en NestJS
import { Module } from '@nestjs/common';

import { UsersController } from './users.controller';

import { UsersService } from './users.service';

@Module({

  controllers: [UsersController], // Controladores del módulo
  providers: [UsersService], // Servicios del módulo
  exports: [UsersService], // Componentes exportados

})

export class UsersModule {}

### Estructura de carpetas

Para mantener todo ordenado, se coloca cada módulo en su propia carpeta dentro de tu proyecto.Por ejemplo, podrías tener una carpeta llamada users para el módulo de usuarios, otra llamada products para el módulo de productos, y así sucesivamente.
Dentro de cada carpeta de módulo, va los archivos relacionados, como el archivo del módulo mismo (nombre-del-modulo.module.ts), el controlador (nombre-del-modulo.controller.ts) y el servicio (nombre-del-modulo.service.ts).

# Reflexión

La organización de módulos en NestJS es crucial para la eficiencia y la calidad del desarrollo de aplicaciones. Al tener una estructura modular clara y bien definida, se facilita el mantenimiento, la escalabilidad y la comprensión del código. Esta organización promueve la reutilización de componentes, la separación de responsabilidades y la flexibilidad para adaptarse a cambios, lo que resulta en un código más legible, mantenible y adaptable a largo plazo; por esa razon, la organización de los módulos en NestJS no solo es una cuestión de orden superficial, sino una práctica fundamental que impacta en la calidad, la robustez y la evolución continua de las aplicaciones. Es una parte esencial de la arquitectura de software que merece atención y cuidado en cada proyecto de desarrollo.

# Analogia 
## Tema: Contrucción de una casa 

 La organización de módulos en NestJS es como diseñar y construir cada habitación de la casa de manera ordenada y funcional.
 
 Cada habitación tiene un propósito específico y está equipada con elementos necesarios para cumplir ese propósito. Los módulos son como estas habitaciones: el módulo principal es como el corazón de la casa, conectando todas las habitaciones (módulos secundarios) de manera cohesiva. Los muebles y accesorios dentro de cada habitación son como los componentes (controladores, servicios, etc.) dentro de cada módulo, organizados de manera que la casa entera funcione armoniosamente. Una buena organización de módulos en NestJS es como construir una casa bien diseñada y estructurada, donde todo está en su lugar y es fácil de mantener y adaptar a medida que las necesidades cambian.
 # Resumen

 Los módulos son contenedores esenciales que agrupan componentes como controladores, servicios y pipes, organizando así el código de la aplicación en unidades funcionales y facilitando su mantenimiento y escalabilidad. Cada módulo tiene una responsabilidad específica dentro de la aplicación y se comunica con otros módulos mediante la importación y exportación de componentes, siguiendo el principio de "separación de preocupaciones" para una arquitectura más clara y modular.

 # Referencias
 De las Tecnologías de la Información y las Comunicaciones - Universidad de Almería, S. (s. f.). Introducción a NestJS. https://ualmtorres.github.io/SeminarioNestJS/?ref=reactivisima.com#truecreaci%C3%B3n-de-servicios-conectados-a-bases-de-datos

 Admin. (2019, 1 marzo). Cómo crear un módulo en nestjs | Manticore Labs ec -  Desarrollo Web y Móvil en el Ecuador. https://manticore-labs.com/2019/03/01/como-crear-un-modulo-en-nestjs/

Módulos en Nest. (s. f.). DesarrolloWeb.com. https://desarrolloweb.com/articulos/modulos-nest#:~:text=Los%20m%C3%B3dulos%20son%20clases%20que,clases%20altamente%20relacionadas%20entre%20s%C3%AD.


