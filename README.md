# Prices API – Prueba técnica ODEENE

Servicio Spring Boot 2.7.18 (Java 11) que expone un endpoint para consultar el precio aplicable por fecha, producto y brand. Usa H2 en memoria con datos iniciales.

**Requisitos**
* Java 11
* Maven 3.8+ (o el wrapper mvnw/mvnw.cmd)

# Compilación, tests y ejecución
**Compilar y ejecutar tests**
* mvn clean test

**Arrancar la aplicación**
* mvn spring-boot:run

# Base de datos (H2)

* JDBC URL: jdbc:h2:mem:testdb
* Consola: http://localhost:8080/h2-console

* User: sa (sin password)
* La BD se inicializa con schema.sql + data.sql.

# Endpoint

* GET /prices?date=yyyy-MM-dd-HH.mm.ss&productId={id}&brandId={id}

**Parámetros:**

* date (p.ej. 2020-06-14-10.00.00)
* productId (p.ej. 35455)
* brandId (p.ej. 1)

**Respuesta: productId, brandId, priceList, startDate, endDate, price , curr.**

Ejemplos (cURL)
* curl "http://localhost:8080/prices?date=2020-06-14-10.00.00&productId=35455&brandId=1"
* curl "http://localhost:8080/prices?date=2020-06-14-16.00.00&productId=35455&brandId=1"
* curl "http://localhost:8080/prices?date=2020-06-14-21.00.00&productId=35455&brandId=1"
* curl "http://localhost:8080/prices?date=2020-06-15-10.00.00&productId=35455&brandId=1"
* curl "http://localhost:8080/prices?date=2020-06-16-21.00.00&productId=35455&brandId=1"
