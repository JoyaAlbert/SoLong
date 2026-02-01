# **SoLong**

Descripción
-----------
`so_long` es un pequeño juego 2D escrito en C para sistemas Unix/X11. Usa la MiniLibX incluida en la carpeta `mlx/` y otras utilidades del repositorio. El objetivo del juego es mover al jugador por un mapa, recoger todas las coleccionables y alcanzar la salida.

<img width="928" height="566" alt="imagen" src="https://github.com/user-attachments/assets/2c390988-da72-4384-82b1-e89d38126f84" />


Características
---------------
- Juego simple tipo laberinto con sprites y ventana gráfica (MiniLibX).
- Validación básica de mapas (`.ber`) y detección de errores comunes.
- Muestra ejemplos de mapas en la carpeta `0maps/`.

Requisitos
----------
- Linux con servidor X (X11).
- `make`, `gcc` o `clang`.
- Librerías de desarrollo X11 (normalmente ya presentes en sistemas Linux de desarrollo).
- El repositorio incluye una versión de MiniLibX en `mlx/` (no es necesario instalarla por separado).

Compilar
--------
Desde la raíz del proyecto ejecuta:

```bash
make
```

Comandos útiles:

```bash
make clean    # elimina objetos
make fclean   # elimina objetos y binarios
make re       # fclean + make
```

Ejecutar
-------
Uso básico:

```bash
./so_long 0maps/small.ber
```

El programa espera exactamente 1 argumento: la ruta a un archivo de mapa con extensión `.ber`.

Controles
--------
- Mover: `W A S D` o flechas (arriba/izquierda/abajo/derecha).
- Salir: `ESC` o cerrar la ventana.

Formato del mapa (.ber)
-----------------------
El mapa es un archivo de texto con los siguientes caracteres:

- `1` — muro (pared).
- `0` — suelo/espacio vacío.
- `P` — posición inicial del jugador (exactamente 1 requerida).
- `E` — salida/puerta (al menos 1 requerida).
- `C` — coleccionable/moneda (al menos 1 requerida).

Reglas del mapa:

- El mapa debe ser rectangular (todas las líneas misma longitud).
- El mapa debe estar completamente rodeado por `1` (paredes en los bordes).
- Debe contener exactamente 1 `P`, al menos 1 `E` y al menos 1 `C`.
- Solo se permiten los caracteres `10PEC` y el salto de línea.

Ejemplo
-------
Un mapa mínimo válido:

```
11111
1P0C1
1C0E1
11111
```

Carpeta de mapas de ejemplo
---------------------------
Hay varios mapas de prueba en la carpeta `0maps/` que puedes usar para probar el juego.

Errores comunes
---------------
- Pasar un archivo sin la extensión o con formato inválido.
- Mapas no rectangulares o con caracteres no permitidos.
- No incluir `P`, `E` o `C` en las cantidades necesarias.

Estructura relevante del repositorio
-----------------------------------
- `so_long.c`, `map_split.c`, `maps.c`, `matrix.c` — lógica principal y validación de mapas.
- `mlx/` — MiniLibX incluida (implementación de X11 usada para renderizar).
- `0maps/` — mapas de ejemplo.
- `Makefile` — reglas para compilar y limpiar.

Cómo añadir nuevos mapas
------------------------
1. Crea un archivo de texto con extensión `.ber` siguiendo el formato descrito.
2. Colócalo en `0maps/` o pásale la ruta completa al ejecutar `./so_long`.
