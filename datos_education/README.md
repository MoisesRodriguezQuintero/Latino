# dataframe_education v1.0

Librería para el lenguaje de programación [Latino](https://lenguajelatino.org/) que implementa una estructura de tabla (DataFrame) inspirada en herramientas como pandas. Diseñada con fines educativos para aprender a manejar datos tabulares en Latino.

---

## Instalación

Copia el archivo `datos.lat` en tu proyecto. Se recomienda la siguiente estructura:

```
mi_proyecto/
├── src/
│   └── mi_script.lat
└── libs/
    └── datos.lat
```

---

## Importación

Usa `incluir()` asignándolo a una variable para acceder a las funciones de la librería:

```latino
datos = incluir("src/datos")
```

Ajusta la ruta según la ubicación de tu archivo respecto a `datos.lat`.

---

## Funciones

### `crear(columnas)`
Crea un nuevo DataFrame vacío con las columnas indicadas.

**Parámetros:**
- `columnas` — lista de strings con los nombres de las columnas

**Retorna:** un DataFrame vacío

```latino
df = datos.crear(["nombre", "edad", "pais"])
```

---

### `agregar_fila(df, valores)`
Agrega una fila al DataFrame.

**Parámetros:**
- `df` — el DataFrame al que se agrega la fila
- `valores` — lista de valores en el mismo orden que las columnas

```latino
datos.agregar_fila(df, ["Ana", 25, "Chile"])
datos.agregar_fila(df, ["Luis", 30, "México"])
datos.agregar_fila(df, ["Pedro", 17, "Argentina"])
```

---

### `mostrar(df)`
Imprime el DataFrame en consola en formato de tabla.

**Parámetros:**
- `df` — el DataFrame a mostrar

```latino
datos.mostrar(df)
```

Salida de ejemplo:
```
nombre | edad | pais |
-------------------------------
Ana | 25 | Chile |
Luis | 30 | México |
Pedro | 17 | Argentina |
```

---

### `contar_filas(df)`
Retorna el número de filas del DataFrame.

**Parámetros:**
- `df` — el DataFrame a contar

**Retorna:** número entero

```latino
escribir(datos.contar_filas(df))
```

---

### `filtrar(df, columna, operador, valor)`
Filtra las filas del DataFrame según una condición y retorna un nuevo DataFrame con los resultados.

**Parámetros:**
- `df` — el DataFrame a filtrar
- `columna` — string con el nombre de la columna
- `operador` — string con el operador de comparación: `"="`, `">"`, `"<"`, `">="`, `"<="`, `"!="`
- `valor` — el valor contra el que se compara

**Retorna:** un nuevo DataFrame con las filas que cumplen la condición

```latino
adultos = datos.filtrar(df, "edad", ">", 18)
datos.mostrar(adultos)
```

---

## Ejemplo completo

```latino
datos = incluir("src/datos")

# Crear tabla
df = datos.crear(["nombre", "edad", "pais"])

# Agregar filas
datos.agregar_fila(df, ["Ana", 25, "Chile"])
datos.agregar_fila(df, ["Luis", 30, "México"])
datos.agregar_fila(df, ["Pedro", 17, "Argentina"])

# Mostrar tabla completa
datos.mostrar(df)

# Contar filas
escribir("Total filas:")
escribir(datos.contar_filas(df))

# Filtrar mayores de edad
adultos = datos.filtrar(df, "edad", ">", 18)
escribir("Adultos:")
datos.mostrar(adultos)
```

---

## Operadores disponibles en `filtrar`

| Operador | Descripción       |
|----------|-------------------|
| `=`      | Igual a           |
| `!=`     | Distinto de       |
| `>`      | Mayor que         |
| `<`      | Menor que         |
| `>=`     | Mayor o igual que |
| `<=`     | Menor o igual que |

---

## Limitaciones conocidas

- No soporta valores nulos.
- Los nombres de columnas deben ser strings únicos.
- El orden de los valores en `agregar_fila` debe coincidir exactamente con el orden de las columnas definidas en `crear`.

---

## Versión

**v1.0** — Primera versión estable.