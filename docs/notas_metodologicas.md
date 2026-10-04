# Notas metodológicas

## Procedencia y estado

El único archivo recibido fue el notebook académico S7 de ConnectaTel. Los datos tabulares individuales no se recibieron. Las cifras y gráficos históricos proceden de sus salidas guardadas; no se reconstruyeron ni fabricaron los 4000 clientes o 40000 eventos. Las celdas revisadas tienen contador vacío y no contienen salidas históricas reutilizadas como si fueran nuevas.

## Reglas de segmentación

Las condiciones se evalúan en este orden:

| Condición | Etiqueta |
|---|---|
| Métricas de uso ausentes | Sin actividad observada |
| Llamadas <5 y mensajes <5 | Bajo |
| Llamadas <10 y mensajes <10, sin cumplir Bajo | Medio |
| Resto de perfiles completos | Alto |

Estas reglas provienen del ejercicio, no de una optimización comercial. La revisión cambia 50/200 del código original por 5/10, recupera la condición de mensajes para el nivel medio y evita clasificar nulos como Alto. No es posible calcular cuántos clientes quedan en cada nuevo segmento con los resúmenes disponibles.

## Limpieza y tiempo

- Reemplazar edad -999 por mediana de edades disponibles y conservar indicador de imputación. Las edades imputadas se distinguen en los segmentos para no aparentar información observada.
- Reemplazar `?` y ciudades vacías por categoría Sin dato.
- Marcar como desconocidas las altas posteriores al corte de 2024. Conservar la bandera permite revisarlas posteriormente.
- Excluir fechas de evento nulas o fuera de 2024 de la agregación temporal. El original reportaba 50 eventos sin fecha; no se presupone que fueran consumo cero.
- Revisar coherencia entre alta, baja y actividad antes de atribuir diferencias a comportamientos reales. La revisión no certifica esa coherencia.

## Agregación y nulos

La mayoría de nulos en duration y length dependen del tipo de evento, lo que es compatible con campos no aplicables. Esto no demuestra formalmente MAR. Las salidas originales también muestran algunas duraciones en textos y longitudes en llamadas; requieren investigación.

La nueva agregación suma duración solo donde type es call. Si una llamada carece de duración, marca el total de minutos del usuario como desconocido para evitar un total parcial presentado como completo. No sustituye automáticamente a cero todas las métricas de clientes sin eventos válidos.

## Valores atípicos y oportunidades comerciales

El criterio Q3 + 1.5×IQR señala valores altos relativos a la muestra; no demuestra que un dato sea erróneo o legítimo. Se conservan para revisión. No hay validación externa de usuarios intensivos reales.

Una clasificación por volumen observado no mide rentabilidad, abandono ni disposición a pagar. Para recomendar un cambio de plan se necesitan consumos y exposición mensual, franquicias, reglas de cobro, costos y preferencias. Los datos disponibles no incluyen GB consumidos. No se estimó ahorro, impacto económico ni una campaña de upselling validada.

## Cambios de presentación

Se retiraron consignas, respuestas incompletas y comentarios del revisor de la copia de portafolio, conservando intacto el adjunto original. No se incluyeron nombres o filas individuales de clientes en la evidencia histórica. Las gráficas antiguas se etiquetan como tales; las nuevas gráficas propuestas normalizan por plan para evitar que la cantidad de clientes domine la comparación.
