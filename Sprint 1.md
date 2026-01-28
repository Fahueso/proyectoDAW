# **SPRINT 1 — Análisis del Dominio

**Estado:** ✔ Completado  
**Responsable:** Profesor  
**Alumnado:** Solo lectura  
**Trabajo requerido:** Ninguno  
**Objetivo:** Proporcionar una base sólida del dominio del proyecto antes de comenzar la programación.

---

# 📘 1. Visión general del proyecto

El objetivo del proyecto es desarrollar una aplicación de consola para gestionar distintos elementos de una empresa:

- Empleados
- Puestos de trabajo
- Categorías laborales
- Departamentos
- Sedes físicas
- Datos generales de la empresa

El proyecto se desarrollará aplicando **metodología Scrum**, control de versiones con **GitHub**, y trabajo en equipo mediante **ramas feature** con un **integrador** responsable de unir el código.

Este Sprint proporciona el análisis completo del dominio.  
Los siguientes Sprints se dedicarán ya a programar.

---

# 🧱 2. Entidades principales del dominio

A continuación se describen las entidades que formarán parte del sistema. Estas clases se desarrollarán en el **Sprint 2**, pero aquí se definen de forma conceptual.

---

## 🏢 2.1. Empresa

Representa la única empresa gestionada por la aplicación.

**Atributos previstos:**

- `id`: `long`
- `razonSocial`: `String`
- `nombreComercial`: `String`
- `formaJuridica`: `String`
- `cif`: `String`
- `direccionFiscal`: `String`
- `telefono`: `String`
- `email`: `String`

La empresa **no tiene CRUD** (solo existe una).  
Se podrá **editar**, pero no crear ni borrar.

---

## 📍 2.2. Sede

Cada empresa tiene una o varias sedes físicas.

**Atributos previstos:**

- `id`: `long`
- `empresaId`: `long`
- `tipo`: `String`
- `calle`: `String`
- `numero`: `String`
- `cp`: `String`
- `ciudad`: `String`
- `provincia`: `String`
- `emailContacto`: `String`

---

## 🗂 2.3. Departamento

Divisiones de trabajo dentro de la empresa.

**Atributos previstos:**

- `id`: `long`
- `empresaId`: `long`
- `codigo`: `String`
- `nombre`: `String`
- `descripcion`: `String`

---

## 🏷 2.4. Categoría laboral

Clasifica el tipo de trabajo del empleado.

**Atributos previstos:**

- `id`: `long`
- `empresaId`: `long`
- `convenio`: `String`
- `grupoProfesional`: `String`
- `nivel`: `String`
- `descripcion`: `String`

---

## 💼 2.5. Puesto de trabajo

Representa una posición dentro de una sede y un departamento.

**Atributos previstos:**

- `id`: `long`
- `sedeId`: `long`
- `departamentoId`: `long`
- `categoriaReferencia`: `long`
- `nombre`: `String`
- `descripcionFunciones`: `String`
- `jornada`: `String`
- `modalidad`: `String`
- `activo`: `boolean`

---

## 👤 2.6. Empleado

Almacena la información personal y laboral del trabajador.

**Atributos previstos:**

- `id`: `long`
- `puestoActual`: `long`
- `categoriaReal`: `long`
- `dni`: `String`
- `nombre`: `String`
- `apellidos`: `String`
- `emailCorporativo`: `String`
- `emailPersonal`: `String`
- `telefono`: `String`
- `direccion`: `String`
- `numeroSS`: `String`
- `fechaNacimiento`: `Date`
- `fechaAlta`: `Date`
- `fechaBaja`: `Date`
- `estadoLaboral`: `String`

---

## 🔗 2.7. Usuario

Representa un usuario del sistema, asociado a un empleado.

**Atributos previstos:**

- `id`: `long`
- `empleadoId`: `long`
- `username`: `String`
- `passwordHash`: `String`
- `activo`: `boolean`

---

## 🔗 2.8. Rol

Representa un rol dentro del sistema.

**Atributos previstos:**

- `id`: `long`
- `nombre`: `String`

---

## 🔗 2.9. UsuarioRol

Relación many-to-many entre usuarios y roles.

**Atributos previstos:**

- `id`: `long`
- `usuarioId`: `long`
- `rolId`: `long`

---

# 🔗 3. Relaciones entre las entidades

Estas relaciones ayudan a comprender cómo interactúan los objetos entre sí:

- Una **empresa** tiene varias **sedes**.
- Una **empresa** tiene varios **departamentos**.
- Una **empresa** tiene varias **categorías laborales**.
- Una **sede** puede tener varios **puestos de trabajo**.
- Un **departamento** puede tener varios **puestos de trabajo**.
- Una **categoría laboral** puede asignarse a varios **puestos de trabajo**.
- Un **puesto de trabajo** está asociado a:
    - una **sede**
    - un **departamento**
    - una **categoría laboral de referencia**
- Un **empleado** tiene:
    - un **puesto de trabajo**
    - una **categoría laboral real**
- Un **usuario** está asociado a un **empleado**.
- Un **usuario** puede tener varios **roles**.

Todas las relaciones se trabajarán mediante **composición** en los POJOs.

---

# 🧬 4. Identidad y unicidad de objetos

Para evitar duplicados y permitir el uso correcto de colecciones, cada clase tendrá una **clave natural**:

|Entidad|Identidad|
|---|---|
|Empresa|`cif`|
|Sede|`id`|
|Departamento|`id`|
|Categoría laboral|`id`|
|PuestoTrabajo|`id`|
|Empleado|`dni`|
|Usuario|`username`|
|Rol|`nombre`|

Esto permitirá implementar con sentido `equals()` y `hashCode()` en el Sprint 3.

---

# 🧩 5. Herencia prevista en el dominio (se aplicará en otro Sprint)
La herencia se utilizará para mejorar el diseño:

### ✔ `Persona` → `Empleado`

Clase padre con:

- `nombre`: `String`
- `apellidos`: `String`
- `dni`: `String`

El alumnado lo implementará más adelante.

### ✔ `Ubicacion` → `Sede`

Clase con dirección completa.

### ✔ (Opcional según nivel) `BaseEntity` → entidades con ID

Para unificar atributos comunes.

---

# 🗂 6. Reglas del dominio (business rules)

Estas reglas se aplicarán a partir del Sprint 3 (Servicios), pero se definen aquí:

- No puede existir un empleado con el mismo DNI.
- No puede existir un departamento con el mismo ID.
- Un puesto debe estar vinculado siempre a:
    - una sede existente
    - un departamento existente
    - una categoría válida
- Un empleado no puede darse de baja sin antes haber sido dado de alta.
- No se pueden eliminar sedes, puestos o departamentos si tienen empleados asociados.
- Un usuario debe tener un empleado asociado.
- Un usuario puede tener varios roles, pero debe tener al menos uno.

---

# 🧭 7. Arquitectura general prevista

La aplicación avanzará progresivamente hacia una arquitectura por capas:

```
(Usuario)
   ↓
Menú de consola
   ↓
Service Layer (CRUD + reglas de negocio)
   ↓
Persistencia (ficheros / DAO)
   ↓
POJOs
```

Las capas superiores nunca accederán directamente a colecciones.

---

# 📌 8. Fuera del alcance del Sprint 1

Este Sprint NO incluye:

- Codear POJOs
- Hacer menús
- Colecciones
- Excepciones
- Ficheros
- Serialización
- DAO
- Bases de datos

Todo eso comienza en el Sprint 2.

---

