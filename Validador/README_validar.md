# validar v1.0

Librería para el lenguaje de programación [Latino](https://lenguajelatino.org/) que proporciona funciones de validación de cadenas usando expresiones regulares. Útil para verificar formatos de datos antes de procesarlos.

---

## Instalación

Copia el archivo `validar.lat` en tu proyecto:

```
mi_proyecto/
├── src/
│   └── validar.lat
└── ejemplos/
    └── mi_script.lat
```

---

## Importación

```latino
v = incluir("src/validar")
```

---

## Funciones

### `email(texto)`
Valida si el texto tiene formato de correo electrónico.

```latino
escribir(v.email("usuario@ejemplo.com"))   # verdadero
escribir(v.email("esto no es un email"))   # falso
```

---

### `telefono(texto)`
Valida si el texto es un número de teléfono local (7-15 dígitos) o internacional (con `+`).

```latino
escribir(v.telefono("+34612345678"))   # verdadero
escribir(v.telefono("6123456"))        # verdadero
escribir(v.telefono("abc"))            # falso
```

---

### `url(texto)`
Valida si el texto es una URL con protocolo `http` o `https`.

```latino
escribir(v.url("https://lenguajelatino.org"))   # verdadero
escribir(v.url("lenguajelatino.org"))            # falso
```

---

### `fecha(texto)`
Valida si el texto tiene formato de fecha `DD/MM/AAAA`.

```latino
escribir(v.fecha("14/04/2026"))   # verdadero
escribir(v.fecha("2026-04-14"))   # falso
```

---

### `es_entero(texto)`
Valida si el texto representa un número entero (solo dígitos).

```latino
escribir(v.es_entero("42"))     # verdadero
escribir(v.es_entero("3.14"))   # falso
escribir(v.es_entero("abc"))    # falso
```

---

### `es_decimal(texto)`
Valida si el texto representa un número decimal con punto.

```latino
escribir(v.es_decimal("3.14"))   # verdadero
escribir(v.es_decimal("42"))     # falso
```

---

### `codigo_postal(texto)`
Valida si el texto es un código postal de 4 o 5 dígitos.

```latino
escribir(v.codigo_postal("28001"))   # verdadero
escribir(v.codigo_postal("1234"))    # verdadero
escribir(v.codigo_postal("123"))     # falso
```

---

### `solo_letras(texto)`
Valida si el texto contiene únicamente letras y espacios (incluye acentos y ñ).

```latino
escribir(v.solo_letras("Juan García"))   # verdadero
escribir(v.solo_letras("Juan123"))       # falso
```

---

### `vacia(texto)`
Valida si el texto está vacío o contiene solo espacios.

```latino
escribir(v.vacia(""))        # verdadero
escribir(v.vacia("   "))     # verdadero
escribir(v.vacia("hola"))    # falso
```

---

## Ejemplo completo

```latino
v = incluir("src/validar")

nombre = "Ana López"
correo = "ana@ejemplo.com"
telefono = "+34612345678"
web = "https://mipagina.com"
nacimiento = "14/04/2026"
cp = "28001"

si v.solo_letras(nombre)
    escribir("Nombre válido: " .. nombre)
sino
    escribir("Nombre inválido")
fin

si v.email(correo)
    escribir("Correo válido: " .. correo)
sino
    escribir("Correo inválido")
fin

si v.telefono(telefono)
    escribir("Teléfono válido: " .. telefono)
sino
    escribir("Teléfono inválido")
fin

si v.url(web)
    escribir("URL válida: " .. web)
sino
    escribir("URL inválida")
fin

si v.fecha(nacimiento)
    escribir("Fecha válida: " .. nacimiento)
sino
    escribir("Fecha inválida")
fin

si v.codigo_postal(cp)
    escribir("Código postal válido: " .. cp)
sino
    escribir("Código postal inválido")
fin
```

Salida esperada:
```
Nombre válido: Ana López
Correo válido: ana@ejemplo.com
Teléfono válido: +34612345678
URL válida: https://mipagina.com
Fecha válida: 14/04/2026
Código postal válido: 28001
```

---

## Limitaciones conocidas

- `fecha` solo valida el formato `DD/MM/AAAA`, no comprueba si la fecha es lógicamente válida (por ejemplo, `31/02/2026` pasaría la validación).
- `telefono` no valida prefijos de país específicos, solo el formato general.
- `solo_letras` permite espacios, útil para nombres completos.

---

## Versión

**v1.0** — Primera versión estable.
