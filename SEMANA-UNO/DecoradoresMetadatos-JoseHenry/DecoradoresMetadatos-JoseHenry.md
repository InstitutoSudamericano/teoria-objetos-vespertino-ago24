**Teoría** 
**Decoradores y Metadatos**
Es un marco de trabajo Node.js de código abierto para el desarrollo de sistemas backend desafiantes que utilizan la convención del paradigma de diseño sobre la configuración que elimina la necesidad de una configuración explícita permitiendo a los desarrolladores utilizar herramientas comunes y el código de una manera particular. Puede crear aplicaciones escalables, comprobables y poco acopladas. Está significativamente influenciado por Angular y una característica importante es el poder de la inyección de dependencia, que permite inyectar un módulo en otro, promoviendo la reutilización del código.

**Decoradores:** Un decorador es una expresión que acepta tres argumentos: un objetivo, un nombre y un descriptor de propiedad, y devuelve una función. Se aplica insertando el decorator en la parte superior de lo que se intenta decorar, seguido del carácter @. Hay tres decoradores diferentes como clase ( @Controller() ), método( @Get() ), o argumento ( @Body() ). En NestJs todo puede ser controlado con decoradores. Puedes conectar un controlador a una colección de rutas, especificar un método de petición, añadir contenido al cuerpo de la petición o analizar los parámetros de la misma. 
Los controladores manejan las solicitudes entrantes y devuelven las respuestas al cliente. Puedes especificar una URL como ruta principal para este controlador y un decorador de método como @Get, @Post, @Put o @Delete utilizando el decorador @Controller.

**Metadatos:** Cuando usamos decoradores con Nest, los usamos para crear entradas de metadatos que luego se leerán y usarán. Estos metadatos siempre se leen a través de la ReflectAPI y siempre adoptan la forma de lectura a través de Reflect.getMetadata(metadataKey, classInstance, methodName). Esto methodNamees solo para cuando los métodos están decorados, como métodos de controlador con sus verbos HTTP o solucionadores GraphQL. Podría decirse que los metadatos más importantes que Nest termina utilizando son los design:paramtypesmetadatos. Esta es la clave de metadatos que contiene la información sobre qué dependencia va en qué posición de los constructores. Esto también se usa para ValidationPipeconocer el tipo de cada parámetro del controlador de ruta, si eso es algo que se usa en su aplicación. Cabe señalar que los design:paramtypesmetadatos solo existen cuando la opción --emitDecoratorMetadataflag o emitDecoratorMetadataconfig está configurada con tsc o métodos de compilación similares. Esta es la razón por la que algunas herramientas de compilación, como esbuild, pueden terminar teniendo dificultades para crear aplicaciones Nest sin complementos adicionales.

**Reflexión**
Al utilizar decoradores, NestJS permite definir de manera clara y concisa la arquitectura de una aplicación. Por ejemplo, al definir un controlador con el decorador @Controller(), estamos indicando a NestJS que esa clase representa un controlador y debe ser tratada como tal. Esto simplifica enormemente el proceso de desarrollo, ya que la configuración y la lógica de la aplicación se vuelven más transparentes y fáciles de entender.
La reflexión también se encuentra presente en el uso de metadatos. Estos pueden ser utilizados por NestJS en tiempo de ejecución para realizar acciones específicas, como la inyección de dependencias o la validación de datos. Esto proporciona una mayor flexibilidad y capacidad de adaptación a la aplicación, ya que permite que ciertas decisiones se tomen dinámicamente en función de la información proporcionada por los metadatos.

**Analogía**
En el mundo de Node.js, es una práctica común adjuntar propiedades al objeto de solicitud . Luego, los extrae manualmente en cada controlador de ruta, usando un código como el siguiente: *const user = req.user;*
Cuando el comportamiento de su decorador depende de algunas condiciones, puede usar el dataparámetro para pasar un argumento a la función de fábrica del decorador. Un caso de uso para esto es un decorador personalizado que extrae propiedades del objeto de solicitud por clave. Nest proporciona un método auxiliar para componer varios decoradores. Por ejemplo, supongamos que desea combinar todos los decoradores relacionados con la autenticación en un solo decorador.

Podemos pensar en los decoradores y los metadatos como las etiquetas y la información adicional que se adjunta a un objeto en el mundo real. Por ejemplo, cuando etiquetamos un frasco de mermelada como "fresa", estamos añadiendo metadatos que describen el contenido del frasco. De manera similar, al decorar una clase con @Controller('ruta'), estamos añadiendo metadatos que indican a NestJS cómo debe ser tratada esa clase.

**Resumen**
Los decoradores y los metadatos son características fundamentales de TypeScript y NestJS que permiten definir la estructura y el comportamiento de una aplicación de manera clara y concisa. Los decoradores se utilizan para marcar y anotar elementos del código, mientras que los metadatos proporcionan información adicional que puede ser utilizada por NestJS en tiempo de ejecución para configurar y ejecutar la aplicación de manera adecuada.

**Referencias**
autor: Jay Mcdoniel
fecha: 18/07/2023
url: https://trilon.io/blog/nestjs-metadata-deep-dive 

autor: nestjs
fecha: s/f
url: https://docs.nestjs.com/custom-decorators 

autor: Beste Burcu Bayhan
fecha: 10/11/2022
url: https://apiumhub.com/es/tech-blog-barcelona/por-que-utilizar-el-framework-nestjs/#:~:text=fundamentales%20de%20NestJs-,Decoradores,propiedad%2C%20y%20devuelve%20una%20funci%C3%B3n. 

