# Requerimientos

Completar a partir de los fragmentos de relevamiento del caso. Seguir
la convención de `skill/SKILL.md` (atómico, verificable, sin tecnología
mezclada).

## Requerimientos funcionales

El ID es el del informe (MDA-nnn); entre paréntesis, la clave del issue en Jira.

| ID | Requerimiento | Fragmento(s) de origen |
|----|---------------|------------------------|
| MDA-001 (G13-8) | El sistema debe rechazar toda solicitud de un vehículo de más de 20 años de antigüedad. | Acta 3.3 (M. Duarte) |
| MDA-002 (G13-9) | El sistema debe derivar automáticamente a Suscripción las solicitudes de vehículos cuyo valor supere un umbral determinado. | Acta 3.4 / Acta 4.2 (R. Ferreyra) |
| MDA-003 (G13-10) | El sistema debe mostrar el número y usuario de PAS al emitir desde su terminal. | Acta 3.4 (J. Ponce) |
| MDA-004 (G13-11) · v2 | El sistema debe determinar como VIP, a partir de sus datos y sin carga manual, al cliente que tenga dos o más pólizas vigentes y al menos tres años de antigüedad como cliente. | Acta 3.ª §3.4 (A. Pampín) |
| MDA-005 (G13-25) | Registro del domicilio del cliente. PENDIENTE DE DECISIÓN, no se especifica. [NEEDS CLARIFICATION: el Caso dice «domicilio» y SIGA pide solo «Zona de radicación»; no figura decisor en las actas] | Caso §2.1; hallazgo E1-02 |
| MDA-006 (G13-26) | El sistema debe permitir dar de baja un vehículo registrado. [NEEDS CLARIFICATION: la baja sale de SIGA, no de una decisión del negocio; falta decidir si se mantiene y quién puede pedirla] | SIGA, lista de vehículos, acción «Baja» (captura E0-1) |
| MDA-007 (G13-23) | El sistema no debe considerar VIP a un cliente con marca de mora mientras la mora siga. [NEEDS CLARIFICATION: momento en que se quita la marca de mora; Acta 3.ª §4.6, M. Duarte, 20/11/2026] | Acta 3.ª §3.4; Acta 3.ª §4.6 (M. Duarte) |
| MDA-008 (G13-24) | El sistema debe quitar la categoría VIP, sin intervención manual, a un cliente que deje de cumplir la condición. | Acta 3.ª §3.4 (A. Pampín) |
| MDA-009 (G13-27) | El sistema debe permitir elegir la marca y el modelo del vehículo de una tabla. [NEEDS CLARIFICATION: quién actualiza la tabla y qué hace el usuario si el modelo no está] | Caso §2.1; hallazgo E0-02 |

## Historial de versiones de los requerimientos

| ID | Versión | Fecha | Qué cambió | Issue de cambio |
|----|---------|-------|------------|-----------------|
| MDA-004 | v1 | 16/10/2026 | «El sistema debe categorizar a un cliente como VIP.» [NEEDS CLARIFICATION: antigüedad de 5 años (M. Duarte) o varias pólizas vigentes (R. Ferreyra); Acta 4.1]. Commit b5002b2. | — |
| MDA-004 | v2 | 30/10/2026 | La Dirección decide combinar los dos criterios y que el sistema los determine sin carga manual (Acta 3.ª §3.4). Se agregan MDA-007 y MDA-008. Commit 86bab41. | G13-22 |
| MDA-005 | v1 | 30/10/2026 | Alta: requerimiento que mostró la validación de la E3 (domicilio, pendiente de decisión). | — (alta, issue G13-25) |
| MDA-006 | v1 | 30/10/2026 | Alta: requerimiento que mostró la validación de la E3 (baja de vehículo). | — (alta, issue G13-26) |
| MDA-007 | v1 | 30/10/2026 | Alta: regla nueva del Acta 3.ª §3.4 (no es VIP con mora). Commit 86bab41, con la clave G13-12 por error, y 2ffbd64, con la clave G13-23. | G13-22 |
| MDA-008 | v1 | 30/10/2026 | Alta: regla nueva del Acta 3.ª §3.4 (pérdida automática del VIP). Commit 86bab41, con la clave G13-13 por error, y 2ffbd64, con la clave G13-24. | G13-22 |
| MDA-009 | v1 | 30/10/2026 | Alta: requerimiento que mostró la validación de la E3 (marca y modelo de una tabla). | — (alta, issue G13-27) |

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
| C2 | Criterio de cliente VIP. | Caso §4: M. Duarte («el que tiene antigüedad… cinco años») vs. R. Ferreyra («el que tiene varias pólizas»). | MDA-004 (v2), MDA-007 y MDA-008 | Resuelto: dos o más pólizas vigentes y al menos tres años de antigüedad, determinado por el sistema (Acta 3.ª §3.4). Queda abierto el descuento asociado (ver C4). | A. Pampín |
| C3 | Valor del vehículo a partir del cual interviene suscripción. | Caso §3.2 («si el vehículo supera cierto valor») y Acta 3.4 («un determinado valor»): ninguno fija el importe. | MDA-002 → [NEEDS CLARIFICATION: importe del umbral, no definido] | Pendiente (Acta 4.2). Nota E4: el Acta 3.ª §3.2 fija el importe; es el punto del frente 2 (Emisión) y no se trabaja en este frente. | R. Ferreyra |
| C4 | Acumulación de descuentos (afecta el 15 % VIP). | Caso §4: H. Vidal («están topeados, no se pueden acumular») vs. J. Ponce («los descuentos se suman»). | Ninguno todavía (impacta en el beneficio asociado al VIP de MDA-004) | Pendiente (Acta 2.ª §4.3). | M. Duarte y H. Vidal |
| C5 | Terminología prima/premio. | Acta 3.4 («la prima final que va a pagar el cliente») vs. Glosario §6 (lo que paga el cliente es el premio). | MDA-003 | Observación: en los RF usar «premio». | — |
| C6 | Lo declarado vs. lo implementado. | Caso §2.1 (marca y modelo desde una tabla; alta con domicilio) vs. SIGA (texto libre; solo «Zona de radicación»). | Ninguno (hallazgos E0-2 y E1-2) | Observación: SIGA no sirve como fuente de reglas. | — |

-
| C7 | Momento en que se quita la marca de mora. | Acta 3.ª §3.4 («no es VIP mientras la mora siga») y Acta 3.ª §3.8 (la anulación por falta de pago marca al cliente en mora): ninguna dice cuándo se quita. | MDA-007 → [NEEDS CLARIFICATION: momento en que se quita la marca de mora] | Pendiente (Acta 3.ª §4.6). | M. Duarte (20/11/2026) |
| C8 | Clientes que hoy figuran como VIP en SIGA. | Acta 3.ª §3.4: la marca se pone a mano en la ficha del cliente; se acordó que el equipo de análisis los revise contra la nueva definición. | Ninguno todavía (hallazgo E4-2) | Pendiente de decisión: qué hacer con los que no cumplen. | M. Duarte |
