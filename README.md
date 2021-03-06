# APIRest - Customers

## Requerimientos técnicos

* PHP >= 8.0.
* Composer >= 2.3.7.
* Docker Desktop >= 4.9.1 (Solo entorno desarrollo).

## Make

Para inicalizar el proyecto siga los siguientes comandos:

```
git clone https://github.com/lecheynata/gdalab.git
cd gdalab
make modules_clone
make build
```

## Configurar variables de entorno

**Asignar los parametros siguientes de conexión por defecto para conectar a la base de datos.

```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=testing
DB_USERNAME=root
DB_PASSWORD=
```

## Inicializar Aplicación

**Ejecutar el siguiente comando para inicializar la aplicación dentro de un entorno Docker.

```
make up
```

La api puede ser accedida desde http://localhost/api.

## Database seeding and refresing

**Rellenar la base de datos con los datos basicos para su uso en donde se incluyen: customers, communes, regions and users.

```
make populate_db
```

**Refrescando la base de datos

```
make repopulate_db
```

## API Specification

## Obtener el listado de usuarios

### Request

`GET /api/users`

    curl -i -H 'Accept: application/json' http://localhost/api/users

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    []

## Obtener el token de acceso

### Request

`POST /api/auth`

    curl -i -H 'Accept: application/json' \
      -d 'email=<email>&password=<password>' \
      http://localhost/api/auth

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    {"success":true,"data":{"token":"2|9UfXqvHPAX68uN75hxLRRCRef0hYR1xtsue57uLK"}}

## Obtener el listado de clientes

### Request

`GET /api/customers`

    curl -i -H 'Accept: application/json' http://localhost/api/customers

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    {"data":[]}

## Registrar a un cliente

### Request

`POST /api/customers`

    curl -i -H 'Accept: application/json' \
      -H "Authorization: Bearer <token>" \
      -d 'dni=<dni>&id_reg=<id_reg>&id_com=<id_com>&email=<email>&name=<name>&last_name=<last_name>&address=<address>' \
      http://localhost/api/auth

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    {"success":true}

## Eliminar un cliente

### Request

`DELETE /api/customers/dni`

    curl -i -H 'Accept: application/json' \
      -H "Authorization: Bearer <token>" \
      http://localhost/api/customers/<dni>

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    {"success":true}

## Consultar un cliente

### Request

`DELETE /api/customers/dni|email`

    curl -i -H 'Accept: application/json' \
      -H "Authorization: Bearer <token>" \
      http://localhost/api/customers/<dni>|<email>

### Response

    HTTP/1.1 200 OK
    Status: 200 OK
    Connection: close
    Content-Type: application/json

    {"success":true,"data": {}}
