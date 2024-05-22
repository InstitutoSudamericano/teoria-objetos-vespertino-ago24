# PROVIDERS 
----------------------------------------------------------------------------------------------------------------------------------------
# TEORÍA
---------------------------------------------------------------------------------------------------------------------------------------
### Proveedores
Los proveedores son un concepto fundamental en Nest. Muchas de las clases básicas de Nest pueden tratarse como proveedores: servicios, repositorios, fábricas, ayudantes, etc. La idea principal de un proveedor es que se puede inyectar como una dependencia; esto significa que los objetos pueden crear varias relaciones entre sí, y la función de "cablear" estos objetos se puede delegar en gran medida al sistema de ejecución de Nest.

### Servicios
Comencemos creando un archivo simple `CatsService`. Este servicio se encargará del almacenamiento y recuperación de datos, y está diseñado para ser utilizado por el usuario `CatsController`, por lo que es un buen candidato para ser definido como proveedor.

Ejemplo:

```tsx
import { Injectable } from '@nestjs/common';
import { Cat } from './interfaces/cat.interface';@Injectable()
export class CatsService {
  private readonly cats: Cat[] = [];create(cat: Cat) {
    this.cats.push(cat);
  }findAll(): Cat[] {
    return this.cats;
  }
}
```

**Dato: Para crear un servicio usando la CLI, simplemente ejecute el `$ nest g service cats`comando.**

La nuestra `CatsService`es una clase básica con una propiedad y dos métodos. La única característica nueva es que utiliza el `@Injectable()`decorador. El `@Injectable()`decorador adjunta metadatos, que declaran que `CatsService`es una clase que puede ser administrada por el contenedor Nest, este ejemplo también utiliza una `Cat`interfaz, que probablemente se vea así:

```tsx
export interface Cat {
  name: string;
  age: number;
  breed: string;

```

**Ahora que tenemos una clase de servicio para recuperar gatos, usémosla dentro de `CatsController`:** 

```tsx
import { Controller, Get, Post, Body } from '@nestjs/common';
import { CreateCatDto } from './dto/create-cat.dto';
import { CatsService } from './cats.service';
import { Cat } from './interfaces/cat.interface';@Controller('cats')
export class CatsController {
  constructor(private catsService: CatsService) {}@Post()
  async create(@Body() createCatDto: CreateCatDto) {
    this.catsService.create(createCatDto);
  }@Get()
  async findAll(): Promise<Cat[]> {
    return this.catsService.findAll();
  }
}
```

Se `CatsService`inyecta a través del constructor **de** clases. Observe el uso de la `private`sintaxis. Esta abreviatura nos permite declarar e inicializar el `catsService`miembro inmediatamente en la misma ubicación.

### Inyección de dependencia

Nest se basa en un sólido patrón de diseño comúnmente conocido como **inyección de dependencia** . Recomendamos leer un excelente artículo sobre este concepto en la documentación oficial de Angular

Esta dependencia se resuelve y se pasa al constructor de su controlador (o se asigna a la propiedad indicada): 
`constructor(private catsService: CatsService) {}`

### Proveedores Personalizados

Nest tiene un contenedor de inversión de control ("IoC") incorporado que resuelve las relaciones entre proveedores. Esta característica subyace a la característica de inyección de dependencia descrita anteriormente, pero de hecho es mucho más poderosa que lo que hemos descrito hasta ahora.

### Proveedores Opcionales

En ocasiones, es posible que tenga dependencias que no necesariamente deben resolverse. Por ejemplo, su clase puede depender de un **objeto de configuración** , pero si no se pasa ninguno, se deben usar los valores predeterminados. En tal caso, la dependencia se vuelve opcional, porque la falta del proveedor de configuración no provocaría errores.

Para indicar que un proveedor es opcional, utilice el `@Optional()`decorador en la firma del constructor.

```tsx
import { Injectable, Optional, Inject } from '@nestjs/common';@Injectable()
export class HttpService<T> {
  constructor(@Optional() @Inject('HTTP_OPTIONS') private httpClient: T) {}
}
```

Ten en cuenta que en el ejemplo anterior utilizamos un proveedor personalizado, razón por la cual incluimos el **token**`HTTP_OPTIONS` personalizado . 

### Inyección Basa en Propiedad

La técnica que hemos usado hasta ahora se llama inyección basada en constructor, ya que los proveedores se inyectan mediante el método constructor. En algunos casos muy específicos, **la inyección basada en propiedades** puede resultar útil. Por ejemplo, si su clase de nivel superior depende de uno o varios proveedores, pasarlos hacia arriba llamando `super()`a subclases desde el constructor puede ser muy tedioso. Para evitar esto, puede utilizar el `@Inject()`decorador a nivel de propiedad.

```tsx
import { Injectable, Inject } from '@nestjs/common';@Injectable()
export class HttpService<T> {
  @Inject('HTTP_OPTIONS')
  private readonly httpClient: T;
}
```

