# **SPRINT 1 — Análisis del Dominio (DOCUMENTO ENTREGADO POR EL PROFESOR)**

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

- Nombre
- CIF
- Dirección fiscal
- Teléfono
- Email de contacto

La empresa **no tiene CRUD** (solo existe una).  
Se podrá **editar**, pero no crear ni borrar.

---

## 📍 2.2. Sede

Cada empresa tiene una o varias sedes físicas.

**Atributos previstos:**

- ID
- Dirección completa (calle, número, CP, ciudad, provincia)
- Teléfonos
- Email de contacto

---

## 🗂 2.3. Departamento

Divisiones de trabajo dentro de la empresa.

**Atributos previstos:**

- ID
- Nombre
- Descripción

---

## 🏷 2.4. Categoría laboral

Clasifica el tipo de trabajo del empleado.

**Atributos previstos:**

- ID
- Nombre (Administrativo, Técnico, etc.)
- Descripción
- Nivel profesional (opcional)

---

## 💼 2.5. Puesto de trabajo

Representa una posición dentro de una sede y un departamento.

**Atributos previstos:**

- ID
- Sede
- Departamento
- Categoría laboral de referencia
- Nombre del puesto
- Descripción de funciones
- Estado (activo/inactivo)

---

## 👤 2.6. Empleado

Almacena la información personal y laboral del trabajador.

**Atributos previstos:**

- Nombre
- Apellidos
- DNI (clave natural, único)
- Teléfono
- Email corporativo
- Dirección personal
- Puesto asignado
- Categoría real
- Fechas de alta y baja
- Estado laboral

---

# 🔗 3. Relaciones entre las entidades

Estas relaciones ayudan a comprender cómo interactúan los objetos entre sí:

- Una **empresa** tiene varias **sedes**.
- Una **empresa** tiene varios **departamentos**.
- Una **categoría laboral** puede asignarse a varios puestos o empleados.
- Un **puesto de trabajo** está asociado a:
    - una sede
    - un departamento
    - una categoría laboral de referencia
- Un **empleado** tiene:
    - un puesto de trabajo
    - una categoría laboral real

Todas las relaciones se trabajarán mediante **composición** en los POJOs.

---

# 🧬 4. Identidad y unicidad de objetos

Para evitar duplicados y permitir el uso correcto de colecciones, cada clase tendrá una **clave natural**:

|Entidad|Identidad|
|---|---|
|Empresa|CIF|
|Sede|ID|
|Departamento|ID|
|Categoría laboral|ID|
|PuestoTrabajo|ID|
|Empleado|DNI|

Esto permitirá implementar con sentido `equals()` y `hashCode()` en el Sprint 3.

---

# 🧩 5. Herencia prevista en el dominio (se aplicará en Sprint 2.5)

La herencia se utilizará para mejorar el diseño:

### ✔ `Persona` → `Empleado`

Clase padre con:

- nombre
- apellidos
- dni

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

# 🎯 9. Conclusión del Sprint 1

Este Sprint sienta la base teórica del proyecto:

- Dominio definido
- Entidades claras
- Relaciones establecidas
- Reglas del negocio visibles
- Identidades asignadas
- Herencia prevista
- Arquitectura general acordada

A partir del Sprint 2, el alumnado empezará a programar.

---