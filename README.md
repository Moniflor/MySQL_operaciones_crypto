# MySQL_operaciones_crypto

Este repositorio contiene una base de datos relacionada con criptomonedas implementada en MySQL. La base de datos almacena información sobre operaciones de compra y venta de criptomonedas, y también incluye una tabla para monedas cripto específicas.

En la carpeta documentation/ agregamos enlaces de interés a la documentación oficial de MySQL y a algún curso que podría resultar útil.

##Tablas de la Base de Datos

###**Tabla 'operaciones_crypto'**

Esta tabla registra las operaciones de compra y venta de criptomonedas realizadas por los usuarios. A continuación, se detallan las columnas de la tabla:

- **id_operacion**: Identificador único de la operación.
- **fecha_operacion**: Fecha y hora en que se realizó la operación.
- **id_moneda**: ID de la moneda cripto involucrada en la operación, que se relaciona con la tabla **'monedas_crypto'**.
- **precio_crypto**: Precio unitario de la criptomoneda al momento de la operación.
- **cantidad**: Cantidad de criptomonedas compradas o vendidas en la opercaión.

###**Tabla 'monedas_crypto'**

Esta tabla contiene información sobre las diferentes criptomonedas disponibles en el sistema. Cada criptomoneda tiene un ID único y un nombre descriptivo. A continuación, se detallan las columnas de la tabla:

- **id_moneda**: Identificador único de la moneda cripto.
- **nombre_crypto**: Nombre de la criptomoneda.

En el repostorio se adjunta el script de la estructura de la base de datos.
https://github.com/Moniflor/MySQL_operaciones_crypto/blob/main/bdcrypto.sql 

##Procedimientos Almacenados

Hemos creado varios procedimientos almacenados para realizar consultas comunes y obtener información relevante sobre las operaciones de criptomonedas almacenadas en la base de datos. A continuación, se describen los procedimientos y su lógica.

En la carpeta procedures/ se encuentran los script de los procedimientos almacenados.

###**Procedimiento 'calcular_precio'**

Este procediemiento no tiene parámetros y devuelve todas las operaciones de la tabla 'operaciones_crypto' jutno con una columna adicional llamada 'euros', que representa el valor en euros de cada operación. El cálculo se realiza multiplicando el 'precio_crytpto' por la 'cantidad' y redondeando a dos decimales.

https://github.com/Moniflor/MySQL_operaciones_crypto/blob/main/procedures/calcular_precio.txt

**Ejemplo**

Supongamos que tenemos una operación de compra de 1.5 bitcoins('cantidad') a un precio de 35000 euros por bitcoin('precio_crypto'). El resultado del procedimiento 'calcular_precio' mostrará esta operación con un valor total de 52500 euros(1.5 bitcoins * 35000 euros/bitcoin).

###**Procediemiento 'media_precio_general'**

Este procedimiento toma un parámetro 'moneda' (nombre de la criptomoneda) y calcula el precio promedio de la criptomoneda específica en todas las operaciones registradas en la tabla 'operaciones_crypto'. El resultado redondea a dos decimales.

https://github.com/Moniflor/MySQL_operaciones_crypto/blob/main/procedures/media_precio_general.txt

**Ejemplo**

Si tenemos las siguientes operaciones de compra de Bitcoin('btc') en la tabla 'operaciones_crypto':
- compra 1 bitcoin a 30000 euros.
- compra 2 bitcoin a 32000 euros.

El resultado del procedimiento 'media_preio_general' para la criptomoneda 'btc' sería:

(30000 euros + 32000 euros)/3 bitcoins = 31000 euros.

###**Procedimiento 'total_euros'**

Este procedimiento toma un parámetro 'moneda' (nombre de la criptomoneda) y devuelve el valor total en euros de todas las operaciones de esa criptomoneda registradas en la tabla 'operaciones_crypto'. El resultado se redondea a dos decimales.

**Ejemplo**

Si tenemos las siguientes operaciones de compra de Ripple ('xrp') en la tabla 'operaciones_crypto':
- compra 500 xrp a 1.20 euros por xrp.
- compra 1000 xrp a 1.30 euros por xrp.

El resultado del procedimiento 'total_euros' para la criptomoneda 'xrp' sería:

(500 xrp * 1.20 euros/xrp) + (1000 xrp * 1.30 euros/xrp) = 1700 euros.

###**Procedimiento 'total_cantidad'**

Este procedimiento toma un parámetro 'moneda' (nombre de la criptomoneda) y devuelve el total de la cantidad de esa criptomoneda involucrada en todas las operaciones registradas en la tabla 'operaciones_crypto'. El resultado se redondea a siete decimales.

https://github.com/Moniflor/MySQL_operaciones_crypto/blob/main/procedures/total_cantidad.txt

**Ejemplo**

Si tenemos las siguientes operaciones de compra de Ethereum ('eth') en la tabla 'operaciones_crypto':
- compra 1.25 'eth'
- compra 0.75 'eth'

El resultado del procedimiento 'total_cantidad' para la criptomoneda 'eth' sería:

1.25 eth + 0.75 eth = 2 eth

## Contribuciones

¡Las contribuciones a este proyecto son bienvenidas! Si deseas mejorar los porcedimientos existentes, agregar nuevas características o corregir errores, no dudes en enviar un pull request.


