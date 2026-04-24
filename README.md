# A/A/B Testing — Validación de Funnel de Compra

> 241K eventos. 7,534 usuarios. Una decisión que salva costos de implementación  
> y revela dónde se pierde el 38% de los usuarios antes de llegar al carrito.

---

## 🎯 Problema de negocio

Una empresa de productos alimenticios evaluaba si cambiar la tipografía de su app móvil mejoraba la conversión. Con 241,298 eventos registrados en 7 días y 3 grupos experimentales balanceados, el reto era doble: determinar si el cambio tenía impacto real y, en paralelo, identificar en qué etapa del embudo se perdían más usuarios.

---

## 🛠️ Herramientas usadas

- Python (Pandas, NumPy, Matplotlib, Seaborn)
- SciPy (z-test de proporciones)
- Estadística inferencial: corrección de Bonferroni

---

## 🔍 Metodología

- Limpieza y preparación de 244,126 eventos: conversión de Unix timestamps, estandarización de columnas y validación de grupos experimentales
- Análisis temporal para detectar datos incompletos y establecer período confiable de 7 días (1-7 agosto 2019)
- Construcción del embudo de conversión con tasas de paso entre cada etapa
- Validación A/A: verificación de que los dos grupos de control son estadísticamente equivalentes antes de comparar con el grupo experimental
- 20 pruebas de hipótesis (z-test de proporciones) con corrección de Bonferroni (α ajustado = 0.0025) para controlar falsos positivos
- Decisión final basada en evidencia estadística con 95% de confianza

---

## 💡 Hallazgo principal

La transición Ofertas → Carrito registra el mayor abandono del embudo con un 38.1% de pérdida de usuarios, mientras que el cambio de tipografía no genera ningún impacto medible (0/5 eventos significativos tras corrección de Bonferroni).

---

## 📊 Impacto o decisión que genera

La empresa evita los costos de implementación del cambio tipográfico al no existir beneficio comprobado, y redirige el foco hacia la etapa crítica del embudo: optimizar la transición Ofertas → Carrito podría elevar la conversión end-to-end de 47.7% a ~54%, un incremento de 6 puntos porcentuales sobre la base actual.

---

## ▶️ Cómo correr el código

```bash
git clone https://github.com/tu-usuario/aab-testing-conversion
cd aab-testing-conversion
pip install -r requirements.txt
jupyter notebook Test_AB_-_Validación_Funnel_de_compra.ipynb
```

**Dataset requerido** (colocar en carpeta `/datasets/`):
- `logs_exp_us.csv`
