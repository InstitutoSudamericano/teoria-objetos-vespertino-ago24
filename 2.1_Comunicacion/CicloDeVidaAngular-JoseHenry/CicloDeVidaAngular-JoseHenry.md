## Ciclo de vida de los componentes de Angular 

## Teoría 
En Angular, los componentes tienen un ciclo de vida con 8 etapas o "lifecycle hooks". Estos eventos se pueden utilizar en diferentes fases de la aplicación para controlar los componentes. Como los componentes son clases de TypeScript, cada uno debe tener un método constructor.

El constructor de la clase del componente se ejecuta primero, antes que cualquier otro lifecycle hook. Es el mejor lugar para inyectar dependencias en el componente. Después del constructor, Angular ejecuta los métodos de ciclo de vida en un orden específico.

### **1. Creación del Componente**

Cuando Angular crea un componente, inicia varios pasos esenciales, que incluyen la configuración de dependencias, la inicialización de propiedades y la construcción de la vista.

### **Hooks:**

- **`ngOnChanges`**: Se llama antes del **`ngOnInit`** y cada vez que cambian las propiedades enlazadas a datos (**`@Input`**). Recibe un objeto **`SimpleChanges`** que contiene los cambios.
- **`ngOnInit`**: Se llama una vez, justo después de la primera ejecución de **`ngOnChanges`**. Ideal para poder inicializar el componente.

### **2. Renderización del Componente**

Durante esta fase, Angular procesa las vistas y las plantillas del componente.

### **Hooks:**

- **`ngDoCheck`**: Se llama durante cada ciclo de detección de cambios. Útil para la lógica personalizada de detección de cambios.
- **`ngAfterContentInit`**: Se llama después de insertar el contenido proyectado en el componente. Solo se llama una vez.
- **`ngAfterContentChecked`**: Se llama después de cada verificación de cambios en el contenido proyectado. Puede llamarse múltiples veces.

### **3. Actualización de la Vista del Componente**

Después de que Angular haya proyectado el contenido y construido la vista, entra en la fase de detección y actualización de cambios de la vista.

### **Hooks:**

- **`ngAfterViewInit`**: Se llama una vez después de que Angular ha inicializado las vistas del componente y sus vistas hijas.
- **`ngAfterViewChecked`**: Se llama después de cada verificación de cambios en las vistas del componente y sus vistas hijas. Puede llamarse múltiples veces.

### **4. Destrucción del Componente**

Cuando un componente ya no es necesario, Angular lo destruye y ejecuta el hook final.

### **Hooks:**

- **`ngOnDestroy`**: Se llama justo antes de que Angular destruya el componente. Útil para realizar limpieza como desuscribirse de observables o eliminar manejadores de eventos.

## Reflexión
Comprender el ciclo de vida de los componentes en Angular es esencial para aprovechar al máximo las capacidades del framework. Los hooks del ciclo de vida proporcionan puntos de entrada específicos para ejecutar lógica en momentos clave, desde la inicialización hasta la destrucción de un componente:

1. **Inicialización** (**`ngOnInit`**, **`ngOnChanges`**): Permite configurar y preparar el componente, asegurando que esté listo para manejar la interacción del usuario y la entrada de datos.
2. **Renderización y Proyección de Contenido** (**`ngDoCheck`**, **`ngAfterContentInit`**, **`ngAfterContentChecked`**): Facilitan la gestión de la integración y actualización de contenido dinámico, asegurando que la interfaz de usuario se mantenga sincronizada con el estado de la aplicación.
3. **Actualización de la Vista** (**`ngAfterViewInit`**, **`ngAfterViewChecked`**): Permiten optimizar y ajustar la representación visual del componente, mejorando la experiencia del usuario mediante la manipulación directa del DOM y la integración con bibliotecas de terceros.
4. **Destrucción** (**`ngOnDestroy`**): Es crucial para limpiar recursos y prevenir fugas de memoria, garantizando que la aplicación permanezca eficiente y libre de errores.

La combinación de una comunicación efectiva entre componentes y una gestión cuidadosa del ciclo de vida en Angular permite a los desarrolladores construir aplicaciones sofisticadas y responsivas. Estas prácticas no solo mejoran la calidad del código, sino que también facilitan la colaboración en equipo y la escalabilidad del proyecto.

## Analogía 
Imaginemos que cada componente de Angular es como un árbol en un jardín. Desde la plantación de una semilla hasta la caída de sus hojas en otoño, cada etapa en la vida del árbol corresponde a un hook del ciclo de vida de un componente de Angular.

### **1. Plantación de la Semilla (Constructor)**

- **Analogía:** Plantar una semilla en el suelo.
- **Angular:** El constructor del componente se llama y se preparan las bases iniciales para el crecimiento del componente.
    
    ```tsx
    typescriptCopiar código
    constructor() {
      console.log('Plantando la semilla');
    }
    ```
    

### **2. Germinación y Crecimiento Inicial (ngOnChanges, ngOnInit)**

