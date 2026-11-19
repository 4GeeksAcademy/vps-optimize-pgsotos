# Optimización de recursos del VPS

Este repositorio registra el uso de memoria y disco del VPS antes y después de los cambios realizados, para facilitar la comparación de ambos estados.

## Archivos

- [`resources-before.txt`](resources-before.txt): salida de `free -h` y `df -h` antes de los cambios.
- [`resources-after.txt`](resources-after.txt): las mismas mediciones después de los cambios.

## Comparación observada

| Métrica | Antes | Después | Variación |
| --- | ---: | ---: | ---: |
| Memoria usada | 172 MiB | 151 MiB | −21 MiB |
| Memoria libre | 191 MiB | 203 MiB | +12 MiB |
| Memoria disponible | 631 MiB | 660 MiB | +29 MiB |
| Espacio usado en `/` | 1.9 GiB | 1.9 GiB | Sin cambio visible |

Las cifras corresponden a capturas puntuales y pueden variar según la carga del sistema. La columna `available` es una referencia más útil que `free` para estimar cuánta memoria puede utilizarse sin recurrir a swap. En ambas mediciones el VPS reportó 957 MiB de RAM y no tenía swap configurada.

## Cómo repetir la medición

Ejecuta estos comandos en el VPS y guarda su salida en los archivos correspondientes:

```sh
free -h
df -h
```

Para comparar los registros:

```sh
diff -u resources-before.txt resources-after.txt
```
