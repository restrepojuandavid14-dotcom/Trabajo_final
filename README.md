# Trabajo_final  

## Integrantes del proyecto
1. Manuela Rojas Mazo
2. Mariana Carvajal Chica 
3. Juan David Restrepo Rodríguez    

## Descripción  
Somos un equipo que se destaca por combinar habilidades técnicas con competencias blandas. Nos enfocamos en mejorar continuamente, aprendiendo de cada etapa del proceso para lograr resultados sólidos y bien fundamentados.  

**-> Manuela Rojas Mazo:** Estudiante de Ingeniería Industrial destacada por las habilidades de programación y resolución de problemas.  
**-> Mariana Chica Carvajal:**  Estudiante de Ingeniería Industrial destacada por el buen trabajo en equipo, el análisis crítico, la resolución de problemas y la adaptabilidad.  
**-> Juan David Restrepo Rodríguez:**   Estudiante de Ingeniería Industrial destacado por las habilidades de liderazgo, el enfoque en la mejora continua y la resolución de problemas.  

## Cibercinema
   <img alt="I&S" height="200px" src="https://github.com/user-attachments/assets/83ee874b-7daf-494c-8d8b-82ca7e46a3b5">


 La Universidad de Antioquia planea crear un espacio cinematográfico también conocido como cinema, para ofrecer a la comunidad universitaria la capacidad de asistir a cine en las inmediaciones de la ciudadela universitaria los fines de semana. Con base en lo anterior se plantea apoyarse en los estudiantes de Ingeniería Industrial de la UdeA para crear el boceto del programa de consola en Python para poder gestionar usuarios, reservas, generar cobros, facturas, reportes y algo más. El programa debe permitir registrar usuarios, consultar la disponibilidad de películas para el próximo fin de semana, crear reservas, cancelar reservas, imprimir facturas, y mostrar el estado administrativo de los ingresos y del servicio de cine en la UdeA.  

<div>
    <img alt="CC" height="60px" src="https://raw.githubusercontent.com/juliancastillo-udea/2024-1-ProgramacionPosgrados/main/images/by.xlarge.png">
    <img alt="Attribution" height="60px" src="https://raw.githubusercontent.com/juliancastillo-udea/2024-1-ProgramacionPosgrados/main/images/nc.xlarge.png">
    <img alt="NC" height="60px" src="https://raw.githubusercontent.com/juliancastillo-udea/2024-1-ProgramacionPosgrados/main/images/sa.xlarge.png">
    <img alt="SA" height="60px" src="https://raw.githubusercontent.com/juliancastillo-udea/2024-1-ProgramacionPosgrados/main/images/cc-icons.png">
</div> CC BY-NC-SA 4.0  

## Visión
Cibercinema busca crear un espacio cultural y recreativo para los estudiantes de la Universidad de Antioquia, mediante una aplicación de consola que gestione usuarios, reservas y reportes administrativos de manera sencilla.

## Objetivo principal:  
Ofrecer una herramienta práctica y educativa que simule la administración de un cine universitario.

## Beneficios:

1. Permitir a los estudiantes aplicar conceptos de programación orientada a objetos en un caso real.  

2. Desarrollar habilidades en trabajo colaborativo y uso de GitHub.  

3. Aportar a la vida universitaria un proyecto que fomente la cultura cinematográfica.

## Especificación de requisitos
* **Funcionales:**
> El sistema debe:
> 1.   Registrar al usuario con el tipo de vínculo con la UdeA.
> 2.   Registrar reservas.
> 3.   Permitir cancelar reservas únicamente si tiene algunas activas.
> 4.   Permitir mostrar en orden de día, hora y nombre y sillas disponibles a los usuarios las
películas programadas para el próximo fin de semana.
> 5.   Permitir acceder al espacio de administrador a quien tenga usuario y contraseña
de administración.
> 6.   Ofrecer al usuario la salida del sitio.
* **No funcionales**
> 1.   Usabilidad: El sistema debe tener un menú en consola claro y fácil de entender para cualquier usuario.
> 2.   Rendimiento: Cada operación (registro, reserva, cancelación) debe responder en menos de 2 segundos.
> 3.   Fiabilidad: Si el programa se cierra de forma inesperada, al volver a abrir debe conservar los datos guardados (en CSV).
> 4. Portabilidad: El programa debe ejecutarse en cualquier computadora con Python 3 instalado (Windows, Linux o Mac).
> 5. Seguridad: Solo el administrador con usuario y contraseña puede acceder al módulo de reportes.
## Diagrama de Gantt
   <img alt="I&S" height="4000px" src="https://github.com/user-attachments/assets/00ceb6f4-0781-44b3-85ac-51664508b6c4">
Evolución del Proyecto (Control de Versiones)

# Plan de Versionado 

El trabajo evolucionó en varias fases, cada una siendo bastante significativa.

---

## **Versión 1.0 – Menú inicial sin funciones**
- Implementación del menú principal en un solo bloque `while`.
- Toda la lógica estaba escrita de forma secuencial.
- No existía separación de responsabilidades.

---

## **Versión 1.1 – Modularización inicial**
- Se creó una función para el menú principal: `menu_p()`.
- Primera reorganización del código para mejorar la lectura y pruebas.
- Se mantuvo la lógica principal dentro de un solo archivo.

---

## **Versión 1.2 – Conversión de cada opción a funciones**
- Cada opción del menú se convirtió en una función correcta e independiente.
- Lógica separada:
  - registrar usuario  
  - registrar reserva  
  - cancelar reserva  
  - consultar funciones  
- Esto mejoró la reutilización y el mantenimiento del código.

---

## **Versión 1.3 – Corrección de errores previos a la entrega**
Se resolvieron cuatro errores detectados en pruebas:
- Validación incorrecta de entradas.
- Duplicación de registros en reservas.
- Problemas al cancelar reservas.
- Ajustes en los diccionarios internos.

---

## **Versión 1.4 – Función para guardar en CSV**
- Se añadió una nueva función: `guardar_csv()`.
- Se creó la función para escribir los diccionarios de usuarios y reservas en un archivo `.csv`.
- Esta mejora permitió persistencia de datos entre ejecuciones.


## Presupuesto del proyecto

**->Valor hora: $7.115**


**Manuela Rojas Mazo**

   Inversión semanal (5 horas): $35.575.
   
   Inversión total (16 semanas): $569.200.

**Mariana Carvajal Chica**

   Inversión semanal (5 horas): $35.575.
   
   Inversión total (16 semanas): $569.200.

**Juan David Restrepo Rodríguez**   

   Inversión semanal (5 horas): $35.575.
   
   Inversión total (16 semanas): $569.200.
   

**->Valor final: $1'707.600**

