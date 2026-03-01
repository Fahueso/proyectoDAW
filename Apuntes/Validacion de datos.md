
# **Validar datos con `String.matches()`**

En este sprint vais a usar **predicados sencillos**. Lo que realmente necesitáis aprender es esto:

> **`String.matches("<expresión_regular>")` devuelve `true` si el texto cumple la regla, y `false` si no.**

---

# 🧠 ¿Qué es una _expresión regular_?

Una expresión regular (regex) es una **regla escrita como un texto**.  
Java puede comprobar si una cadena cumple esa regla con:

siLaCadena.matches("la-regla-aqui")

---

# 🧪 Ejemplos muy útiles para este proyecto

### ✔ DNI: 8 números + 1 letra

s.matches("\d{8}[A-Za-z]")

Desglose:

- `\\d` → un dígito
- `{8}` → ocho veces
- `[A-Za-z]` → una letra (mayúscula o minúscula)

---

### ✔ CIF simple: 8 a 10 caracteres alfanuméricos

s.matches("[A-Za-z0-9]{8,10}")

---

### ✔ Código Postal: exactamente 5 dígitos

s.matches("\d{5}")

---

### ✔ Código Departamento: 2–10 letras mayúsculas o números

s.matches("[A-Z0-9]{2,10}")

---

### ✔ Email básico (que contenga @ y un punto después)


s.contains("@") && s.indexOf('@') < s.lastIndexOf('.')

No es regex, pero es **perfecto** para este sprint.

---

# 🧰 ¿Cómo se usa esto en `InputUtils.readMatching`?

Tu factoría usa algo así, donde in es la instancia de InputUtils

String dni = in.readMatching(

    "DNI",

    new java.util.function.Predicate<String>() {

        @Override

        public boolean test(String s) {

            return s.matches("\d{8}[A-Za-z]");

        }

    },

    "DNI inválido (8 números + letra).",

    true

);

Esto significa:

1. `InputUtils` pregunta por teclado.
2. Envía lo que escribes al `test()` del `Predicate`.
3. `test()` hace `s.matches("...")`.
4. Si devuelve **true**, el dato es válido y sigue.
5. Si devuelve **false**, `InputUtils` muestra el error y vuelve a preguntar (hasta que esté bien).

---

# 🎯 Ejemplos completos que ellos ven claramente

### Ejemplo real en **EmpresaConsoleFactory**:

String cif = in.readMatching(

    "CIF",

    new java.util.function.Predicate<String>() {

        @Override

        public boolean test(String s) {

            return s.matches("[A-Za-z0-9]{8,10}");

        }

    },

    "CIF inválido (8-10 caracteres alfanuméricos).",

    true

);

---

### Ejemplo real en **SedeConsoleFactory**:

String cp = in.readMatching(

    "Código Postal",

    new java.util.function.Predicate<String>() {

        @Override

        public boolean test(String s) {

            return s.matches("\d{5}");

        }

    },

    "El código postal debe tener 5 dígitos.",

    true

);

---

### Ejemplo real en **DepartamentoConsoleFactory**:

String codigoDepto = in.readMatching(

    "Código (2-10 mayúsculas/números)",

    new java.util.function.Predicate<String>() {

        @Override

        public boolean test(String s) {

            return s.matches("[A-Z0-9]{2,10}");

        }

    },

    "Formato inválido. Usa 2-10 mayúsculas/números.",

    true

);

---

### Ejemplo real en **EmpleadoConsoleFactory** (validación de email corporativo):

String email = in.readMatching(

    "Email corporativo",

    new java.util.function.Predicate<String>() {

        @Override

        public boolean test(String s) {

            return s.isEmpty() || (s.contains("@") && s.indexOf('@') < s.lastIndexOf('.'));

        }

    },

    "Email inválido.",

    false

);

---

# 👨‍🏫 Explicación para clase: **¿Por qué `matches` usa `\\d` y no `\d`?**

Porque en Java:

- `\d` dentro de un string se interpreta como código de escape.
- Para que un **true `\d` llegue a `matches`**, hay que escribir **`\\d`**.

Explica siempre así:

- **Primer `\`** → “escapa” dentro del string de Java
- **Segundo `\`** → “llega” al regex real

