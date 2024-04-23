Tarea 
Institucion: Instituto Sudamericano

          Materia:  Programaacion Orientada  A Objetos

                    Docente: Prof.Jhonathan Vallejo.

                               Estudiante: Enrique Ochoa

                                                  Fecha: 23/04/2024


Año Lectivo: 2024-2025

# Teoría

## Inyección de Dependencias y Decoradores en NestJS
NestJS se destaca por su potente sistema de inyección de dependencias y el uso de decoradores para facilitar la escritura de código limpio y mantenible. Estos conceptos son fundamentales para entender cómo NestJS gestiona las dependencias entre módulos, servicios y controladores.

Inyección de Dependencias
La inyección de dependencias es un patrón de diseño que permite separar las preocupaciones en una aplicación, facilitando la reutilización y el testing de código. En NestJS, este patrón se implementa de manera transparente a través del sistema de inyección de dependencias.

En lugar de crear manualmente instancias de clases o servicios, NestJS se encarga de inyectar las dependencias necesarias en los controladores, servicios y otros componentes de la aplicación. Esto se logra mediante la anotación de clases o parámetros con decoradores especiales.

Decoradores en NestJS
Los decoradores son una característica poderosa de TypeScript que NestJS utiliza extensamente para definir metadatos y comportamientos adicionales en las clases, métodos, propiedades y parámetros.

Algunos decoradores comunes en NestJS incluyen:

@Module: Define un módulo y especifica qué componentes deben estar incluidos en él.
@Controller: Marca una clase como controlador y define la ruta base para sus métodos.
@Injectable: Indica que una clase es un servicio y puede ser inyectada en otros componentes.
@Get, @Post, @Put, @Delete: Decoradores para definir endpoints HTTP en un controlador.

# Analogia

Inyección de Dependencias
Servicios: Son como libros con funciones específicas.
Controladores y Módulos: Son las estanterías que organizan los servicios (libros).
Decoradores
@Module: Etiqueta que indica el tipo de libros (servicios) en una sección.
@Controller: Señalización que guía hacia diferentes géneros de libros (áreas de interés).
Ejemplo
Un LibroService gestiona información de libros, mientras que LibroController es la estantería que muestra esta información. Los decoradores @Injectable() y @Controller('libros') son las etiquetas que organizan y guían.

# Conclusión

La combinación de inyección de dependencias y decoradores en NestJS proporciona una forma elegante y eficiente de estructurar aplicaciones backend. Facilita la separación de preocupaciones, mejora la reutilización del código y simplifica el testing.

Entender estos conceptos es crucial para aprovechar al máximo las capacidades de NestJS y escribir aplicaciones robustas y mantenibles.

Referencias
# Inyección de Dependencias en TypeScript y NestJS
URL: Medium - Understanding Dependency Injection in TypeScript and NestJS
Descripción: Un artículo detallado que explica los principios de la inyección de dependencias en TypeScript y cómo se implementa en NestJS.
# Decoradores en TypeScript y NestJS
URL: Medium - Understanding Decorators in TypeScript and NestJS
Descripción: Un artículo que proporciona una explicación clara y ejemplos prácticos sobre cómo funcionan los decoradores en TypeScript y NestJS.