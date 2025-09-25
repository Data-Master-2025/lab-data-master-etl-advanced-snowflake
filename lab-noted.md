# Preguntas de análisis #
### ¿Cuántos registros fueron descartados por errores? ###
<pre>
SELECT COUNT(ID_ORDER) FROM B_ORDERS_RAW_COMPLEX; -> 1000 filas  
SELECT COUNT(ID_ORDER) FROM S_ORDERS_CLEAN_COMPLEX; -> 629 filas
</pre>
Se han descartado 371 registros  
### ¿Qué proporción de métodos de pago están ausentes o mal escritos? ###
<pre>
// que proporcion de metodos de pago estan mal escritos
SELECT COUNT(S_ORDERS_CLEAN_COMPLEX.REF_PAYMENT_METHOD)
FROM S_ORDERS_CLEAN_COMPLEX
RIGHT JOIN S_PAYMENT_METHODS
ON S_ORDERS_CLEAN_COMPLEX.REF_PAYMENT_METHOD = S_PAYMENT_METHODS.REF_PAYMENT_METHOD;
</pre>
La query devuelve 510 registros. Por tanto un 49% de los metodos de pago estan ausentes o mal escritos  
### ¿Cuál es el ticket medio por pedido? ###
<pre>
SELECT
AVG(AMT_TOTAL)
FROM S_ORDERS_CLEAN_COMPLEX;
</pre>
766.961844
### ¿Cuántos pedidos no tienen fecha de entrega informada? ###
<pre>
  SELECT
COUNT(*)
FROM
S_ORDERS_CLEAN_COMPLEX
WHERE DTE_DELIVERY_EST IS NULL
</pre>
126 registros en silver no tienen fecha de entrega

# Cuántos registros fueron descartados #
Se han descartado 371 registros

# Qué errores o inconsistencias predominaban #

# Qué validaciones aplicaste (formato, tipos, nulos, valores inválidos) #

# Propuesta de otras vistas analíticas en Gold #

