# Mejora de Algoritmo Genético para MSA

Este proyecto presenta una versión mejorada de un Algoritmo Genético (AG) para resolver el problema de Alineamiento Múltiple de Secuencias (MSA), basado en el material del curso [Nombre de tu Materia/Curso].

## Video Demostrativo y Explicación

Aquí puedes ver un video que explica el código, la mejora implementada y demuestra la comparativa de resultados:

**➡️ [https://drive.google.com/file/d/1zngeHp6bi3wG67_zQBT1k85WVs2WbJQ1/view?usp=sharing]**

---

## Explicación de la Mejora

El algoritmo original (`AG10 (1).py`) utilizaba una estrategia de mutación única con una probabilidad muy alta (80%) de insertar un gap aleatorio. Esto generaba un comportamiento caótico (pura **exploración**) que impedía al algoritmo converger, destruyendo las buenas soluciones encontradas por la cruza.

La **mejora** implementada en el notebook (`comparacion_ag_paso_a_paso.ipynb`) consiste en reemplazar esa estrategia por un **balance entre exploración y explotación**:

1.  **Exploración (15%):** Se reduce la probabilidad de inserción de gap a un `p=0.15`. Esto permite introducir nueva diversidad de forma controlada, sin destruir las buenas soluciones.
2.  **Explotación (20%):** Se introduce un nuevo operador de "gap shifting" (búsqueda local) con una probabilidad `p_seq=0.2`. Este operador toma un gap existente y lo mueve un espacio a la izquierda o derecha, permitiendo "refinar" o "pulir" las soluciones que ya son buenas.

Como se demuestra en la gráfica generada por el notebook, esta estrategia balanceada alcanza un fitness promedio consistentemente más alto que la original.

## Archivos del Proyecto

* `comparacion_ag_paso_a_paso.ipynb`: El Jupyter Notebook principal. Contiene el código del AG Original, el AG Mejorado, ejecuta la simulación completa y genera la gráfica comparativa.
* `AG10 (1).py`: El script original del algoritmo genético sin modificar.
* `Documento Informativo...pdf`: El PDF con el resumen teórico de la materia.

## Validación de Integridad

Ambos algoritmos (Original y Mejorado) incluyen la función `validar_poblacion_sin_gaps` para asegurar que, después de todas las operaciones de cruza y mutación, las secuencias de aminoácidos (sin gaps) permanecen idénticas a las originales.
