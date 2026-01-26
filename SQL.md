
# 🗄️ **SQL DEL SPRINT 1 (MySQL)**

### _Modelo conceptual implementado sin herencia aún_

_(La herencia aparecerá en el modelo Java, pero el SQL mantiene estructura plana para BD)_

```sql
-- -----------------------------------------------------

-- SPRINT 1 - MODELO DE DATOS DEL DOMINIO (MySQL)

-- Entregado por el profesor

-- -----------------------------------------------------

  

CREATE DATABASE IF NOT EXISTS empresa_gestion;

USE empresa_gestion;

  

-- -----------------------------------------------------

-- Tabla: Empresa

-- Nota: solo habrá un registro, pero se define completa.

-- -----------------------------------------------------

CREATE TABLE empresa (

    id                  BIGINT AUTO_INCREMENT PRIMARY KEY,

    nombre              VARCHAR(100) NOT NULL,

    cif                 VARCHAR(20) NOT NULL UNIQUE,

    direccion_fiscal    VARCHAR(200),

    telefono            VARCHAR(20),

    email               VARCHAR(100)

);

  

-- -----------------------------------------------------

-- Tabla: Sede

-- -----------------------------------------------------

CREATE TABLE sede (

    id                  BIGINT AUTO_INCREMENT PRIMARY KEY,

    calle               VARCHAR(100) NOT NULL,

    numero              VARCHAR(10),

    cp                  VARCHAR(10),

    ciudad              VARCHAR(50),

    provincia           VARCHAR(50),

    email_contacto      VARCHAR(100)

);

  

-- Teléfonos de la sede (relación 1:N)

CREATE TABLE sede_telefono (

    id          BIGINT AUTO_INCREMENT PRIMARY KEY,

    sede_id     BIGINT NOT NULL,

    telefono    VARCHAR(20) NOT NULL,

    FOREIGN KEY (sede_id) REFERENCES sede(id)

);

  

-- -----------------------------------------------------

-- Tabla: Departamento

-- -----------------------------------------------------

CREATE TABLE departamento (

    id           BIGINT AUTO_INCREMENT PRIMARY KEY,

    nombre       VARCHAR(100) NOT NULL UNIQUE,

    descripcion  VARCHAR(255)

);

  

-- -----------------------------------------------------

-- Tabla: Categoria Laboral

-- -----------------------------------------------------

CREATE TABLE categoria_laboral (

    id                  BIGINT AUTO_INCREMENT PRIMARY KEY,

    nombre              VARCHAR(100) NOT NULL UNIQUE,

    descripcion         VARCHAR(255),

    nivel_profesional   VARCHAR(50)

);

  

-- -----------------------------------------------------

-- Tabla: Puesto de Trabajo

-- -----------------------------------------------------

CREATE TABLE puesto_trabajo (

    id                      BIGINT AUTO_INCREMENT PRIMARY KEY,

    sede_id                 BIGINT NOT NULL,

    departamento_id         BIGINT NOT NULL,

    categoria_ref_id        BIGINT NOT NULL,

    nombre                  VARCHAR(100),

    descripcion_funciones   VARCHAR(255),

    activo                  BOOLEAN NOT NULL DEFAULT TRUE,

  

    FOREIGN KEY (sede_id) REFERENCES sede(id),

    FOREIGN KEY (departamento_id) REFERENCES departamento(id),

    FOREIGN KEY (categoria_ref_id) REFERENCES categoria_laboral(id)

);

  

-- -----------------------------------------------------

-- Tabla: Empleado

-- -----------------------------------------------------

CREATE TABLE empleado (

    id                  BIGINT AUTO_INCREMENT PRIMARY KEY,

    dni                 VARCHAR(20) NOT NULL UNIQUE,

    nombre              VARCHAR(100) NOT NULL,

    apellidos           VARCHAR(100) NOT NULL,

    email_corporativo   VARCHAR(100),

    email_personal      VARCHAR(100),

    telefono            VARCHAR(20),

    direccion           VARCHAR(200),

  

    puesto_id           BIGINT,

    categoria_real_id   BIGINT,

  

    fecha_alta          DATE NOT NULL,

    fecha_baja          DATE,

    estado_laboral      VARCHAR(50),

  

    FOREIGN KEY (puesto_id) REFERENCES puesto_trabajo(id),

    FOREIGN KEY (categoria_real_id) REFERENCES categoria_laboral(id)

);
```


---

# 🚀 ¿Quieres que prepare también el **diagrama ER** basado en este SQL?

Puedo generarlo en:

- Texto estructurado
- ASCII-art
- Notación UML
- Notación entidad-relación clásica
- O incluso una versión lista para pegar en draw.io

Solo dime:\ 👉 **“Hazme el diagrama ER del Sprint 1”**