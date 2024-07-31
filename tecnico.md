# Manual Técnico - Starlight Cinema

## Introducción
Starlight Cinema consiste en una aplicación web dinámica ofreciendo un amplio catálogo de películas del momento y funciones para satisfacer al cliente.

## Arquitectura del Sistema
El sistema Starlight Cinema consta de tres componentes principales:
1. **Backend**: Desarrollado en Python.
2. **Frontend**: Desarrollado utilizando JavaScript, HTML, CSS.
3. **Gestor de Datos**: Desarrollado utilizando MYSQL, JSON.

## Requisitos Técnicos
1. **Backend**: Python, Flask
2. **Frontend**: JavaScript, HTML, CSS
3. **Gestión de Datos**: MYSQL

## Estructura de Datos a Almacenar en MYSQL
### Ejemplo de Estructura de Usuarios
```json
{
    "usuarios": [
        {
            "id": 1,
            "nombre": "John",
            "apellido": "Doe",
            "usuario": "johndoe",
            "fotoPerfil": "url_a_la_foto",
            "correoElectronico": "john.doe@example.com",
            "contrasena": "hashed_password",
            "tipoUsuario": "turista"
        }
    ]
}
```
### Ejemplo de Estructura de Registro
```MYSQL
CREATE TABLE Registro (
    id INT AUTO_INCREMENT PRIMARY KEY,
    Usuario VARCHAR(255) NOT NULL,
    Email VARCHAR(255) NOT NULL,
    Contraseña VARCHAR(255) NOT NULL,	
    Validacion VARCHAR(255) NOT NULL,
    Verificado BOOLEAN NOT NULL DEFAULT FALSE,
    Correo_Enviado BOOLEAN NOT NULL DEFAULT FALSE,
    Tipo VARCHAR(50) NOT NULL
);
```

### Ejemplo de Estructura de Pelicula
```MYSQL
CREATE TABLE Pelicula (
    id INT AUTO_INCREMENT PRIMARY KEY,
    Titulo VARCHAR(255) NOT NULL,
    Descripcion TEXT NOT NULL,
    Genero VARCHAR(20) NOT NULL,
    Duracion VARCHAR(10) NOT NULL,
    Funcion1 VARCHAR(10) NOT NULL,
    Funcion2 VARCHAR(10) NOT NULL,
    Funcion3 VARCHAR(10) NOT NULL,
    Funcion4 VARCHAR(10) NOT NULL,
    Sala VARCHAR(10) NOT NULL,
    Carrusel_img_path VARCHAR(255) NOT NULL,
    Poster_img_path VARCHAR(255) NOT NULL,
    Fecha_creacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
### Ejemplo de Estructura de Pagos
```MYSQL
CREATE TABLE Pagos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    Nombre VARCHAR(100) NOT NULL,
    Email VARCHAR(100) NOT NULL,
    Pelicula VARCHAR(255) NOT NULL,
    Horario VARCHAR(50) NOT NULL,
    Sala VARCHAR(10) NOT NULL,
    NIT VARCHAR(20) NOT NULL,
    NO_Tarjeta VARCHAR(255) NOT NULL,
    Fecha_Expiracion VARCHAR(10) NOT NULL,
    CVV VARCHAR(255) NOT NULL,
    AsientosSeleccionados JSON NOT NULL,
    Total DECIMAL(10, 2) NOT NULL,
    FechaCreacion TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
### Ejemplo de Estructura de Reserva
```MYSQL
CREATE TABLE Reservas (
    id INT AUTO_INCREMENT PRIMARY KEY,
    pelicula_id INT NOT NULL,
    horario VARCHAR(50) NOT NULL,
    asiento VARCHAR(10) NOT NULL,
    pago_id INT NOT NULL,
    FOREIGN KEY (pelicula_id) REFERENCES Pelicula(id),
    FOREIGN KEY (pago_id) REFERENCES Pagos(id)
);
```

## Implementación del Backend
### Configuración del Entorno
1. Instalar Flask Json.
3. Realizar la conexion con la base de datos creada en MYSQL.

### Ejemplo de Código para el Servidor
![Mi Imagen](img/code.png)

## Implementación del Frontend
### Configuración del Entorno
1. Crear un proyecto utilizando Visual Code. 
2. Crear carpetas HTML, JavaScrip, CSS.
3. Crear o modificarlas interfazes que semostraran al usuario colocarle las condiciones y animación.
   
### Ejemplo de la conexion con MYSQL 
1. Crear la base de datos en MYSQL con las tablas necesarias. 
2. Crear la Api.
3. Crear la conexion de la api con MYSQL.
4. Crear componentes y servicios necesarios
