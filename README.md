# ADBD-Practica1-ModeloER
* Autores: Ithaisa Morales Arbelo (alu0101482194@ull.edu.es). Guillermo Plaza Gayán (alu0101495354@ull.edu.es)
* Asignatura: Administración de Bases de Datos. 4º Curso.
* Curso: 2024/2025.
* Escuela Superior de Ingeniería y Tecnología.
* Universidad de La Laguna.
* Grado en Ingeniería Informática.

## Introducción
En este informe se describe un modelo entidad-relación para un sistema de gestión de una farmacia. Se definen cinco entidades principales: Medicamento, Laboratorio, Familia, Venta y Cliente, cada una con atributos que describen sus características específicas. Además, se establecen relaciones que reflejan cómo estas entidades interactúan entre sí.
    
## Descripción de las entidades definidas
* **Medicamento:** Entidad fuerte que sirve para almacenar y gestionar la información sobre los medicamentos. Contiene información sobre el código del medicamento (único e identificativo), nombre, precio, tipo, unidades en stock, unidades vendidas y cómo es su tipo de venta (con receta o libre).
* **Laboratorio:** Entidad fuerte que almacena infromación sobre el laboratorio como el código del laboratorio, el nombre, el nombre de la persona de contacto, la dirección postal, el fax, el teléfono y la dirección de dónde está ubicado (tanto su calle como el número de la calle).
* **Familia:** Entidad débil, ya que para que se dé la existencia de una familia de medicamentos tiene que haber mínimo un medicamento que forme parte de esta familia. Almacena información como el código identificativo de la familia, el nombre y el tipo de enfermedades sobre las que se aplican los medicamentos pertenecientes a la familia.
* **Venta:** Entidad fuerte que almacena la fecha en la que se realizó la compra, las unidades que se compraron, el precio total de la compra y un código identificativo.
* **Cliente:** Entidad fuerte que almacena el DNI de los clientes junto con sus datos bancarios, además de sus teléfonos de contacto.

## Dominio de los atributos
**Dentro de la entidad medicamento:**
* Atributos identificadores:
    - Código: su valor no se repite dentro de la entidad. Se trata de la clave primaria en forma de string que sirve para identificar de forma inequívoca el medicamento. Ejemplo: PARACETAMOL-500-20 (Dominio: Texto alfanumérico (string), con longitud máxima de 30 caracteres.)
* Atributos descriptores:
    - Precio: almacena el valor numérico del precio del medicamento en euros. Ejemplo: 20,99.(Dominio: Número decimal con dos decimales (precio en euros))
    - Tipo: indica el tipo del medicamento con una string. Puede tomar valores como pomada, jarabe... Ejemplo: comprimido. (Dominio: Texto (string), longitud máxima de 20 caracteres. Valores permitidos incluyen: pomada, jarabe, comprimido, etc.)
    - Unidades en stock: valor numérico. Representa la cantidad de unidades del medicamento disponibles en el inventario. Ejemplo: 5. (Dominio: Número entero positivo)
    - Unidades vendidas: valor numérico. Representa la cantidad de unidades que se han vendido hasta la fecha. Ejemplo: 15. (Dominio: Número entero positivo)
    - Tipo de venta: valor numérico. [1] si se vende con receta, [2] si es un medicamento de venta libre. Ejemplo: 2 (medicamento de venta libre). (Dominio: Número entero (valores permitidos: 1 o 2).)

* Atributos discriminantes:
    - Nombre: Puede identificar también a la entidad aunque no se usa como clave primaria. Ejemplo: Paracetamol 500 gramos. (Dominio: Texto (string), longitud máxima de 50 caracteres)


**Dentro de la entidad laboratorio:**
* Atributos identificadores:
    - Código: su valor no se repite dentro de la entidad. Se trata de la clave primaria en forma de string que sirve para identificar de forma inequívoca el laboratorio. Ejemplo: LAB12345. (Dominio: Texto alfanumérico).
* Atributos descriptores:
    - Fax: indica el número de fax del laboratorio. Ejemplo: +34 915678901. (Dominio: Número de 9 dígitos).
    - Nombre de la persona de contacto: indica el nombre completo de la persona de contacto. Ejemplo: María del Carmen García (Dominio: cadena de texto).
    - Dirección postal: indica la dirección postal. Ejemplo: 37000. (Dominio: numérico de 5 dígitos).
