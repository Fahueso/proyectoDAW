
#  **SPRINT 2 — Modelado de POJOs del Dominio**

**Estado:** Pendiente  
**Responsables:** Equipo de desarrollo (alumnado)  
**Objetivo:** Implementar las clases básicas del dominio (POJOs), aplicando composición, encapsulación y las identidades definidas en el Sprint 1.

---

# 🎯 **Objetivo general del Sprint**

Crear todas las clases del dominio (POJOs) con:

- Atributos privados
- Constructores
- Getters y setters
- Identidad clara (campo clave natural o ID)
- Composición entre clases
- Preparación para futura herencia (sin implementarla todavía)
- Preparación para equals/hashCode (que llegará en Sprint 3)

Este Sprint sienta **las bases del modelo de datos** de toda la aplicación.

---

# 📘 1. **Entidades a implementar en este Sprint**

Los alumnos deben crear las siguientes clases:

1. `Empresa`
2. `Sede`
3. `Departamento`
4. `CategoriaLaboral`
5. `PuestoTrabajo`
6. `Empleado`

➡ Todas estas clases deben estar en un paquete apropiado, por ejemplo:  
`com.miempresa.modelo`

---

# 🧱 2. **Requisitos técnicos obligatorios**

Cada POJO debe contener:

### ✔ Atributos privados

### ✔ Constructor vacío

### ✔ Constructor con parámetros mínimos

### ✔ Getters y setters para todos los campos

### ✔ Encapsulación correcta

### ✔ Composición entre clases (por ejemplo: PuestoTrabajo contiene Sede, Departamento, etc.)

### ✔ `implements Serializable` (aunque se usará más adelante)

### ✔ Campo de identidad (ID o DNI) correctamente definido

> ⚠ **NO implementar todavía equals/hashCode — eso se hará en Sprint 3.**  
> ⚠ **NO implementar herencia todavía — eso será Sprint 2.5.**

---

# 🧩 3. **Atributos obligatorios de cada clase**

Listado oficial para asegurar homogeneidad:

---

## 🏢 Empresa

- `String nombre`
- `String cif`
- `String direccionFiscal`
- `String telefono`
- `String email`

---

## 📍 Sede

- `Long id`
- `String calle`
- `String numero`
- `String cp`
- `String ciudad`
- `String provincia`
- `List<String> telefonos`
- `String emailContacto`

---

## 🗂 Departamento

- `Long id`
- `String nombre`
- `String descripcion`

---

## 🏷 CategoriaLaboral

- `Long id`
- `String nombre`
- `String descripcion`
- `String nivelProfesional` (opcional)

---

## 💼 PuestoTrabajo

- `Long id`
- `Sede sede`
- `Departamento departamento`
- `CategoriaLaboral categoriaReferencia`
- `String nombre`
- `String descripcionFunciones`
- `boolean activo`

---

## 👤 Empleado

- `String nombre`
- `String apellidos`
- `String dni` (identidad, clave natural)
- `String emailCorporativo`
- `String emailPersonal`
- `String telefono`
- `String direccion`
- `PuestoTrabajo puesto`
- `CategoriaLaboral categoriaReal`
- `LocalDate fechaAlta`
- `LocalDate fechaBaja`
- `String estadoLaboral`

---

# 🧭 4. **Tareas del Sprint (para Trello)**

Copia y pega estas tarjetas directamente:

---

### 🟦 **HU-001 — Crear POJO Empresa**

**Descripción:**  
Implementar la clase `Empresa` con atributos, constructores y getters/setters.

**Criterios de aceptación:**

- Atributos privados
- Constructor vacío y completo
- Composición NO necesaria
- Clase compila sin errores

---

### 🟦 **HU-002 — Crear POJO Sede**

**Descripción:**  
Implementar clase Sede, incluyendo dirección y medios de contacto.

**Criterios de aceptación:**

- Lista de teléfonos inicializada
- Atributo `id` obligatorio
- Clase compila sin errores

---

### 🟦 **HU-003 — Crear POJO Departamento**

**Criterios de aceptación:**

- Atributos privados
- ID obligatorio
- Clase simple, sin composición

---

### 🟦 **HU-004 — Crear POJO CategoriaLaboral**

**Criterios de aceptación:**

- Identidad por ID
- Campo nivelProfesional opcional
- Clase compila

---

### 🟦 **HU-005 — Crear POJO PuestoTrabajo**

**Descripción:**  
Contiene referencias a Sede, Departamento y CategoriaLaboral.

**Criterios de aceptación:**

- Composición correctamente aplicada
- Constructor con dependencias
- Campo activo por defecto verdadero

---

### 🟦 **HU-006 — Crear POJO Empleado**

**Descripción:**  
Implementar datos personales y laborales del empleado.

**Criterios de aceptación:**

- DNI obligatorio
- Referencia a puesto y categoría real
- Fechas con `LocalDate`
- Clase compila

---

### 🟦 **HU-007 — Inicializar colecciones internas**

**Descripción:**  
Donde haya `List<>`, inicializar en el constructor vacío (ej: Sede).

---

### 🟦 **HU-008 — Implementar Serializable en todas las clases**

**Descripción:**  
Agregar `implements Serializable` y `serialVersionUID`.

---

# 📝 5. **Definition of Done del Sprint 2**

✔ Todas las clases creadas y compilando  
✔ Paquetes correctamente organizados  
✔ Atributos privados y accesibles mediante getters/setters  
✔ Uso correcto de composición  
✔ No hay duplicación de código innecesaria  
✔ serialVersionUID incluido en cada clase  
✔ Proyecto subido a GitHub en ramas feature  
✔ Pull Requests revisados por el integrador  
✔ Tarjetas Trello movidas a **Done**

---

# 📘 6. **Notas para el alumnado**

- Este Sprint se centra solo en **crear la estructura básica del modelo**.
- Todavía no se implementa lógica ni comportamiento.
- Todavía no se crea herencia ni equals/hashCode.
- El integrador debe validar que las clases coinciden con el dominio definido en Sprint 1.

---

# 🎯 ¿Quieres que genere ahora el **SPRINT 2.5 (Herencia)** del mismo estilo?

Puedo generarlo igual de detallado, con tarjetas Trello, criterios de aceptación y ejemplos.