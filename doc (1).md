![](images/c4e0f487fc994e874fa131e417bc3e26fe0994cc64f828905f18cfc3b5f66607.jpg)

# UNIVERSIDAD DE ANTIQUIA

1803

FACULTAD DE INGENIERIA

PROGRAMA DE INGENIERÍA INSDUSTRIAL

CURSO: ALGORITMIA Y PROGRAMACION

SEMESTRE 2025-2

MANUAL DE USUARIO

CIBERCINEMA UDEA

![](images/43e206bd2ab5e902febfa55f2529600fabc521d1b856c6768d15a9862cfcd82e.jpg)

# Tabla de contenido

1. Introduccion  
2. Especialización de requisitos  
3. Opciones del systema  
4. Beneficios del sistemas  
5. Consideraciones visuales  
6. Equipo de descrollo

# 1. Introduccion:

Cibercinema UdeAbine en la creacion de un cine universitario accesible a diversos publicos, con precios differenciados segun el tipo de vinculo con la universidad. El objetivo es plagiarar un programa en Python que permita: registrar uxuarios, gestionar reservas y cancelarlas, generar facturas personalizadas y almacenar toda la informacion relevante en un archivo CSV. El cine contara con 121 asientos, y el programa informar a los uxuarios sobre la disponibilidad de这些东西 al momento de realizar una reserva.

# 2. Especialación de requisitos:

# - Funcionales:

El problema debe:

a. Registrar al usuario con el tipo de vinculo con la UdeA.  
b. Registrar reservas.  
c. Permitir cancelar reservas unicamente si Tiene的一些 activas.  
d. Permitir estar en orden de día, hora y nombre y sillas disponibles a los usuario laspelículas programadas para el próimo fin de semana.  
e. Permitir acceder al espacio de administrador a quienonga usuario y contraseña de administración.  
f. Ofrecer al usuario la calidad del sitio.

# Noionales

a. Usabilidad: El sistemas debe tener un menu en consola claro y fácil de parler para cualquier usuario.  
b. Rendimiento: Cada operation (registry,resherva,cancelacion)debe responder en menos de 2segundos.

c. Fiabilidad: Si el programa se cierra de forma inesperada, al volver a partir deben conservar los datos guardados (en CSV).  
d. Portability: El programa debe executarse en cualquier computadora con Python 3 instalado (Windows, Linux o Mac).  
e. Seguidad: Solo el administrador con usuario y restraseña puede acceder al modulo de reportes.

# 3. Opcionedesistema

# 3.1 Registrar usuario

Permite registrar los datos de un usuario nuevo.

> SeLECTIONAR la opcION 1 del menu.  
> Ingrasar el documento: deben tener valores numéricos únicamente y tener una extension de 3 a 15 characteres.  
> Ingresar nombre: solo se permite ingresar texto y deben tener una longitudínima de 3 characteres.  
> Ingresar apellido: solo se permite ingresar textual y deben tener una longitudínima de tres caracteres.  
> Ingrésar vinculo: estaisión es la que determina el preco de la boleta, solo debe de ingresar el número correspondiente a laisión deseada.

<table><tr><td>1. Estudiante</td><td>$7,500</td></tr><tr><td>2. Docente</td><td>$10,000</td></tr><tr><td>3. Administrativo</td><td>$8,500</td></tr><tr><td>4. Oficial interno</td><td>$7,000</td></tr><tr><td>5. Publico externo</td><td>$15,000</td></tr></table>

> Si la información se llenó exitosamente, los datos quedan guardados.

# 3.2 Registrar reserva

> SeLECTIONAR la opcION 2 del menu.  
> Ingresar documento previamente registrar; si el documento no está registrar, por medio de un mensaje se le informa al usuario que primero debe registrarse.  
> Ingrasar asiento(s) a resolver: se le做不到 al usuario por medio de una O el asiento disponible y una X asiento occupancy. Al momento de ingresar el asiento, recuerde que deben ser tipo texto y solo dos caracteres, el primero es la fila y el segundo la columna.  
> 0 para terminar: esta optacion debe ingresarla cuando ya no desee reservar más asientos.  
> Si todo está bien, se le entrega a una factura con el nombre del cinema, Fecha y hora exacta de la compra, el documento, el nombre y el vinculo del usuario con la universidad de Antioquia, elPRECIO unitario de la boleta, los asientos reservados, lacantidad de asientos reservados y el total a pagar.

# 3.3 Cancelarresherva

> SeLECTIONAR la opcION 3 del menu.  
> Ingresar documento previamente registrar; si el documento no está registrar, por medio de un mensaje se le informa al usuario que primero debe registrarse.  
> Ingrasar el asiento a cancelar: al momento de ingresar el asiento, recuerde que deben ser tipo texto y solo dos caracteres, el primero es la fila y el segundo la columna. Si el usuario no tiene reservado ese asiento, se le informa por medio de un mensaje, que no ha reservado ese asiento.  
> 0 para terminar: bajo de presionar estaopyción:  
> Si todo está bien, se refleja la cancelación y vuelve a(""); no se da para darce unaopersión differente.

# 3.4 Consultariones del fin de semana

> SeLECTIONAR la opcION 4 del menu.  
> El sistemas arrojaré el encabezado FUNCIONES FIN DE SEMANA.  
> Se muestran todas las functions programadas y el número depelículas disponibles en la cartelera.  
> Se enumeran laspellicas que están disponible para el fin de semana.  
> Se muestra una tabla que incluye el IdPelicula, el día, la hora y lapellicula.  
> El usuario可以选择 ver los horarios de las unidades del viernes, sábado y domingo.  
> Luego de consultar las functions, el sistema permanece activo y le permite al usuario selectionar另一边ccion del menu.

# 3.5 Administrador

> Señecionar la opción 5 del menu.  
> Ingrasar usuario y contraseña asignados previamente para acceder al modo administrador.  
> Si los datos son Incorrectos, se le informa al usuario por medio de un mensaje que no seswanae registrar en el sistemas y se le permite intentarlo de nuevo.  
> Si el acceso es correcto, se muestra el mensaje de bienvenida al administrador y su menu exclusivo.  
En el menu se despliegan las siguientes options:

Total de reservas registradas  
Total de tiques vendidos  
Total de reservas realizadas  
Total pagorealizzato  
- Promedio por vente diario del cine  
- List de sistemas  
- Usario con mayorcantidad de reservas y menorcantidad de reservas  
- Cerrar sesión

> El administrador可以选择 elegir cualquier option para revisar la informacion interna delsystema.  
> Cuando el administrador elija una de las options y posteriormente decide cerrar Sesión, regresará inmediamente al menu principal para realizar另一asaxonies.

# 3.6 Salir

> SeLECTIONAR la opcION 6.  
> El sistemas finaliza la executions.
