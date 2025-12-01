

<p align="center"><img width="200" height="300" alt="image" src="https://github.com/user-attachments/assets/92c84980-623a-469c-8dfe-b0df0a63a041" /></p>

**<p align="center">FACULTAD DE INGENIERÍA</p>**       
**<p align="center">INGENIERÍA INDUSTRIAL</p>**   
**<p align="center">ALGORITMIA Y PROGRAMACIÓN</p>**   
**<p align="center">SEMESTRE 2025-2</p>**   
**<p align="center">MANUAL DE USUARIO</p>**   
**<p align="center">CIBERCINEMA UDEA</p>**   
<p align="center"><img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/5351dc14-26a9-43d9-a075-3f139861afc2" /></p>

**Tabla de contenido**
1.  Introdución
2.  Especificación de requisitos 
3.	Opciones del sistema 
4.	Beneficios del sistema 
5.	Consideraciones visuales 
6.	Equipo de desarrollo 
 
**1.	Introducción:**   
Cibercinema UdeA consiste en la creación de un cine universitario accesible a diversos públicos, con precios diferenciados según el tipo de vínculo con la universidad. El objetivo es desarrollar un programa en Python que permita: registrar usuarios, gestionar reservas y cancelarlas, generar facturas personalizadas y almacenar toda la información relevante en un archivo CSV. El cine contará con 121 asientos, y el programa informará a los usuarios sobre la disponibilidad de estos al momento de realizar una reserva. 

**2.	Especificación de requisitos:**  
	• 	Funcionales: 
El sistema debe: 
a.	Registrar al usuario con el tipo de vínculo con la UdeA. 
b.	Registrar reservas. 
c.	Permitir cancelar reservas únicamente si tiene algunas activas. 
d.	Permitir mostrar en orden de día, hora y nombre y sillas disponibles a los usuarios las películas programadas para el próximo fin de semana. 
e.	Permitir acceder al espacio de administrador a quien tenga usuario y contraseña de administración. 
f.	Ofrecer al usuario la salida del sitio.

No funcionales 
a.	Usabilidad: El sistema debe tener un menú en consola claro y fácil de entender para cualquier usuario. 
b.	Rendimiento: Cada operación (registro, reserva, cancelación) debe responder en menos de 2 segundos. 
c.	Fiabilidad: Si el programa se cierra de forma inesperada, al volver a abrir debe conservar los datos guardados (en CSV). 
d.	Portabilidad: El programa debe ejecutarse en cualquier computadora con Python 3 instalado (Windows, Linux o Mac). 
e.	Seguridad: Solo el administrador con usuario y contraseña puede acceder al módulo de reportes. 
**3.	Opciones del sistema**  
3.1	Registrar usuario 
Permite registrar los datos de un usuario nuevo. 
*	Seleccionar la opción 1 del menú. 
*	Ingresar el documento: debe tener valores numéricos únicamente y tener una extensión de 3 a 15 caracteres. 
*	Ingresar nombre: solo se permite ingresar texto y debe tener una longitud mínima de 3 caracteres. 
*	Ingresar apellido: solo se permite ingresar texto y debe tener una longitud mínima de tres caracteres. 
*	Ingresar vínculo: esta opción es la que determina el precio de la boleta, solo debe de ingresar el número correspondiente a la opción deseada. 



