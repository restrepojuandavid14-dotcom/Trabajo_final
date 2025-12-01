

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
   **Funcionales:**     
   
El sistema debe:   
a.	Registrar al usuario con el tipo de vínculo con la UdeA.  
b.	Registrar reservas.   
c.	Permitir cancelar reservas únicamente si tiene algunas activas.   
d.	Permitir mostrar en orden de día, hora y nombre y sillas disponibles a los usuarios las películas programadas para el próximo fin de semana.   
e.	Permitir acceder al espacio de administrador a quien tenga usuario y contraseña de administración.   
f.	Ofrecer al usuario la salida del sitio.  

**No funcionales:**  

a.	Usabilidad: El sistema debe tener un menú en consola claro y fácil de entender para   cualquier usuario.   
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

  <img width="623" height="227" alt="image" src="https://github.com/user-attachments/assets/3738455b-7a0c-45e7-b989-4f661a5794fa" />   

  
3.2	Registrar reserva   

*	Seleccionar la opción 2 del menú.   
*	Ingresar documento previamente registrado; si el documento no está registrado, por medio de   un mensaje se le informa al usuario que primero debe registrarse.   
*	Ingresar asiento(s) a reservar: se le mostrará al usuario por medio de una O el asiento disponible y una X asiento ocupado. Al momento de ingresar el asiento, recuerde que debe ser tipo texto y solo dos caracteres, el primero es la fila y el segundo la columna.   
*	0 para terminar: esta opción debe ingresarla cuando ya no desee reservar más asientos.   
*	Si todo está bien, se le entregará una factura con el nombre del cinema, fecha y hora exacta de la compra, el documento, el nombre y el vínculo del usuario con la universidad de Antioquia, el precio unitario de la boleta, los asientos reservados, la cantidad de asientos reservados y el total a pagar.   
 
3.3	Cancelar reserva   

*	Seleccionar la opción 3 del menú.   
*	Ingresar documento previamente registrado; si el documento no está registrado, por medio de un mensaje se le informa al usuario que primero debe registrarse.   
*	Ingresar el asiento a cancelar:  al momento de ingresar el asiento, recuerde que debe ser tipo texto y solo dos caracteres, el primero es la fila y el segundo la columna. Si el usuario no tiene reservado ese asiento, se le informa por medio de un mensaje, que no ha reservado ese asiento.   
*	0 para terminar: luego de presionar esta opción:  
*	Si todo está bien, se refleja la cancelación y vuelve a mostrar el menú por si se desea marcar una opción diferente.   

3.4	Consultar funciones del fin de semana  

*	Seleccionar la opción 4 del menú.  
*	El sistema arrojará el encabezado FUNCIONES FIN DE SEMANA.  
*	Se muestran todas las funciones programadas y el número de películas disponibles en la cartelera.  
*	Se enumeran las películas que están disponibles para el fin de semana.   
*	Se muestra una tabla que incluye el IdPelicula, el día, la hora y la película.  
*	El usuario puede ver los horarios de las funciones del viernes, sábado y domingo.  
*	Luego de consultar las funciones, el sistema permanece activo y le permite al usuario   seleccionar otra opción del menú.    

3.5	Administrador   
  
*	 Seleccionar la opción 5 del menú.  
*	Ingresar usuario y contraseña asignados previamente para acceder al modo administrador.  
*	Si los datos son incorrectos, se le informa al usuario por medio de un mensaje que no se encuentra registrado en el sistema y se le permite intentarlo de nuevo.  
*	Si el acceso es correcto, se muestra el mensaje de bienvenida al administrador y su menú exclusivo.  
*	En el menú se despliegan las siguientes opciones:  
-	Total de reservas registradas  
-	Total de tiquetes vendidos  
-	Total de reservas realizadas   
-	Total pago realizado  
-	Promedio por venta diario del cine   
-	Lista de usuarios   
-	Usuario con mayor cantidad de reservas y menor cantidad de reservas   
-	Cerrar sesión  

*	El administrador puede elegir cualquier opción para revisar la información interna del sistema.   
* Cuando el administrador elija una de las opciones y posteriormente decida cerrar sesión, regresará inmediatamente al menú principal para realizar otras acciones.   
  
3.6	Salir   

*	Seleccionar la opción 6.  
*	El sistema finaliza la ejecución.   



