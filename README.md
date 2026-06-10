[README.md](https://github.com/user-attachments/files/28797198/README.md)
# Test de hipótesis: play-delay de Netflix

Trabajo práctico de **Inferencia Estadística** que reproduce, de forma simplificada, el proceso de control de calidad que usa Netflix para decidir si una actualización de su plataforma empeora el *play-delay* (el tiempo entre que el usuario presiona "play" y el inicio de la reproducción).

## El problema

Una nueva versión de la plataforma se despliega a un grupo de prueba de 200 usuarios. A partir de datos históricos de la versión anterior, queremos decidir si la actualización **aumenta** el play-delay, controlando la probabilidad de falsos positivos (mandar a auditar un cambio que en realidad no empeora nada).

## Qué hicimos

- **Análisis exploratorio**: media y varianza de los datos históricos, histograma de densidad con la curva normal superpuesta.
- **Test de hipótesis unilateral** (H₀: μ ≤ μ₀ vs. H₁: μ > μ₀) con estadístico Z y varianza conocida, a nivel α = 0.05.
- **Análisis de sensibilidad**: cómo cambia la decisión al variar el nivel de significancia, y búsqueda del menor α que rechaza H₀.
- **p-valor por dos caminos**: como menor nivel de rechazo (grilla fina de α) y como probabilidad de observar un estadístico tan o más extremo — y verificación de que coinciden.
- **Simulación de Monte Carlo** (10.000 réplicas bajo H₀) para comprobar empíricamente que la tasa de error de tipo I es ≈ α.
- **Test de normalidad de Shapiro–Wilk** para validar el supuesto de normalidad de ambas muestras.

**Conclusión**: con los datos del grupo de prueba no se rechaza H₀ a nivel 0.05 (p-valor ≈ 0.058): no hay evidencia suficiente de que la nueva versión aumente el play-delay.

## Archivos

| Archivo | Descripción |
|---|---|
| `TP4-Inferencia.qmd` | Análisis completo en Quarto (R) |
| `datos_historicos_.csv` | Play-delays de la versión anterior |
| `datos_nuevos_.csv` | Play-delays de los 200 usuarios de prueba |

## Cómo ejecutarlo

Con R y [Quarto](https://quarto.org/) instalados:

```bash
quarto render TP4-Inferencia.qmd
```

Se genera un HTML con el análisis, los gráficos y las conclusiones.

## Autoras

Jacinta Matas Terranova · Martina Monastra · Maria Yunes Marangoni
