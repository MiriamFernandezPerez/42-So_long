# 🎮 So_long
## *Juego 2D en C*

## 📚 Descripción general
**So_long** es un juego 2D “tile-based” escrito en C donde el jugador debe recoger todos los objetos de un mapa y llegar a la salida para ganar. Utiliza la librería **MiniLibX (MLX)** para renderizado e interacción con el teclado.:contentReference[oaicite:0]{index=0}

---

## 🎯 Objetivos del proyecto
- Implementar un **motor de juego** simple usando MLX.  
- Gestionar dos pilas de sprites (suelo/paredes y entidades) y dibujarlas cada fotograma.  
- Validar mapas `.ber` rectangulares y rodeados de muros.  
- Ofrecer controles fluidos y detección de colisiones.:contentReference[oaicite:1]{index=1}

---

## 🧱 Arquitectura del sistema
| Módulo | Archivo(s) principal(es) | Función |
|--------|--------------------------|---------|
| **Main / Orquestador** | `push_swap.c` | Inicializa datos y lanza el bucle MLX |
| **Entrada & argumentos** | `check_args.c`, `manage_arr.c` | Valida y transforma parámetros |
| **Gestión de pilas** | `manage_stacks.c` | Estructuras `t_stack`, push/pop |
| **Motor de juego** | `sort_stacks.c` | Reglas de actualización y render |
| **Optimización** | `stack_props.c`, `stack_movs.c` | Cálculo de costes de movimiento |
| **Operaciones básicas** | `push.c`, `swap.c`, `rotate.c`, `reverse_rotate.c` | Operaciones permitidas |
| **Utilidades** | `utils.c` | Funciones auxiliares (`ft_atoi`, etc.) |

> Consulta también `inc/so_long.h` para ver todas las estructuras (`t_map`, `t_vars`, `t_item`, `t_tile`).:contentReference[oaicite:2]{index=2}

---

## 🗺️ Formato de mapa `.ber`
Caracteres reconocidos:​:contentReference[oaicite:3]{index=3}  

| Símbolo | Significado | Restricciones |
|---------|-------------|---------------|
| `1` | Muro | Debe encerrar totalmente el mapa |
| `0` | Suelo | Libre |
| `P` | Posición inicial | Exactamente uno |
| `C` | Coleccionable | ≥ 1 |
| `E` | Salida | Exactamente uno |

*El mapa debe ser rectangular y estar delimitado por muros*.

---

## 🎮 Controles de juego
| Tecla | Acción |
|-------|--------|
| **W / ↑** | Mover arriba |
| **A / ←** | Mover izquierda |
| **S / ↓** | Mover abajo |
| **D / →** | Mover derecha |
| **ESC** | Salir del juego |

Cada movimiento:  
1️⃣ Actualiza la posición del jugador  
2️⃣ Comprueba colisiones con muros (`1`)  
3️⃣ Recoge `C` si procede (y actualiza contador)  
4️⃣ Incrementa el número de movimientos  
5️⃣ Redibuja la ventana:contentReference[oaicite:4]{index=4}

---

## 🔧 Compilación
El proyecto usa un **Makefile** que compila tres componentes:  

1. **MLX** (`mlx_linux/`)  
2. **libft** (`my_libft/`)  
3. **so_long** (ejecutable final)

```bash
make        # Compila todo
make clean  # Borra .o y .d
make fclean # clean + elimina binarios/librerías
make re     # fclean seguido de make
```

## 🔧 Compilación

El proyecto se compila usando los siguientes **flags estrictos** para garantizar una buena gestión de errores y depuración:

```bash
-Wall -Wextra -Werror -g -fsanitize=address,leak
```

## 🚀 **Ejecución**

Para lanzar el juego, ejecuta en la terminal:

```bash
./so_long mapas/ejemplo.ber
```
El juego se abrirá en una ventana gráfica utilizando la librería MiniLibX.

# 🕹️ **So_long – Juego con MiniLibX**

---

## 🎯 **Objetivo del Juego**

Recoge **todos los coleccionables (C)** y llega hasta la **salida (E)** para ganar 🏁

---

## 🧩 **Ejemplo de Mapa Mínimo**

11111
1PCE1
11111

🔹 `1` = muro  
🔹 `0` = suelo  
🔹 `P` = posición inicial del jugador  
🔹 `C` = coleccionable  
🔹 `E` = salida

---

## 📌 **Reglas del Mapa**

El mapa debe cumplir con las siguientes condiciones:

- 🧱 Ser **rectangular**
- 🔒 Estar **completamente cerrado por muros** (`1`)
- 🎯 Contener al menos **1 coleccionable (C)**, exactamente **1 jugador (P)** y exactamente **1 salida (E)**

---

## 📎 **Recursos Útiles**

📘 [Guía completa del proyecto (DeepWiki)](#)  
📗 [Documentación oficial de MiniLibX](#)  
📙 [Tutoriales sobre validación de mapas y eventos con MLX](#)

---

## 📝 **Créditos**

💻 Proyecto: **So_long – Escuela 42**  
✍️ Autor original: **Miriam Fernández Pérez**  

---

¡Disfruta programando y… que no te coman los muros! 🧱✨

