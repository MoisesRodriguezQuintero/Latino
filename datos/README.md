# datos

Mini librería **DataFrame** para el lenguaje **Latino**.

`datos` permite trabajar con información tabular de forma sencilla usando listas y diccionarios.
Está pensada como una herramienta ligera para **educación, scripts y manipulación básica de datos**.

Versión actual: **0.1**

---

# Características

* Crear tablas de datos
* Agregar filas
* Mostrar datos en consola
* Filtrar registros
* Contar filas

La librería está inspirada en los **DataFrame**, pero diseñada para ser **simple y fácil de aprender**.

---

# Instalación

Coloca el archivo `datos.lat` en tu proyecto o en tu carpeta de librerías.

Luego inclúyelo en tu script:

```
datos = incluir("datos")
```

---

# Ejemplo rápido

```
datos = incluir("datos")

df = datos.crear(["nombre","edad","pais"])

datos.agregar(df, ["Ana",25,"Chile"])
datos.agregar(df, ["Luis",30,"México"])
datos.agregar(df, ["Pedro",17,"Argentina"])

datos.mostrar(df)

adultos = datos.filtrar(df, "edad", ">", 18)

escribir("")
escribir("Adultos:")

datos.mostrar(adultos)
```

Salida aproximada:

```
nombre | edad | pais |
---------------------
Ana | 25 | Chile |
Luis | 30 | México |
Pedro | 17 | Argentina |
```

---

# API

## crear()

Crea una nueva tabla.

```
df = datos.crear(["columna1","columna2"])
```

---

## agregar()

Agrega una fila a la tabla.

```
datos.agregar(df, ["valor1","valor2"])
```

---

## contar()

Devuelve el número de filas.

```
total = datos.contar(df)
```

---

## mostrar()

Imprime la tabla en consola.

```
datos.mostrar(df)
```

---

## filtrar()

Filtra registros según una condición.

Operadores soportados:

```
=
!=
>
<
>=
<=
```

Ejemplo:

```
adultos = datos.filtrar(df, "edad", ">", 18)
```

---

# Estructura interna

Un DataFrame en `datos` es un diccionario con dos propiedades:

```
{
    "columnas": lista,
    "filas": lista
}
```

Cada fila se almacena como un diccionario.

Ejemplo:

```
{
    columnas = ["nombre","edad"],
    filas = [
        {"nombre":"Ana","edad":25},
        {"nombre":"Luis","edad":30}
    ]
}
```

---

# Roadmap

Próximas funciones planeadas:

* ordenar()
* promedio()
* maximo()
* minimo()
* cargar_csv()
* guardar_csv()

---

# Objetivo

`datos` busca ofrecer una forma **simple y accesible de trabajar con datos tabulares en Latino**, especialmente para:

* aprendizaje
* automatización
* scripts de datos simples

---

# Licencia

MIT
