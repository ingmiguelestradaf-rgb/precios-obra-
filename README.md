# Precios de Obra MX

Buscador de precios de materiales de construcción en México y proveedores internacionales certificados. `precios.json` se actualiza a diario.

## Mano de obra y precio unitario (pestaña "Mano de obra y P.U.")

`mano-obra.json` complementa `precios.json` para armar análisis de precios unitarios (APU) en Tijuana:

- **categorias**: salario diario de referencia por oficio (rango de mercado y mínimo legal ZLFN 2026). En la app cada salario se puede cambiar y se guarda en el equipo.
- **fsr**: parámetros del Factor de Salario Real: aguinaldo, vacaciones, festivos LFT, días de costumbre y clima, cuotas IMSS 2026 (con la tabla CEAV por rango de UMA), Infonavit 5 % e ISN de B.C. 4.25 %.
  - `Tp = 365 + aguinaldo + vacaciones × prima`; `Tl = 365 − domingos − vacaciones − festivos − costumbre − clima`
  - `SBC = SD × Tp / 365`; `Ps = (cuotas patronales anuales + ISN) / (SD × Tp)`; `FSR = Tp / Tl × (1 + Ps)`
- **cuadrillas**: composición de cada cuadrilla.
- **rendimientos**: 27 conceptos con rango de rendimiento por jornada, cuadrilla, consumo de materiales (ligado a los `_id` de `precios.json`) y equipo.
- **equipo**: renta de equipo menor y maquinaria.
- **factor_regional**: ajuste de los precios nacionales a Tijuana (10 % por omisión).

La misma lógica está en Python en el repo [VERTICE-CALCULO](https://github.com/ingmiguelestradaf-rgb/VERTICE-CALCULO) (`vertice.costos`), que lee estos dos archivos para presupuestos completos.

Los salarios de mercado, rendimientos y rentas son referencias iniciales: calíbralos con tus listas de raya, tus datos de obra y cotizaciones.
