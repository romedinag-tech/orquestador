# Orquestador — tablero de coordinación

Tablero **en vivo** de cómo avanzan los motores de `Análisis RMG`: qué encargo tiene abierto cada
dominio, con quién, hace cuántos días, qué se despachó hoy y qué se cerró.

- **[index.html](index.html)** es el tablero. Se regenera y se sube desde `_orquestador/publica.py`.
- `version.json` dice cuándo se generó, cuántos encargos hay abiertos y cuántos eventos lleva el libro.

## Qué es lo que está mirando

Cada proyecto del repositorio es un **motor** con su propio dato, y ninguno puede editar los archivos
de otro. La coordinación pasa por un libro compartido de **sólo añadir** (`estado.jsonl`): un encargo
lo abre quien pregunta, el dueño responde midiendo en su propio dato, y **cierra quien pidió**,
después de volver a medir. Lo que viaja entre motores es **evidencia con su cifra**, nunca un
veredicto: quien recibe un hallazgo lo vuelve a medir antes de corregir nada.

El tablero no publica microdato: sólo asuntos, estados, cifras agregadas y tiempos.