- **Analogía:** La semilla germina y comienza a crecer.
- **Angular:** **`ngOnChanges`** se llama cuando cambian las propiedades enlazadas a datos y **`ngOnInit`** se llama después de la primera inicialización, estableciendo el ambiente inicial del componente.
    
    ```tsx
    typescriptCopiar código
    ngOnChanges(changes: SimpleChanges) {
      console.log('La semilla está germinando', changes);
    }
    
    ngOnInit() {
      console.log('El árbol comienza a crecer');
    }
    ```
    

### **3. Desarrollo de Hojas y Ramas (ngDoCheck, ngAfterContentInit, ngAfterContentChecked)**

- **Analogía:** El árbol desarrolla hojas y ramas, creciendo en tamaño y complejidad.
- **Angular:** **`ngDoCheck`** se llama para detectar cambios personalizados, **`ngAfterContentInit`** se llama después de que el contenido proyectado está inicializado y **`ngAfterContentChecked`** después de que se verifica.
    
    ```tsx
    typescriptCopiar código
    ngDoCheck() {
      console.log('Verificando el crecimiento del árbol');
    }
    
    ngAfterContentInit() {
      console.log('Las hojas y ramas comienzan a desarrollarse');
    }
    
    ngAfterContentChecked() {
      console.log('Verificando las hojas y ramas');
    }
    ```
    

### **4. Producción de Frutos (ngAfterViewInit, ngAfterViewChecked)**

- **Analogía:** El árbol está maduro y comienza a producir frutos.
- **Angular:** **`ngAfterViewInit`** se llama después de que las vistas del componente y sus hijos están inicializadas y **`ngAfterViewChecked`** se llama después de cada verificación de cambios en las vistas.
    
    ```tsx
    typescriptCopiar código
    ngAfterViewInit() {
      console.log('El árbol ha madurado y produce frutos');
    }
    
    ngAfterViewChecked() {
      console.log('Verificando los frutos y las ramas');
    }
    ```
    

### **5. Pérdida de Hojas en Otoño (ngOnDestroy)**

- **Analogía:** Las hojas del árbol caen y el árbol se prepara para el invierno.
- **Angular:** **`ngOnDestroy`** se llama justo antes de que el componente se destruya, permitiendo limpiar recursos y suscripciones.
    
    ```tsx
    typescriptCopiar código
    ngOnDestroy() {
      console.log('El árbol pierde sus hojas y se prepara para el invierno');
    }
    
    ```
    
## Resumen
El ciclo de vida de un componente en Angular consta de varias etapas, cada una asociada con un hook específico que permite a los desarrolladores ejecutar lógica en momentos clave del ciclo de vida del componente. A continuación, se presenta un resumen de estos hooks y sus propósitos:

1. **Creación del Componente**
    - **Constructor**: Inicializa el componente.
    - **`ngOnChanges`**: Se llama cada vez que cambian las propiedades enlazadas a datos (**`@Input`**).
    - **`ngOnInit`**: Se llama una vez, justo después de la primera ejecución de **`ngOnChanges`**. Se utiliza para inicializar el componente.
2. **Renderización del Componente**
    - **`ngDoCheck`**: Se llama durante cada ciclo de detección de cambios. Útil para la lógica personalizada de detección de cambios.
    - **`ngAfterContentInit`**: Se llama después de insertar el contenido proyectado en el componente. Solo se llama una vez.
    - **`ngAfterContentChecked`**: Se llama después de cada verificación de cambios en el contenido proyectado. Puede llamarse múltiples veces.
3. **Actualización de la Vista del Componente**
    - **`ngAfterViewInit`**: Se llama una vez después de que Angular ha inicializado las vistas del componente y sus vistas hijas.
    - **`ngAfterViewChecked`**: Se llama después de cada verificación de cambios en las vistas del componente y sus vistas hijas. Puede llamarse múltiples veces.
4. **Destrucción del Componente**
    - **`ngOnDestroy`**: Se llama justo antes de que Angular destruya el componente. Se utiliza para realizar tareas de limpieza como desuscribirse de observables o eliminar manejadores de eventos.

### **Secuencia de Hooks del Ciclo de Vida**

1. **Inicialización**:
    - Constructor
    - **`ngOnChanges`**
    - **`ngOnInit`**
2. **Renderización**:
    - **`ngDoCheck`**
    - **`ngAfterContentInit`**
    - **`ngAfterContentChecked`**
3. **Actualización de la Vista**:
    - **`ngAfterViewInit`**
    - **`ngAfterViewChecked`**
4. **Destrucción**:
    - **`ngOnDestroy`**

## Referencias 
*Angular: Componentes y sus ciclos de vida:* <https://medium.com/angular-chile/angular-componentes-y-sus-ciclos-de-vida-aa639e13a688>

*Ciclos de vida en Angular: La guía definitiva:* <https://blog.enriqueoriol.com/2018/10/ciclos-de-vida-en-angular-la-guia-definitiva.html>

## Link de YouTube: <https://youtu.be/6516GEQpZ7Y>