**Advertencia 💀: Si su clase no extiende otra clase, siempre debería preferir usar la inyección basada en constructor** . 

### Registro del proveedor

Hemos definido un proveedor ( `CatsService`) y tenemos un consumidor de ese servicio ( `CatsController`), necesitamos registrar el servicio con Nest para que pueda realizar la inyección. Hacemos esto editando nuestro archivo de módulo ( `app.module.ts`) y agregando el servicio a la `providers`matriz del `@Module()`decorador.

```tsx

import { Module } from '@nestjs/common';
import { CatsController } from './cats/cats.controller';
import { CatsService } from './cats/cats.service';@Module({
  controllers: [CatsController],
  providers: [CatsService],
})
export class AppModule {}
```

**Nest ahora podrá resolver las dependencias de la `CatsController`clase.**
----------------------------------------------------------------------------------------------------------------------------------------

## Reflexión

Los proveedores en NestJs nos ayudan a inyectar dependencias, por lo tanto eso nos ayuda a que los objetos puedan crear varias relaciones entre ellos. Los proveedores son un concepto fundamental en Nest. Muchas de las clases básicas de Nest pueden tratarse como proveedores: servicios, repositorios, fábricas, ayudantes, etc. La idea principal de un proveedor es que se puede **inyectar** como una dependencia; esto significa que los objetos pueden crear varias relaciones entre sí, y la función de "cablear" estos objetos se puede delegar en gran medida al sistema de ejecución de Nest.
----------------------------------------------------------------------------------------------------------------------------------------

### Analogía

Imagínate que estás organizando una pequeña en tu casa. Para que todo salga bien, necesitas diferentes elementos como comida, bebida, música, decoración, entre otros. En lugar de hacerlo todo tú mismo, decides contratar a proveedores que se encarguen de cada aspecto de la fiesta.

1. **Servicios**: Cada proveedor es un servicio que te ofrece algo específico. Por ejemplo, tienes un proveedor de catering que se encarga de la comida, otro proveedor para la música, y otro para la decoración. Estos proveedores son expertos en sus áreas y te brindan soluciones especializadas.
2. **Inyección de dependencia**: En lugar de preocuparte por cómo obtener cada servicio (comida, música, decoración), simplemente les dices a tus proveedores lo que necesitas y ellos te lo entregan en el momento adecuado. De este modo, tú puedes concentrarte en disfrutar de la fiesta y los proveedores se encargan de los detalles.
3. **Proveedores opcionales**: Algunos servicios podrían ser opcionales para tu fiesta. Por ejemplo, si el presupuesto es limitado, podrías prescindir de un proveedor de decoración o de un DJ profesional. Esto es similar a cómo en NestJS puedes marcar ciertas dependencias como opcionales.
4. **Inyección basada en propiedad**: A veces, necesitas acceder a un servicio específico directamente, como pedir una bebida o una canción específica al DJ durante la fiesta. En NestJS, esto es como inyectar una dependencia directamente en una propiedad de una clase para usarla cuando sea necesario.
5. **Registro del proveedor**: Al planificar la fiesta, haces una lista de los proveedores que vas a contratar y les informas sobre la fecha, hora y ubicación de la fiesta. En NestJS, haces algo similar al registrar los servicios que necesitas en un módulo para que Nest pueda administrarlos y usarlos cuando sea necesario.

----------------------------------------------------------------------------------------------------------------------------------------
### Resumen

En resumen NestJS, los proveedores son componentes clave que encapsulan la lógica de negocio, como servicios, repositorios, fábricas o ayudantes. Permiten que las clases se inyecten como dependencias en otras partes de la aplicación, facilitando la modularidad, mantenibilidad y testabilidad del código. NestJS utiliza un contenedor de inversión de control (IoC) para gestionar la inyección de dependencias, asegurando que los objetos se relacionen entre sí de manera eficiente. Los proveedores opcionales y la inyección basada en propiedades son características adicionales que brindan flexibilidad en la administración de dependencias. Cada proveedor tiene un trabajo específico y, cuando se integran correctamente, hacen que todo funcione de manera armoniosa y eficiente. NestJS se encarga de coordinar y conectar estos proveedores para que tú puedas concentrarte en la lógica de negocio sin preocuparte por los detalles de implementación.
----------------------------------------------------------------------------------------------------------------------------------------

### Referenciado

*Providers | NestJs: Documentation | NestJS - A progressive Node.js framework*. (s. f.). Documentation | NestJS - A progressive Node.js framework. Recuperado 23 de abril de 2024, de https://docs.nestjs.com 

*Conceptos Clave de NestJs* *|  Framework de NestJs:* diego.coder. (2024, febrero 1). Conceptos clave de Nestjs (Framework para Node.js). *Medium*. https://medium.com/@diego.coder/conceptos-clave-de-nestjs-framework-para-node-js-c169803d1bc7
--- 