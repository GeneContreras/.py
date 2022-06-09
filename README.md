# .py
Proyecto orientado a la venta de pasajes de Vuelos DUOC

ENUNCIADO 

Vuelos-Duoc requiere contratar sus servicios de informática para el desarrollo de un proyecto en Python, el cual consiste en la venta de sus pasajes.

El sistema debe considerar que se encuentran disponibles un total de 42 asientos por avión, ver ejemplo:

|	1	2	3		4	5	6	|
|								|
|	7	8	9		10	11	12	|
|								|
|	13	14	15		16	17	18	|
|								|
|	19	20	21		22	23	24	|
|								|
|	25	26	27		28	29	30	|
|______________________                      ________________________|
|______________________                      ________________________|
|	31	32	33		34	35	36	|
|								|
|								|
|	37	38	39		40	41	42	|

Dentro de las restricciones, se contempla que desde el asiento 31 al 42 son para pasajeros vip.

Los precios son:
•	Asiento normal, $78.900
•	Asiento vip, $240.000.

El sistema debe permitir al usuario:
•	Seleccionar un asiento disponible (mostrando los que aún tienen disponibilidad)
•	Indicar el valor, una vez que el usuario lo acepte.
Además, solicitar los siguientes datos del usuario:
•	nombrePasajero
•	rutPasajero
•	telefonoPasajero
•	bancoPasajero
Se pide implementar el siguiente menú:

1.	Ver asientos disponibles
2.	Comprar asiento
3.	Anular vuelo
4.	Modificar datos de pasajero
5.	Salir

Ver asientos disponibles: Mostrará por pantalla todos los asientos disponibles con su número de asiento y los no disponibles los con una “X”

|	1	2	3		4	5	6	|
|								|
|	7	X	X		10	11	12	|
|								|
|	X	X	X		16	X	18	|
|								|
|	19	20	21		22	23	24	|
|								|
|	25	26	27		X	29	30	|
|______________________                      ________________________|
|______________________                      ________________________|
|	X	32	33		34	35	36	|
|								|
|								|
|	X	38	X		40	41	X	|

Comprar asiento: Solicita los datos del usuario, luego el usuario escoge un asiento, si es usuario de “bancoDuoc” el sistema realiza un 15% de descuento en el total de su pasaje.

Anular Pasaje: Deja el asiento nuevamente disponible y elimina los datos del usuario.

Modificar datos de pasajero: Solicita el asiento y Rut (para verificar datos), luego muestra un submenú, en el cual, debe escoger que dato va a modificar, entre ellos se consideran únicamente el nombrePasajero y telefonoPasajero.

Para realizar la evaluación se recomienda crear arreglo multidimensional y funciones para las opciones del menú.

