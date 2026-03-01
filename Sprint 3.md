### **SPRINT 3 — Implementación de Herencia y Refactorización**

**Estado:** Pendiente  
**Responsables:** Equipo de desarrollo (alumnado)  
**Objetivo:** Implementar la herencia en las clases del dominio y refactorizar las clases existentes para aprovechar la herencia.

---

# 🎯 **Objetivo general del Sprint**

Implementar la herencia en las clases del dominio para mejorar el diseño y reutilizar código. Refactorizar las clases existentes para que hereden de clases base.

---

# 📚 1. **Entidades a implementar en este Sprint**

Los alumnos deben implementar la herencia en las siguientes clases:

1. `Persona` → `Empleado`
2. `Ubicacion` → `Sede`
3. `BaseEntity` → Todas las entidades con ID

➡ Todas estas clases deben estar en un paquete apropiado, por ejemplo:  
`com.miempresa.modelo`

---

# 🧱 2. **Requisitos técnicos obligatorios**

Cada clase debe cumplir con los siguientes requisitos:

### ✔ Clase `Persona`

- Atributos comunes:
  - `nombre`: `String`
  - `apellidos`: `String`
  - `dni`: `String`
- Constructor vacío y completo.
- Getters y setters para todos los campos.

### ✔ Clase `Empleado` (hereda de `Persona`)

- Atributos adicionales:
  - `puestoActual`: `PuestoTrabajo`
  - `categoriaReal`: `CategoriaLaboral`
  - `emailCorporativo`: `String`
  - `fechaAlta`: `LocalDate`
  - `fechaBaja`: `LocalDate`
  - `estadoLaboral`: `String`
- Constructor vacío y completo.
- Getters y setters para todos los campos.
- Sobrescribir métodos si es necesario.

### ✔ Clase `Ubicacion`

- Atributos comunes:
  - `calle`: `String`
  - `numero`: `String`
  - `cp`: `String`
  - `ciudad`: `String`
  - `provincia`: `String`
- Constructor vacío y completo.
- Getters y setters para todos los campos.

### ✔ Clase `Sede` (hereda de `Ubicacion`)

- Atributos adicionales:
  - `id`: `long`
  - `empresaId`: `long`
  - `tipo`: `String`
  - `emailContacto`: `String`
- Constructor vacío y completo.
- Getters y setters para todos los campos.
- Sobrescribir métodos si es necesario.

### ✔ Clase `BaseEntity`

- Atributos comunes:
  - `id`: `long`
- Constructor vacío y completo.
- Getters y setters para todos los campos.

### ✔ Todas las entidades con ID deben heredar de `BaseEntity`

- Asegurar que todas las entidades que tienen un ID heredan de `BaseEntity`.

---

# 🧭 4. **Tareas del Sprint (para Trello)**

Copia y pega estas tarjetas directamente:

---

### 🟦 **HU-007 — Implementar clase Persona**

**Descripción:**  
Implementar la clase `Persona` con atributos comunes.

**Criterios de aceptación:**

- Atributos privados: `nombre`, `apellidos`, `dni`
- Constructor vacío y completo
- Getters y setters para todos los campos
- Clase compila sin errores

---

### 🟦 **HU-008 — Implementar clase Empleado (hereda de Persona)**

**Descripción:**  
Implementar la clase `Empleado` heredando de `Persona`.

**Criterios de aceptación:**

- Atributos adicionales: `puestoActual`, `categoriaReal`, `emailCorporativo`, `fechaAlta`, `fechaBaja`, `estadoLaboral`
- Constructor vacío y completo
- Getters y setters para todos los campos
- Sobrescribir métodos si es necesario
- Clase compila sin errores

---

### 🟦 **HU-009 — Implementar clase Ubicacion**

**Descripción:**  
Implementar la clase `Ubicacion` con atributos de dirección.

**Criterios de aceptación:**

- Atributos privados: `calle`, `numero`, `cp`, `ciudad`, `provincia`
- Constructor vacío y completo
- Getters y setters para todos los campos
- Clase compila sin errores

---

### 🟦 **HU-010 — Implementar clase Sede (hereda de Ubicacion)**

**Descripción:**  
Implementar la clase `Sede` heredando de `Ubicacion`.

**Criterios de aceptación:**

- Atributos adicionales: `id`, `empresaId`, `tipo`, `emailContacto`
- Constructor vacío y completo
- Getters y setters para todos los campos
- Sobrescribir métodos si es necesario
- Clase compila sin errores

---

### 🟦 **HU-011 — Implementar clase BaseEntity**

**Descripción:**  
Implementar la clase `BaseEntity` con atributo ID.

**Criterios de aceptación:**

- Atributo privado: `id`
- Constructor vacío y completo
- Getters y setters para todos los campos
- Clase compila sin errores

---

### 🟦 **HU-012 — Heredar BaseEntity en todas las entidades con ID**

**Descripción:**  
Hacer que todas las entidades con ID hereden de `BaseEntity`.

**Criterios de aceptación:**

- Todas las entidades con ID deben heredar de `BaseEntity`
- Constructor vacío y completo
- Getters y setters para todos los campos
- Clase compila sin errores

---

# 📝 5. **Definition of Done del Sprint 3**

✔ Todas las clases creadas y compilando  
✔ Herencia implementada correctamente  
✔ Atributos privados y accesibles mediante getters/setters  
✔ Uso correcto de la herencia  
✔ No hay duplicación de código innecesaria  
✔ Proyecto subido a GitHub en ramas feature  
✔ Pull Requests revisados por el integrador  
✔ Tarjetas Trello movidas a **Done**

---

# 📚 6. **Notas para el alumnado**

- Este Sprint se centra en **implementar la herencia** en las clases del dominio.
- Asegúrate de que las clases heredan correctamente y reutilizan código.
- El integrador debe validar que las clases coinciden con el diseño definido en el Sprint 1 y 2.
- No se implementa lógica ni comportamiento específico en este Sprint.
