# Tenpo Infra

Este repositorio contiene la infraestructura de la aplicación "Tenpo Transactions", que incluye los servicios necesarios para levantar la base de datos, el backend y el frontend usando Docker y Docker Compose.

- Author: Rodrigo Espinoza A.
- Email: rodrigo.espinoza.aguayo@gmail.com

## Requisitos

- [Docker](https://www.docker.com/get-started) (versión 20.10 o superior)
- [Docker Compose](https://docs.docker.com/compose/) (versión 1.27.0 o superior)

## Descripción de los Servicios

Este proyecto utiliza Docker Compose para definir y ejecutar los siguientes servicios:

- **tenpo-postgres**: Base de datos PostgreSQL.
- **tenpo-backend**: Backend de la aplicación (Spring Boot).
- **tenpo-frontend**: Frontend de la aplicación (React).

Cada servicio se ejecuta dentro de un contenedor Docker y está configurado para interactuar entre sí a través de una red definida en el archivo `docker-compose.yml`.

## Referencias a Proyectos Relacionados

Las imagenes del Backend y del Frontend fueron generadas a partir del codigo de los proyectos relacionados disponibles tambien en Github:

- **Backend**: [tenpo-backend](https://github.com/codelious/tenpo-backend) (Repositorio con el código del backend, construido con Spring Boot).
- **Frontend**: [tenpo-frontend](https://github.com/codelious/tenpo-frontend) (Repositorio con el código del frontend, construido con React).

## Instrucciones para Levantar el Proyecto

### 1. Clonar el Repositorio

Primero, clona el repositorio en tu máquina local:

```bash
git clone https://github.com/codelious/tenpo-infra.git
cd tenpo-infra
```

### 2. Iniciar Docker Compose

Para levantar todos los servicios definidos en el archivo docker-compose.yml, usa el siguiente comando:

```bash
docker-compose up -d
```

Este comando descargará las imágenes de los servicios si no están presentes en tu máquina local, y luego iniciará los contenedores en segundo plano.

### 3. Verificar los Servicios

Para verificar que los contenedores se estén ejecutando correctamente, puedes usar el siguiente comando:

```bash
docker-compose ps
```

### 4. Acceder a los Servicios

Una vez que los contenedores estén en funcionamiento, puedes acceder a los servicios de la siguiente manera:
-	Frontend (React): http://localhost:3000
-	Backend (Spring Boot): http://localhost:8080
-	Base de datos PostgreSQL: Puedes conectarte a la base de datos usando el cliente PostgreSQL en localhost:5432 con el siguiente usuario y contraseña:
-	Usuario: user
-	Contraseña: password
-	Base de datos: transactions_db

### 5. Detener los Servicios

Cuando hayas terminado de probar, puedes detener los servicios con el siguiente comando:

```bash
docker-compose down
```
Esto detendrá y eliminará los contenedores, pero no eliminará los volúmenes de datos. Si deseas eliminar los volúmenes (por ejemplo, para reiniciar la base de datos), puedes usar:

```bash
docker-compose down -v
```

### 6. Probar la Aplicación

Una vez que todo esté levantado, puedes probar el funcionamiento de la aplicación accediendo al frontend en http://localhost:3000, que debería estar interactuando con el backend en http://localhost:8080.

Si todo funciona correctamente, deberías ver la interfaz de usuario y ser capaz de interactuar con el backend a través del frontend.

Notas Adicionales
-	Asegúrate de que Docker esté en funcionamiento antes de ejecutar los comandos.
-	Los servicios están configurados para reiniciarse automáticamente, lo que significa que en caso de fallo, Docker intentará reiniciarlos.
-	Si necesitas realizar cambios en las imágenes del backend o frontend, recuerda reconstruir las imágenes y hacer docker-compose up nuevamente.
