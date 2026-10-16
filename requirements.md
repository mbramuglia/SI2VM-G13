# Requerimientos

Completar a partir de los fragmentos de relevamiento del caso. Seguir
la convención de `skill/SKILL.md` (atómico, verificable, sin tecnología
mezclada).

## Requerimientos funcionales

| ID | Requerimiento | Fragmento(s) de origen |
| G13-8 | El sistema debe rechazar toda solicitud de un vehículo de más de 20 años de antigüedad.|ACTA 3.3 M.DUARTE|
| G13-9 |El sistema debe derivar automáticamente a Suscripción las solicitudes de vehículos cuyo valor supere un umbral determinado. |Acta 3.4 / Acta 4.2 (R. Ferreyra) |
| G13-10 |El sistema debe mostrar el número y usuario de PAS al emitir desde su terminal.|Acta 3.4 (J. Ponce)|
| G13-11 |El sistema debe categorizar a un cliente como VIP. |Acta 4.1 (M. Duarte / R. Ferreyra) |

## Fragmentos que NO son requerimientos funcionales

| Fragmento | Texto | Categoría | Justificación |
|-----------|-------|-----------|---------------|
| Caso §4 / §7 (A. Pampín) | «Quiero un sistema rápido, moderno y fácil de usar. Que el productor lo pueda usar sin capacitación.» | RNF | Describe cualidades (velocidad, usabilidad) sin métrica; el Acta 4.5 confirma que no hay cifra. |
| Acta 3.2 (A. Pampín) | «El sistema nuevo debe estar operativo el 1 de marzo de 2027.» | Objetivo/meta de negocio | Es un plazo de negocio, no una función del sistema. |
| Caso §3.2 | «El circuito completo demora entre 24 y 72 horas hábiles… principal motivo por el cual la compañía pierde operaciones.» | Objetivo/meta de negocio | Expresa el resultado buscado (emitir más rápido); de ahí sale MDA-003, pero en sí no es un RF. |
| Caso §4 (J. Ponce) | «Necesito emitir yo, desde mi computadora, en el momento.» | Objetivo/meta de negocio | Es una necesidad del usuario; el RF concreto lo fija la Dirección en el Acta 3.4. |
| Acta 3.2 (A. Pampín) | «…con SIGA disponible en modo consulta durante los dos meses siguientes.» | Restricción técnica | Impone convivir con una plataforma existente (SIGA); no describe qué hace el sistema nuevo. |
| Acta 3.1 (A. Pampín) | «La contabilidad y la conciliación bancaria se integran pero no se reemplazan.» | Restricción técnica | Obliga a integrarse con sistemas ya instalados; es una condición de implementación. |
| Caso §2 | «Desarrollado en 2003 sobre Visual Basic 6 con base de datos SQL Server… No existe documentación técnica ni funcional.» | Dato de contexto | Describe la tecnología del sistema actual, sin pedir nada al nuevo. |
| Caso §3.2, paso 3 | «El operador carga los datos en SIGA a mano, reescribiendo lo que el productor ya había escrito en el PDF.» | Dato de contexto | Describe cómo se hace hoy la carga de clientes y vehículos. |
| Caso §4 (S. Roldán) | «El sistema te deja cargar cualquier año, no te frena nada.» | Dato de contexto | Describe el comportamiento actual de SIGA (verificado en E0-1), no el del sistema nuevo. |

## Conflictos u observaciones detectadas

| # | Conflicto | Fragmentos en conflicto | RF afectado | Estado | Decisor |
|---|-----------|-------------------------|-------------|--------|---------|
| C1 | Antigüedad máxima del vehículo. | Caso §4: M. Duarte («autos de más de veinte años no tomamos») vs. S. Roldán («se lo tomamos igual hasta veinticinco»). | MDA-001 | Resuelto: 20 años, sin excepciones (Acta 3.3). | M. Duarte |
| C2 | Criterio de cliente VIP. | Caso §4: M. Duarte («el que tiene antigüedad… cinco años») vs. R. Ferreyra («el que tiene varias pólizas»). | MDA-004 → [NEEDS CLARIFICATION: antigüedad de 5 años (Duarte) vs. varias pólizas (Ferreyra)] | Pendiente (Acta 4.1). | M. Duarte y R. Ferreyra |
| C3 | Valor del vehículo a partir del cual interviene suscripción. | Caso §3.2 («si el vehículo supera cierto valor») y Acta 3.4 («un determinado valor»): ninguno fija el importe. | MDA-002 → [NEEDS CLARIFICATION: importe del umbral, no definido] | Pendiente (Acta 4.2). | R. Ferreyra |
| C4 | Acumulación de descuentos (afecta el 15 % VIP). | Caso §4: H. Vidal («están topeados, no se pueden acumular») vs. J. Ponce («los descuentos se suman»). | Ninguno todavía (impacta en MDA-004) | Pendiente (Acta 4.3). | M. Duarte y H. Vidal |
| C5 | Terminología prima/premio. | Acta 3.4 («la prima final que va a pagar el cliente») vs. Glosario §6 (lo que paga el cliente es el premio). | MDA-003 | Observación: en los RF usar «premio». | — |
| C6 | Lo declarado vs. lo implementado. | Caso §2.1 (marca y modelo desde una tabla; alta con domicilio) vs. SIGA (texto libre; solo «Zona de radicación»). | Ninguno (hallazgos E0-2 y E1-2) | Observación: SIGA no sirve como fuente de reglas. | — |

-
