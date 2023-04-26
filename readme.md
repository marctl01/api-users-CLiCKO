Proyecto de API de usuarios.

Este proyecto implementa un CRUD básico de usuarios utilizando Laravel 9. La API se puede consumir utilizando Postman y requiere autenticación.


INSTALACIÓN: 
Clonar el repositorio desde GitHub:    git clone https://github.com/marctl01/api-users-CLiCKO

Configurar la base de datos en el archivo .env.

Actualizacion de  dependencias:
- composer update

Ejecutar las migraciones para crear la tabla de usuarios:
- php artisan migrate

Ejecutar el Seeder para añadir 20 usuarios a la base de datos:
- php artisan db:seed --class=UserSeeder

Iniciar el servidor de Laravel: 
- php artisan serve


RUTAS:

POST /api/register : Registra un usuario.

{
    "name":"admin",
    "username":"admin",
    "email":"adm@adm.com",
    "password":"1234",
    "confirm_password":"1234"
}

POST /api/login : Comprueba el email y la password, devuelve un token para poder acceder a los metodos del CRUD

{
    "email":"adm@adm.com",
    "password":"1234"
}

Introduccion del token en postman:
1) Apartado Authoritation
2) Tipo Bearer Token
3) Introducimos el token copiado. (Todos los metodos necesitan el token en postman)

GET /api/users: Devuelve una lista de todos los usuarios registrados en la base de datos.
- http://localhost:8000/api/users

GET /api/users/{id}: Devuelve los datos de un usuario específico, identificado por su ID.
- http://localhost:8000/api/users/1

POST /api/users: Crea un nuevo usuario en la base de datos. Los datos deben enviarse en formato JSON en el cuerpo de la petición.
- http://localhost:8000/api/users
{
    "name": "Juan Perez",
    "username": "juanpi",
    "email":"juan.perez@example.com",
    "password":"123456789"
}

PUT /api/users/{id}: Actualiza los datos de un usuario específico, identificado por su ID. Los datos deben enviarse en formato JSON en el cuerpo de la petición.
- http://localhost:8000/api/users/1
{
    "name": "Juan Perez",
    "username": "juanpi",
    "email": "juan.perez@example.com",
    "password": "987654321"
}

DELETE /api/users/{id}: Elimina un usuario específico de la base de datos, identificado por su ID.
- http://localhost:8000/api/users/1

GET /api/domains: Devuelve los 3 dominios más usados en los emails de usuarios, en orden descendente.
- http://localhost:8000/api/domains
