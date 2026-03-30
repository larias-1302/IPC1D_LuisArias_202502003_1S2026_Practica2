# MANUAL TÉCNICO  
## Sistema de Simulación de Algoritmos de Ordenamiento
---

# 1. Descripción general
Este sistema implementa algoritmos de ordenamiento para análisis comparativo de rendimiento:
- Bubble Sort  
- Shell Sort  
- Quick Sort  

Permite medir tiempos de ejecución y visualizar el proceso.

---

# 2. Estructura del proyecto
- Main.java
- models
- sorting
  - BubbleSort.java
  - ShellSort.java
  - QuickSort.java
- utils
  - FileReader.java
- reports
- ReportGenerator.java
---

# 3. Librerías utilizadas

- `java.util.Scanner` → entrada de datos  
- `java.io.*` → manejo de archivos  
- `java.util.Arrays` → manipulación de arreglos  
- `java.time.*` → medición de tiempo  

---

# 4. Lógica del sistema

El flujo general del sistema es:

1. Carga de datos (manual o archivo TXT)  
2. Selección del algoritmo  
3. Ejecución del ordenamiento  
4. Medición de rendimiento  
5. Generación de reporte  

---

# 5. Implementación de algoritmos

## Bubble Sort
- Compara elementos adyacentes  
- Intercambia si están en orden incorrecto  
- Complejidad: O(n²)  

---

## Shell Sort
- Mejora del Insertion Sort  
- Utiliza incrementos (gap)  
- Reduce número de comparaciones  

---

## Quick Sort
- Algoritmo divide y vencerás  
- Selecciona un pivote  
- Divide en subarreglos recursivamente  

---

# 6. Medición de rendimiento

El sistema mide:

- Tiempo de ejecución (ns)  
- Número de comparaciones  
- Número de intercambios  

Ejemplo:
- Tiempo: 12000 ns
- Comparaciones: 25
- Intercambios: 10

---

# 7. Manejo de archivos TXT

El sistema permite cargar datos desde archivos `.txt`.

Formato esperado: 5 3 8 1 2


Cada número debe estar separado por espacios.

---

# 8. Observaciones técnicas

- Sistema modular y escalable  
- Cada algoritmo está en una clase independiente  
- Uso de programación orientada a objetos  
- Fácil incorporación de nuevos algoritmos  

---

# 9. Conclusión técnica

El sistema permite comparar algoritmos de ordenamiento de forma visual y cuantitativa, facilitando el análisis de eficiencia.
