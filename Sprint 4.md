# **SPRINT — Factorías por Consola

## ¿Qué vais a hacer en este sprint?

En este sprint vuestra misión es **crear factorías** que construyan los objetos del programa **pidiéndole datos al usuario por consola**, usando únicamente la clase `InputUtils` (que os doy hecha).

En otras palabras:

**El programa va a hablar con vosotros por consola**  
Vosotros le respondéis con datos  
Las factorías crean los objetos del modelo con esa información  
Todo validado, sin permitir datos incorrectos:

- Un DNI debe ser un DNI real.
- Un CP debe tener 5 dígitos.
- Un email debe tener “@”.
- Una Empresa debe tener su `id` y su `cif` correctos.
- Un Empleado debe tener un puesto, una categoría y unos datos personales.

Este sprint os enseña a **controlar la entrada de datos** y a **crear objetos bien construidos**.

En primer lugar debéis estudiar la clase `InputUtils.java` y leer los apuntes de Validación de Datos, que están en este mismo proyecto. Fijaros bien el uso que hace de las excepciones para controlar que los datos sean inconsistentes.
También debéis estudiar el código de `DepartamentoConsoleSupport.java`, como ejemplo a la generación de un departamento.

Todo esto lo encontraréis en las diferentes subcarpetas que acompañan a estos sprints.


---

## 🟦 **HU-10 — Pedir los datos de una Persona correctamente**

**Quiero poder crear personas pidiendo su nombre, apellidos y un DNI válido**,  
porque muchos objetos del sistema dependen de esa información (por ejemplo, un Empleado).

**Lo que harás:**

- Validar el DNI (`12345678A`).
- Repetir la pregunta si está mal.
- Usar un helper llamado `PersonaConsoleSupport`.

---

## 🟦 **HU-11 — Pedir la dirección de forma uniforme**

**Quiero pedir direcciones (calle, número, CP, ciudad y provincia) siempre igual**,  
para no repetir el mismo código mil veces.

**Lo que harás:**

- Validar CP (5 dígitos).
- Repetir hasta que sea correcto.
- Programarlo en un helper llamado `UbicacionConsoleSupport`.

Este helper se usará en Sede y en cualquier cosa futura que herede de Ubicación.

---

## 🟦 **HU-12 — Crear Empresas desde consola**

**Quiero crear empresas completas introduciendo sus datos**,  
porque son la base del flujo del programa.

**Lo que harás:**

- Pedir `id` y `cif`.
- Validar el email.
- Programarlo en un helper llamado `EmpresaConsoleSupport`

---

## 🟦 **HU-13 — Crear Sedes reutilizando la herencia**

**Quiero crear sedes con dirección, pero sin repetir la lógica de pedir calle, número, CP…**,  
porque eso ya lo hace `UbicacionConsoleSupport`.

**Lo que harás:**

- Reusar el helper de Ubicación.
- Pedir solo lo que es exclusivo de Sede: `empresaId`, `tipo`, `emailContacto`.
- Programarlo en un helper llamado `SedeConsoleSupport`

---


## 🟦 **HU-14 — Crear Categorías Laborales**

**Quiero crear categorías laborales**,  
porque luego van asociadas a empleados y puestos.

**Lo que harás:**

- Pedir `id` y `nombre`.
- `nivelProfesional` puede quedar vacío.
- Programarlo en un helper llamado `CategoriaConsoleSupport`

---

## 🟦 **HU-15 — Crear Puestos de Trabajo con sus dependencias**

**Quiero crear puestos de trabajo sin preocuparme de si ya tengo sede, departamento o categoría**, porque si faltan, la factoría los solicitará automáticamente.

**Lo que harás:**

- Pedir `id`, `nombre` y si está activo (ENTER = “sí”).
- Si no recibes Sede, Departamento o Categoría → los creas aquí mismo usando sus factorías.
- Programarlo en un helper llamado `PuestoTrabajoConsoleSupport`

---

## 🟦 **HU-16 — Crear Empleados usando herencia y composición**

**Quiero crear empleados pidiendo solo sus datos propios**,  
porque lo de Persona (DNI, nombre, apellidos) ya está resuelto en un helper.

**Lo que harás:**

- Reusar `PersonaConsoleSupport`.
- Pedir email corporativo, estado laboral, fecha de alta y baja.
- Si faltan puesto o categoría real → los creas con sus factorías.
- Programarlo en un helper llamado `EmpleadoConsoleSupport`

---

## 🟩 **HU-17 — Probar todo en una App**

**Quiero una aplicación principal que cree todos los objetos uno detrás de otro**,  
para comprobar que todo funciona.

**Lo que harás:**

- Inicializar el objeto `InputUtils` con un `Scanner`.

- Crearás con las factorías correspondientes por lo menos una secuencia de este tipo:  
    **Empresa → Sede → Departamento → Categoría → Puesto → Empleado**

