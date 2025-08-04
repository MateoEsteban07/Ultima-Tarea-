# Ultima-Tarea-
# Simulación de Flujo de Trabajo Colaborativo con 4 Personas

Este repositorio demuestra un flujo de trabajo con Git para un equipo de 4 desarrolladores simulados (`dev1`, `dev2`, `dev3`, `dev4`), gestionado por `MateoEsteban07`. El objetivo es mostrar cómo se manejan tanto las fusiones limpias como la resolución de conflictos complejos.

## Flujo de Trabajo Seguido

1.  **Inicialización:** Se creó un archivo `equipo.txt` con tareas asignadas a cada desarrollador en la rama `main`.
2.  **Trabajo en Paralelo :**
    *   `dev1` y `dev2` crearon sus ramas (`rama-dev1`, `rama-dev2`) desde `main`.
    *   Cada uno modificó su línea asignada y subió su rama.
    *   Estas dos ramas se fusionaron en `main` sin ningún problema, ya que los cambios eran en líneas diferentes.
3.  **Trabajo en Paralelo (Con Conflicto):**
    *   `dev3` y `dev4` también crearon sus ramas (`rama-dev3`, `rama-dev4`) desde el `main` original.
    *   Ambos modificaron la **misma línea** (`Línea 3`), preparando el escenario para un conflicto.
4.  **Fusión y Resolución de Conflictos:**
    *   Se fusionó primero la rama `rama-dev3` en `main`.
    *   Al intentar fusionar `rama-dev4`, Git detectó un conflicto, ya que la `Línea 3` en `main` (modificada por `dev3`) era diferente a la de `rama-dev4`.
5.  **Resolución Colaborativa:** Se resolvió el conflicto editando manualmente el archivo para integrar las contribuciones de `dev3` y `dev4` en una sola línea coherente. El merge se completó con un commit de resolución.

## Evidencia del Conflicto y Resolución

El conflicto principal ocurrió al intentar ejecutar `git merge rama-dev4` después de que `rama-dev3` ya había sido integrada en `main`.

### 1. Estado del archivo `equipo.txt` con el conflicto:

Git mostró las dos versiones en conflicto de la `Línea 3`: la que venía de `main` (que ya incluía el cambio de `dev3`) y la que venía de `rama-dev4`.

```diff
Línea 1: Tarea de dev1 completada exitosamente.
Línea 2: Tarea de dev2 finalizada.
<<<<<<< HEAD
Línea 3: Aporte de dev3.
=======
Línea 3: Cambio de dev4.
>>>>>>> rama-dev4
Línea 4: Tarea para dev4
```

### 2. Resolución Aplicada:

Se decidió que ambos aportes eran valiosos. Se combinaron en una nueva línea y se completó la tarea de la línea 4.

```text
Línea 1: Tarea de dev1 completada exitosamente.
Línea 2: Tarea de dev2 finalizada.
Línea 3: Aporte de dev3 y cambio de dev4 integrados.
Línea 4: Tarea para dev4 completada por el líder de equipo.
```

### 3. Commit de Resolución:

El conflicto se marcó como resuelto con los siguientes comandos, unificando el trabajo de todo el equipo:

```bash
git add equipo.txt
git commit -m "fix: Resuelve conflicto entre rama-dev3 y rama-dev4"
```
