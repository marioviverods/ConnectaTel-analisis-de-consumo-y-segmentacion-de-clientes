# Resumen ejecutivo

ConnectaTel es un caso académico orientado a explorar consumo de llamadas y mensajes, calidad de datos y segmentación. El notebook original contiene evidencia de 4000 clientes, 40000 eventos y dos planes. La revisión se realizó sobre código y resultados guardados, sin los tres CSV originales.

Los perfiles históricos presentan medias de 5.52 mensajes y 4.48 llamadas, con máximos de 17 y 15. La duración acumulada original tiene media de 23.32 y mediana de 19.78, pero su suma no filtraba el tipo de evento. Los valores altos requieren revisión y no prueban por sí solos comportamiento intensivo real.

Se identificaron problemas de consistencia entre código y conclusiones: 40 altas de 2026 frente a un corte en 2024, 96 ciudades con sentinel sin tratar y reglas de segmentación que clasificaban a todos los perfiles completos como Bajo. La versión revisada corrige estas reglas, diferencia ausencia de actividad, valida relaciones y restringe la duración a llamadas. Los nuevos tamaños de segmentos siguen pendientes de ejecución con las fuentes.

La recomendación es completar QA, recalcular perfiles y comparar uso mensual con los planes antes de proponer cambios comerciales. La ausencia de datos de GB y de reglas completas de facturación impide demostrar ahorro o conveniencia de un upgrade. El repositorio presenta estas oportunidades como líneas de investigación, sin atribuir mejoras de ingresos o retención no medidas.
