
Alumna: Luisina F Battella Vercesi
Comision: 3k10

# Trabajo practico de Traza correspondiente a la catedra de desarrollo de software. 

## Objetivo
Implementar operaciones CRUD (Crear, Leer, Actualizar y Eliminar) sobre una entidad `Empresa`, utilizando buenas prácticas de programación en Java:
- Separación entre modelo y servicio.
- Uso de Lombok para simplificar código repetitivo.
- Patrones de diseño básicos como Builder para instanciación fluida.

## Estructura del proyecto
El proyecto se organiza en paquetes: Uno de ellos es Modelo que contiene a todas las clases.

### Main (`org.example`)
Punto de entrada del programa. Se crean las entidades y se ejecutan las operaciones CRUD.

## Clase Empresa
Define los atributos y relaciones principales. Gracias a Lombok, los métodos getters, setters, `toString`, `equals`, `hashCode` y constructores se generan automáticamente.

**Decisiones de diseño:**
- `@Builder`: permite construir instancias con un estilo legible y flexible.
- `@EqualsAndHashCode.Exclude` y `@ToString.Exclude`: evitan bucles infinitos al imprimir relaciones entre empresa y sucursal.
- `@Builder.Default`: inicializa la colección `sucursales` para evitar `NullPointerException`.

## Clase EmpresaServicio
Implementa la lógica CRUD sobre una colección en memoria (`Set`).

**Principales métodos:**
- `guardar(Empresa e)`: agrega una empresa.
- `listar()`: muestra todas las empresas con detalle de sus sucursales.
- `buscarPorId(Integer id)`: retorna una empresa según su ID.
- `buscarPorNombre(String nombre)`: retorna una empresa según su nombre.
- `actualizarCuit(Integer id, Long nuevoCuit)`: modifica el CUIT de una empresa existente.
- `eliminar(Integer id)`: elimina una empresa por ID.

**Decisiones de diseño:**
- Uso de Streams para búsquedas rápidas y legibles.
- Validaciones simples (`null`, colecciones vacías) en lugar de `try/catch` innecesarios.
- Separación clara de responsabilidades: `EmpresaServicio` administra datos, `Main` los consume.

## Conclusiones
- La implementación demuestra cómo aplicar CRUD básico en Java sin necesidad de base de datos, utilizando colecciones en memoria.
- Lombok simplifica el código de modelos, reduciendo la repetición.
- `EmpresaServicio` permite separar responsabilidades, haciendo que el código sea más mantenible y escalable.
- El patrón Builder facilita la instanciación de entidades complejas.
