# Manual Técnico - AVICAR

## Introducción
Starlight Cinema consiste en una aplicación web dinámica ofreciendo un amplio catálogo de películas del momento y funciones para satisfacer al cliente.

## Arquitectura del Sistema
El sistema Starlight Cinemas consta de tres componentes principales:
1. **Backend**: Desarrollado en Python.
2. **Frontend**: Desarrollado utilizando JavaScript, HTML, CSS.
3. **Gestor de Datos**: Desarrollado utilizando MYSQL.

## Requisitos Técnicos
1. **Backend**: NodeJS
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
1. Instalar NodeJS y npm.
2. Configurar un nuevo proyecto con npm init.
3. Instalar dependencias necesarias
**npm install express body-parser aws-sdk jsonfile**

### Ejemplo de Código para el Servidor
![Mi Imagen](img/code.png)

## Implementación del Frontend
### Configuración del Entorno
1. Instalar Angular, React o Vue CLI.
2. Crear un nuevo proyecto utilizando el CLI correspondiente.
3. Configurar servicios y componentes según las necesidades de la aplicación.
### Ejemplo de Configuración en Angular
1. Instalar Angular CLI:
**npm install -g @angular/cli**
2. Crear un nuevo proyecto:
**ng new avicar**
3. Crear componentes y servicios necesarios
**ng generate component login**
**ng generate service auth**

## Despliegue en AWS EC2
### Configuración de la Instancia
1. Crear una nueva instancia EC2 con Amazon Linux.
2. Instalar NodeJS y configurar el entorno.
3. Clonar el repositorio del proyecto desde Git.
4. Instalar dependencias y ejecutar el servidor

    **git clone https://github.com/usuario/avicar.git**
**cd avicar**
**npm install**
**npm start**
