# SPRINT 5 — Aplicación Consola (Servicios + Menús + Serialización)

  
En este Sprint se debe realizar:

  
- Una **capa de servicios** basada en `ArrayList` que **usa `ConsoleSupport`** (del Sprint 4) para pedir datos al usuario.

- Una **capa de menús** (uno por entidad) para navegar y ejecutar operaciones CRUD parcialmente (solo crear listar y buscar).

* Serializar los datos introducidos
  

### 🟦 Plantilla 1: Servicio de **Departamento** (DepartamentoService)

  
Estudiar el código fuente de DepartamentoService y utilizarlo como plantilla para las historias 21 a 24

### 🟦 Plantilla 2: Menú de **Departamento** (DepartamentoMenu)

Estudia el código fuente de Departamento menú y utilizarlo como plantilla para las historias 25 a 28

### 🟦 Clase a completar 1: App.java

Estudia el código fuente de App.java y descomenta los métodos correspondientes conforme evoluciona vuestra aplicación.
**Esta clase es la que debemos ejecutar para probar este Sprint.**

### 🟦 Clase a completar 2: MainMenu.java

Estudia el código fuente de MainMenu.java y descomenta los métodos correspondientes conforme evoluciona vuestra aplicación.

# HISTORIAS DE USUARIO — **Servicios** (HU‑21 → HU‑24)

  
### 🟦 HU‑21 — Servicio de **Sede** (SedeService)
 
**Como desarrollador**, quiero un servicio de sedes, para gestionar sedes reutilizando la lógica de dirección (Ubicación).

 **Criterios de aceptación**
*   `SedeService` usa `ArrayList` para guardar todas las sedes.
*   Las sedes se crean con `SedeConsoleSupport` (reusa `UbicacionConsoleSupport`).

***
### 🟦 HU‑22 — Servicio de **Categoría Laboral** (CategoriaService)
 

**Como desarrollador**, quiero un servicio de categorías laborales, **para** gestionar categorías asignadas a empleados y puestos.

**Criterios de aceptación**
*   `CategoriaService` usa `ArrayList` para guardar todas las categorías.
*   Las categorías se crean con `CategoriaConsoleSupport`.

***
### 🟦 HU‑23 — Servicio de **Puesto de Trabajo** (PuestoService)

**Como desarrollador**, quiero un servicio de puestos, **para** crear puestos que se asignarán a empleados. Al introducir el id del departamento, me revisará si ya existe y en caso de ausencia abortará la creación. Al introducir el id del categoría, me revisará si ya existe y en caso de ausencia abortará la creación.

**Criterios de aceptación**
*   `PuestoService` usa `ArrayList` para guardar todos los puestos.
*    En caso de introducir una departamento no existente abortar. Se valorará crear con `DepartamentoConsoleSupport` en lugar de abortar.
*    En caso de introducir una categoría no existente abortar. Se valorará crear con `CategoriaConsoleSupport` en lugar de abortar.
*   Los puestos se crean con `PuestoTrabajoConsoleSupport`

***
### 🟦 HU‑24 — Servicio de **Empleado** (EmpleadoService)

**Como desarrollador**, quiero un servicio de empleados, **para** gestionar datos personales y laborales. Al introducir los ids de Pueseto y Categoría, se revisará si a existe y en caso de ausencia abortará la creación.

**Criterios de aceptación**
*   `EmpleadoService` usa `ArrayList` para guardar todos los Empleados.
*   Los empleados se crean usando `EmpleadoConsoleSupport` (reusa `PersonaConsoleSupport`).
*    En caso de introducir una puesto no existente abortar. Se valorará crear con `PuestoConsoleSupport` en lugar de abortar.
*    En caso de introducir una categoría no existente abortar. Se valorará crear con `CategoriaConsoleSupport` en lugar de abortar.
*   Comprobar duplicado por **DNI**, ya que esta clase no tiene id.

***

# HISTORIAS DE USUARIO — **Menús** (HU‑25 → HU‑28)

### 🟦 HU‑25 — **Menú de Sede**

**Como usuario**, quiero un menú de Sedes con altas, listados y búsquedas.

**Criterios de aceptación**
*   Permite crear, listas y buscar usando su servicio.
*   `0` vuelve al menú principal.

***
### 🟦 HU‑26 — **Menú de Categoría Laboral**

**Como usuario**, quiero un menú de Categorías con altas, listados y búsquedas.

**Criterios de aceptación**
*   Permite crear, listas y buscar usando su servicio.
*   `0` vuelve al menú principal.

***
### 🟦 HU‑27 — **Menú de Puesto de Trabajo**

**Como usuario**, quiero un menú de Puestos con altas, listados y búsquedas.

**Criterios de aceptación**

*   Permite crear, listas y buscar usando su servicio.
*   `0` vuelve al menú principal.

***
### 🟦 HU‑28 — **Menú de Empleado**

**Como usuario**, quiero un menú de Empleados con altas, listados y búsquedas.

**Criterios de aceptación**

*   Permite crear, listas y buscar usando su servicio.
*   `0` vuelve al menú principal.

***
# OTRAS HISTORIAS DE USUARIO
### 🟦 HU‑29 — **Serialización**

**Como desarrollador**, quiero que cada vez que se inicie la aplicación carge del fichero datos.dat la información procesada en ejecuciones anteriores. Además al terminar el programa deberá actualizar los datos.

**Criterios de aceptación**
*   Los datos introducidos en la ejecución anterior se cargan al iniciar la siguiente
*   Todo el código debe incluirse en `App.java`

***