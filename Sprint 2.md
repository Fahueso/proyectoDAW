Claro, puedo agregar detalles sobre las composiciones en las historias de usuario para que quede claro cómo se relacionan las clases. Aquí tienes el documento actualizado con las composiciones detalladas en cada historia de usuario.

---

# **SPRINT 2 — Modelado de POJOs del Dominio**

**Estado:** Pendiente  
**Responsables:** Equipo de desarrollo (alumnado)  
**Objetivo:** Implementar las clases básicas del dominio (POJOs), aplicando composición, encapsulación, y las identidades definidas en el Sprint 1. Además, implementar `equals`, `hashCode`, y `toString`.

---

# 🎯 **Objetivo general del Sprint**

Crear todas las clases del dominio (POJOs) con:

- Atributos privados
- Constructores
- Getters y setters
- Identidad clara (campo clave natural o ID)
- Composición entre clases
- Preparación para futura herencia (sin implementarla todavía)
- Implementación de `equals`, `hashCode`, y `toString`

Este Sprint sienta **las bases del modelo de datos** de toda la aplicación.

---

# 📚 1. **Entidades a implementar en este Sprint**

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

### ✔ Campo de identidad (ID o DNI) correctamente definido

### ✔ Implementación de `equals`, `hashCode`, y `toString`

---

# 🧭 4. **Tareas del Sprint (para Trello)**

Copia y pega estas tarjetas directamente:

---

### 🟦 **HU-001 — Crear POJO Empresa**

**Descripción:**  
Implementar la clase `Empresa` con atributos, constructores y getters/setters. Además, implementar `equals`, `hashCode`, y `toString`.

**Criterios de aceptación:**

- Atributos privados: `id`, `razonSocial`, `nombreComercial`, `formaJuridica`, `cif`, `direccionFiscal`, `telefono`, `email`
- Constructor vacío y completo
- Composición NO necesaria
- Clase compila sin errores
- Implementar `equals`, `hashCode`, y `toString` correctamente

---

### 🟦 **HU-002 — Crear POJO Sede**

**Descripción:**  
Implementar clase Sede, incluyendo dirección y medios de contacto. Además, implementar `equals`, `hashCode`, y `toString`.

**Criterios de aceptación:**

- Atributos privados: `id`, `empresaId`, `tipo`, `calle`, `numero`, `cp`, `ciudad`, `provincia`, `emailContacto`
- Lista de teléfonos inicializada
- Atributo `id` obligatorio
- Clase compila sin errores
- Implementar `equals`, `hashCode`, y `toString` correctamente

---

### 🟦 **HU-003 — Crear POJO Departamento**

**Criterios de aceptación:**

- Atributos privados: `id`, `empresaId`, `codigo`, `nombre`, `descripcion`
- ID obligatorio
- Clase simple, sin composición
- Clase compila sin errores
- Implementar `equals`, `hashCode`, y `toString` correctamente

---

### 🟦 **HU-004 — Crear POJO CategoriaLaboral**

**Criterios de aceptación:**

- Identidad por ID
- Campo nivelProfesional opcional
- Clase compila
- Implementar `equals`, `hashCode`, y `toString` correctamente

---

### 🟦 **HU-005 — Crear POJO PuestoTrabajo**

**Descripción:**  
Contiene referencias a Sede, Departamento y CategoriaLaboral. Además, implementar `equals`, `hashCode`, y `toString`.

**Criterios de aceptación:**

- Composición correctamente aplicada:
  - `sede`: `Sede`
  - `departamento`: `Departamento`
  - `categoriaLaboral`: `CategoriaLaboral`
- Constructor con dependencias
- Campo activo por defecto verdadero
- Clase compila sin errores
- Implementar `equals`, `hashCode`, y `toString` correctamente

---

### 🟦 **HU-006 — Crear POJO Empleado**

**Descripción:**  
Implementar datos personales y laborales del empleado. Además, implementar `equals`, `hashCode`, y `toString`.

**Criterios de aceptación:**

- DNI obligatorio
- Referencia a puesto y categoría real:
  - `puestoActual`: `PuestoTrabajo`
  - `categoriaReal`: `CategoriaLaboral`
- Fechas con `LocalDate`
- Clase compila
- Implementar `equals`, `hashCode`, y `toString` correctamente

---

### 🟦 **HU-007 — Inicializar colecciones internas**

**Descripción:**  
Donde haya `List<>`, inicializar en el constructor vacío (ej: Sede).

**Criterios de aceptación:**

- Todas las colecciones internas inicializadas en el constructor vacío
- Clase compila sin errores

---

# 📝 5. **Definition of Done del Sprint 2**

✔ Todas las clases creadas y compilando  
✔ Paquetes correctamente organizados  
✔ Atributos privados y accesibles mediante getters/setters  
✔ Uso correcto de composición  
✔ No hay duplicación de código innecesaria  
✔ `equals`, `hashCode`, y `toString` implementados correctamente en todas las clases  
✔ Proyecto subido a GitHub en ramas feature  
✔ Mezcla realizada por el integrador  
✔ Tarjetas Trello movidas a **Done**

---

# 📚 6. **Notas para el alumnado**

- Este Sprint se centra solo en **crear la estructura básica del modelo**.
- Todavía no se implementa lógica ni comportamiento.
- Todavía no se crea herencia.
- El integrador debe validar que las clases coinciden con el dominio definido en Sprint 1.
- Asegúrate de que todas las clases implementen `equals`, `hashCode`, y `toString` correctamente para evitar problemas futuros con colecciones y depuración.



