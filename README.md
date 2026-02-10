# Graficacion

INSTALAR BLENDER PORTABLE

Paso 1 — Ir a la página oficial
Entra a la página oficial:
 https://www.blender.org
 
<img width="936" height="464" alt="Captura de pantalla 2026-02-10 121734" src="https://github.com/user-attachments/assets/7b4dcd64-cdb9-4d90-83df-60c2377852dd" />

 Paso 2 - Haz clic en Download Blender.

 Paso 3 -  Baja un poco y busca: Other versions

 <img width="950" height="472" alt="image" src="https://github.com/user-attachments/assets/7b4cd844-4726-4a1e-8680-a5a4bde9a1b9" />

 Paso 4 -  Elige Windows – Portable (.zip)

<img width="950" height="462" alt="image" src="https://github.com/user-attachments/assets/b37c922d-aa22-4a13-98ce-1e26ba1ee83d" />

Paso 5 -  Clic derecho al .zip

Paso 6 - Extract All / Extraer todo

Paso 7 - Se crea una carpeta con Blender completo dentro.

Paso 8 - Entra y verás blender.exe

Ese archivo ya es Blender, sin instalar nada.
Doble clic en blender.exe.
Si abre el cubo, listo.

<img width="960" height="562" alt="image" src="https://github.com/user-attachments/assets/15717644-fb78-4fd7-ba0b-b17ac3d5f141" />

HAORA VAMOS A CREAR UN POLIGONO

Este código en Python para Blender crea automáticamente un polígono regular en 2D

Librerías que usa

```bash
import bpy
import math

bpy: permite controlar Blender con Python.
math: se usa para hacer cálculos con seno, coseno y π (pi).

La función principal

 def crear_poligono_2d(nombre, lados, radio):
Esta función necesita 3 datos:

nombre: cómo se llamará el objeto en Blender.
lados: cuántos lados tendrá el polígono.
radio: la distancia del centro a los vértices.
Crear la malla y el objeto

malla = bpy.data.meshes.new(nombre)
objeto = bpy.data.objects.new(nombre, malla)
bpy.context.collection.objects.link(objeto)

Aquí se crea:
Una malla vacía.
Un objeto que usa esa malla.
Se agrega el objeto a la escena.

Calcular los vértices del polígono

vertices = []
for i in range(lados):
    angulo = 2 * math.pi * i / lados
    x = radio * math.cos(angulo)
    y = radio * math.sin(angulo)
    vertices.append((x, y, 0))

Qué pasa aquí : 
Se calcula la posición de cada vértice.

Conectar los vértices (aristas)


aristas = []
for i in range(lados):
    aristas.append((i, (i + 1) % lados))

Une cada punto con el siguiente.

El % lados hace que el último punto se conecte con el primero y cierre la figura.

Pasar los datos a la malla

malla.from_pydata(vertices, aristas, [])
malla.update()

Se cargan los vértices y las líneas en Blender.

Limpiar la escena

bpy.ops.object.select_all(action='SELECT')
bpy.ops.object.delete()

Borra todo lo que había antes para que solo se vea el polígono.

jecutar la función
crear_poligono_2d("Poligono2D", lados=6, radio=5)

Crea un hexágono con radio 5.