* Atributos multivaluados:
    - Teléfono: puede tener más de un teléfono un laboratorio. Ejemplo: +34 666666666. (Dominio: Número de 9 dígitos).
* Atributos discriminantes:
    - Nombre: Puede identificar también a la entidad aunque no se usa como clave primaria. Ejemplo: Laboratorio García. (Dominio: Texto (string), longitud máxima de 50 caracteres)
* Atributos compuestos: 
    - Dirección: Este atributo puede ser descompuesto en otros dos: número y calle. El atributo número es de dominio numérico. Ejemplo: 15. El atributo calle es una cadena de texto de máximo 50 caracteres. Ejemplo: Calle de la Rosa.

**Dentro de la entidad familia:**
* Atributos identificadores:
    - Código:  su valor no se repite dentro de la entidad. Se trata de la clave primaria que sirve para identificar de forma inequívoca la familia. Ejemplo: FAM123. (Dominio: Texto alfanumérico (string) con longitud máxima de 20 caracteres.)
* Atributos multivaluados:
    - Tipo de enfermedades en las que actúa:  Lista de tipos de enfermedades que pueden ser tratadas por la familia de medicamentos. Es un atributo multivaluado, ya que una familia puede actuar en varios tipos de enfermedades. Ejemplo: Dolor de cabeza.(Dominio: Lista de cadenas de texto (string), cada una con una longitud máxima de 30 caracteres).
* Atributos discriminantes:
    - Nombre: Puede identificar también a la entidad aunque no se usa como clave primaria. Ejemplo: Analgésicos. (Dominio: Texto (string), longitud máxima de 20 caracteres)

**Dentro de la entidad venta:**
* Atributos identificadores:
    - Código:Código único para identificar cada transacción de venta. Este código actúa como la clave primaria para la entidad. Ejemplo: V000000001111111 (Dominio: Texto alfanumérico (string), con longitud máxima de 15 caracteres.)
* Atributos descriptores:
    - Unidades commpradas: Número de unidades del medicamento que se han comprado en una venta específica. Ejemplo: 5. (Dominio: Número entero positivo).
    - Fecha de compra: Fecha en la que se realizó la compra. Ejemplo: 23/12/2024.(Dominio: Fecha (formato DD/MM/AAAA)).
* Atributos calculados:
    - Precio total: Precio total de la venta, calculado como el precio del medicamento multiplicado por las unidades compradas. Ejemplo: 57,17  (Dominio: Número decimal con dos decimales (precio total en euros)).

**Dentro de la entidad cliente:**
* Atributos identificadores:
    - DNI: DNI que sirve para identificar de forma inequívoca a cada cliente. Ejemplo: 79097081N (Dominio: Texto alfanumérico (string), con 9 caracteres (formato típico de DNI español))
* Atributos descriptores:
    - Datos bancarios: Información de la cuenta bancaria del cliente. Ejemplo: ES9100000555550000033333. (Dominio: Texto alfanumérico (string), generalmente el código IBAN, con longitud máxima de 34 caracteres)
* Atributos multivaluados:
    - Teléfono: puede tener más de un teléfono un cliente. Ejemplo: +34 666666666. (Dominio: Número de 9 dígitos).

## Descripción de las relaciones definidas
* **Laboratorio - Medicamento:** Un medicamento es producido por un laboratorio. Un laboratorio fabrica muchos medicamentos. Ejemplo: El laboratorio García produce Paracetamol 500mg y Ibuprofeno 400mg. El Ibuprofeno 400mg con código IBUPROFENO-500-20 fue fabricado en el laboratorio García.
* **Venta - Medicamento:** En una misma venta se pueden vender varios medicamentos, y un medicamento puede estar presente en muchas ventas distintas Ejemplo: Una venta identificada como VENTA001234 incluye Paracetamol 500mg y Ibuprofeno 400mg.
* **Medicamento - Familia:** Un medicamento pertenece a una sola familia, mientras que una familia puede estar compuesta por varios medicamentos Ejemplo: El paracetamol y el ibuprofeno pertenecen a la familia de analgésicos.
* **Venta - Cliente:** Una misma venta es realizada solo por un cliente, pero un cliente puede hacer varias compras. Ejemplo: La venta V001111 solo fue realizada por el cliente con DNI 79097081N, pero este cliente también tiene asociada la venta V001112.

## Restricciones semánticas propuestas
- Los campos de los atributos de las entidades no pueden estar vacíos y tienen que cumplir con el formato específicado por el dominio.

