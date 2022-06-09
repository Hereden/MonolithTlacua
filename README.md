# MonolithTlacua

Busqueda de implementar el proyecto integrador como monolito

# Herramientas

- JHipster
- Angular
- PrimeNG
- RxJava
- Jasper Reports

# Inicialización del proyecto

1. Tener nuestra carpeta lista
   1. mkdir MonolithTlacua && cd MonolithTlacua
2. Si no tenemos instalado Jhipster, instalarlo
   1. npm install -g generate-jhipster
3. Ejecutar el comando de JHipster "jhipster"
   1. Selecionar la configuración del proyecto:
   2. Monolitih / <enter> / Y / <enter> / HTTP / SQL / POSTGRESQL / POSTGRESQL / MAVEN / N / <enter> / Angular / N / Lumen / Primary / N / Spanish / Cypress, Gatling, Cucumber / N / N
   3. En caso de que tengas un .md te aparecera una opción de sobreescribir el archivo .md
4. Pasamos a movernos a la carpeta de Angular a instalar primeNG
   1. cd src/main/webapp
   2. npm install
   3. npm install primeng --save
   4. npm install primeicons --save
5. Agregamos los estilos en angular.json (Normalmente por la línea 38):

   ```json
   "node_modules/primeicons/primeicons.css",
   "node_modules/primeng/resources/themes/lara-light-blue/theme.css",
   "node_modules/primeng/resources/primeng.min.css",
   ```

6. Ejecutamos el proyecto por primera vez la parte de angular:

   ```bash
   $ npm start

   O podemos levantar el proyecto entero con:

   $ ./mvnw
   ```

7. En caso de darnos un error de browser-sync, dejecutar
   1. npm i browser-sync --save
8. Creamos nuestro modelo con JDL, tomando en cuenta los tipos de datos: <https://www.jhipster.tech/jdl/entities-fields#field-types-and-validations>

9. Descargamos nuestro modelo, preferiblemente ponemos el archivo en la carpeta raíz de nuestro proyecto, nuestro modelo debe de quedar algo así:

   ```jdl
   entity Persona{
   nombre String required minlength(2),
   apellido String required,
   sexo Genero,
   correo String required pattern(/^[^@\s]+@[^@\s]+\.[^@\s]+$/) unique,
   contrasena String required,
   domicilio String
   }

   enum Genero{
       MASCULINO, FEMENINO, OTRO
   }

   entity Articulos{
       nombre String required minlength(2),
       descripcion String required,
       precio Float required,
       stock Long required,
       colores String,
       imagenes String,
       tam Tamanos required
   }

   enum Tamanos {
       C, M, G, EG, EEG
   }


   entity Comentarios{
       comentario String minlength(5)
   }


   entity ProductoOrden {
       diaPedido ZonedDateTime required,
       estado OrdenEstado required,
       codigo String required
   }

   enum OrdenEstado {
       COMPLETADO, PENDIENTE, CANCELADO
   }

   entity OrdenArticulo {
       cantidad Integer required min(0),
       total BigDecimal required min(0)
   }


   relationship ManyToOne {
       OrdenArticulo{articulos(nombre) required} to Articulos
   }

   relationship OneToMany {
       Persona{orden} to ProductoOrden{persona(correo) required},
       ProductoOrden{ordenArticulo} to OrdenArticulo{orden(codigo) required},
       Articulos to Comentarios{calificaciones},
       Persona to Comentarios{comenta}
   }



   // Set pagination options
   paginate Articulos, Comentarios,ProductoOrden,OrdenArticulo with infinite-scroll
   paginate Persona with pagination

   // Use Data Transfer Objects (DTO)
   dto * with mapstruct

   ```

10. Para crear nuestras identidades con Jhipster procedemos a ejecutar el siguiente comando donde dejemos el archivo .jdl

    ```bash
        $ jhipster jdl tlacuaRiders.jdl
    ```
