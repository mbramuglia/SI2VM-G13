Casos de uso

 UC-01: Emitir Poliza del Automotor
 
 Actor: Operador de Mesa de Ayuda

Precondición: El Operador debe estar autenticado en el sistema nuevo.

Flujo principal:
1. El Operador ingresa los "Datos del cliente" (tomador).
2. El Operador ingresa los "Datos del vehículo".
3. El sistema ejecuta <<include>> Validar antigüedad del vehículo (controlando tope de 20 años).
4. El sistema registra el nuevo vehículo y al cliente.
5. El sistema emite la póliza confirmada.

Flujo(s) alternativo(s):
-Paso 3a (Rechazo): Si el vehículo supera los 20 años, el sistema informa el rechazo automático y finaliza el caso de uso sin guardar.
-Paso 4a (Derivación por Valor): <<extend>> Solicitar intervención de Suscriptor. Condición: Si el valor del vehículo supera el umbral parametrizado, el sistema interrumpe la emisión directa y deriva el trámite a la bandeja de Suscripción.


Postcondición: El vehículo y el cliente quedan registrados y la póliza es emitida (o derivada a suscripción).

Relaciones con otros casos de uso:

| Relación |    Caso de uso relacionado    | Tipo (include/extend) |                                          Justificación                                       |
|----------|-------------------------------|-----------------------|----------------------------------------------------------------------------------------------|
|    1     |Validar antigüedad del vehículo|      Include          | Se ejecuta siempre y de forma obligatoria como parte del flujo base antes de aceptar el auto.|
|    2     |Solicitar intervención de Suscriptor|      Extend           | Extiende el flujo base opcionalmente solo bajo la condición de que el valor del auto cruce el umbral de dinero.|

Recordar (ver skill/SKILL.md): include = siempre se ejecuta como parte
del flujo, sin excepción. extend = extiende opcionalmente bajo una
condición específica, el flujo base es completo sin ella. Toda relación
sin justificación no cuenta como completa.

## Fragmentos considerados para este caso de uso

Listar qué fragmentos del relevamiento se usaron para armar este caso
de uso, y qué parte del flujo justifica cada uno.

| Fragmento | Qué aporta al caso de uso |
|-----------|---------------------------|
|Caso §2.1 y §3.2 |Define al Operador de Mesa de Ayuda como el Actor Principal. Aporta los pasos 1, 2, 4 y 5 del flujo principal (ingresar datos, registrar y emitir).|
|Acta 3.3 (M. Duarte)| Aporta el paso 3 obligatorio (<<include>> Validar antigüedad) y el flujo alternativo 3a de rechazo automático, justificando la regla estricta del tope de 20 años.|
|Acta 3.4 y 4.2 (R. Ferreyra)| Aporta el flujo alternativo 4a (<<extend>> Solicitar intervención de Suscriptor), estableciendo que si el vehículo supera el umbral de valor, la emisión se frena y se deriva. Suma al Suscriptor como actor secundario.|
|Caso §5 y Acta 3.4| Identifica al Productor Asesor de Seguros (PAS) como actor secundario/iniciador externo que origina la solicitud inicial.|

## Revisión de la E4 (cambio: Acta 3.ª §3.4, definición de cliente VIP · issue G13-22)

El caso de uso UC-01 no cambia. Se revisó: la categoría VIP la determina el sistema a partir de datos del cliente (pólizas vigentes, antigüedad y mora) y no es un paso del flujo ni la ejecuta un actor. Por eso no se agrega paso, flujo alternativo ni relación include/extend.
