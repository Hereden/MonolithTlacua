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
6. Ejecutamos el proyecto por primera vez:
   1. npm start
7. En caso de darnos un error de browser-sync, dejecutar
   1. npm i browser-sync --save
8. Cualquier import que hagamos de PrimeNG hay que importarlo a Home.module.
"node_modules/primeng/resources/primeng.min.css",

```
