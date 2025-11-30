[src.md](https://github.com/user-attachments/files/23842200/src.md)
#**Cibercinema UdeA**


#**Integrantes**



*   Manuela Rojas Mazo
*   Mariana Carvajal Chica
*   Juan David Restrepo Rodríguez







#**Librerías**

Solo se utilizó una librería para el control del tiempo real en el que compra el usuario.


```python
import datetime
```

#**Almacenamiento de datos**


Para el almacenamiento de los datos se utilizaron listas y diccionarios. Estos últimos estructuraban los datos de manera más organizada, facilitanto así, la llamada de las llaves y valores en diferentes funciones. El primer diccionario "registrar_user" guarda información del usuario cada que hace un registro, los datos que guarda son el documento,el nombre, apellido y vínculo con la universidad de Antioquia.El segundo diccionario es "registrar_reserva" que guarda el documento y los asientos reservados por fila y columna."Precios" es un diccionario que establece el precio  de cada tipo de vinculo.También tenemos una lista con cada uno de los vínculos Por último tenemos el diccionario de los administradores que guarda un usuario y clave predeterminado y es de uso exclusivo.


```python
#Diccionario para registrar usuario
registrar_user = {}
#Diccionario para registrar reserva
registrar_reserva = {}

# Precios según vínculo
precios = {
    'estudiante': 7500,
    'docente': 10000,
    'administrativo': 8500,
    'oficial interno': 7000,
    'publico externo': 15000
}

# Diccionario de los administradores
DictAdmin = {
    'admin':'123'
}

#Vinculo con la u:
vinculo = ['Estudiante','Docente','Administrativo','Oficial interno','Publico Externo']
```

#**CSV**


Se crea el nombre del archivo csv donde se guardan los datos principales de cada usuario.


```python
nombre_archivo= 'Reservas.csv'#debemos de ponerlo al inicio en el trabajo
```

Se crea el archivo en una función llamada "actualizar_csv" donde se guarda los datos separados por coma con la información del documento, nombre de usuario, apellido, vinculo, valor de la boleta según el vínculo, el valor total de las boletas registradas y finalmentecada asiento reservado.


```python
def actualizar_csv(nombre_archivo):

  """
  Actualiza el archivo CSV con los datos de usuarios y sus reservas.

  Args:
      nombre_archivo (str): Nombre o ruta del archivo a sobrescribir.
  """
  with open(nombre_archivo, 'w', encoding='utf-8') as f:
      f.write('Documento,Nombre,Apellido,Vinculo,Valor unitario,Total,Reservas\n')

      for doc, datos in registrar_user.items():

          nombre = datos[0]
          apellido = datos[1]
          vinculo = datos[2]
          precio = precios[vinculo.lower()]

          reservas = registrar_reserva.get(doc, [])
          total = len(reservas) * precio

          f.write(f"{doc},{nombre},{apellido},{vinculo},{precio},{total},{reservas}\n")
```

# **Funciones**

**menu_a():**

Retorna el texto del menú administrativo con 8 opciones (estadísticas, reportes y cerrar sesión).

**validar_admin():**

Solicita usuario y contraseña, verificando que coincidan con los datos del diccionario DictAdmin. Repite hasta que las credenciales sean correctas.

**menu_p():**

Retorna el texto del menú principal del sistema con 6 opciones (registro, reservas, consultas y salir).

**crear_cinema():**

Crea una matriz de 11x11 llena de 'O' que representa la sala de cine con todos los asientos disponibles.

**imprimir_sala_cine():**

Muestra visualmente la disposición de la sala de cine con letras A-K para identificar filas y columnas, indicando asientos disponibles (O) y ocupados (X).

**guardar_reserva():**

Marca un asiento como ocupado ('X') en la matriz, convirtiendo las letras de fila/columna en índices y guardando la reserva en el diccionario.

**factura():**

Genera e imprime la factura completa del usuario con sus datos, asientos reservados, precio según vínculo y total a pagar.

**validar_numero():**

Solicita y valida que un número de documento tenga solo dígitos y longitud entre 3 y 15 caracteres.

**validar_string():**

Solicita y valida que una cadena tenga al menos 3 caracteres y no contenga números.

**validar_documento():**

Verifica si un documento ya existe en el diccionario registrar_user, retornando True o False.

**registrar_usuario():**

Agrega un dato (nombre, apellido o vínculo) a la lista de información del usuario en el diccionario.

**cancelar_reserva(lista_asiento, cinema, doc):**

Libera un asiento reservado, marcándolo como disponible ('O') y eliminándolo del registro de reservas del usuario.

**total_reservas_registradas():**

Cuenta y retorna el número total de asientos reservados por todos los usuarios.

**total_tiquetes_vendidos():**

Calcula el total de tiquetes vendidos (equivalente al total de reservas).

**total_reservas_realizadas():**

Retorna la cantidad de usuarios que han hecho al menos una reserva.

**total_pago_realizado():**

Calcula el monto total generado multiplicando las reservas de cada usuario por su precio según vínculo.

**promedio_ventas_diario():**

Calcula el promedio de tiquetes vendidos por usuario que tiene reservas activas.

**lista_usuarios():**

Imprime en pantalla todos los usuarios registrados con su documento, nombre completo y tipo de vínculo.

**reservasMayMen():**

Identifica y muestra qué usuario tiene la mayor cantidad de reservas y cuál tiene la menor cantidad.

**imprimir_cartelera():**

Despliega la cartelera del fin de semana con las 9 funciones programadas, mostrando 3 películas con sus horarios de viernes, sábado y domingo.


```python

#Función letrero del menu principal
def menu_a():
  """
  Retorna el menú principal del administrador como una cadena multilínea.

  Returns:
      str: Texto con las opciones del menú administrativo.
  """

  menu_admin = """

MENÚ

1. Total de reservas registradas
2. Total de tiquetes vendidos
3. Total de reservas realizadas
4. Total pago realizado
5. Promedio por venta diario del cine
6. Lista de usuarios
7. Usuario con mayor cantidad de reservas y menor cantidad de reservas.
8. Cerrar sesión
"""
  return menu_admin

#Función validar ingreso al administrador
def validar_admin(entrada1, entrada2):
  """
  Solicita y valida las credenciales del administrador mediante consola.

  Args:
      entrada1 (str): Texto que se muestra para pedir el usuario.
      entrada2 (str): Texto que se muestra para pedir la contraseña.

  La función no retorna nada, pero mantiene un ciclo hasta
  que el usuario y la contraseña coincidan con los valores en DictAdmin.
  """
  while True:
    user = input(f'{entrada1}--->').lower()
    password = input(f'{entrada2}--->')
    if user in DictAdmin.keys():
      if user in DictAdmin.keys() and (password == DictAdmin[user]):
        print(f'\nBienvenid@, {user}')
        break

      elif user in DictAdmin.keys() and (password != DictAdmin[user]):
        print('La clave es incorrecta, inténtelo de nuevo')
        continue
    else:
      print(f'\nEl usuario {user} no se encuentra registrado en el sistema. Inténtelo de nuevo')

#Función letrero del menu administrador
def menu_p():
  """
  Retorna el menú principal del sistema como una cadena multilínea.

  Returns:
      str: Texto con las opciones principales del programa.
  """

  menu_principal = """

MENÚ PRINCIPAL

1. Registrar usuario
2. Registrar reserva
3. Cancelar reserva
4. Consultar funciones fin de semana
5. Administrador
6. Salir
"""

  return menu_principal

#Función para crear el cinema
def crear_cinema():
  """
  Crea la matriz de asientos del cine, inicialmente todos disponibles ('O').

  Returns:
      list: Lista de listas (11x11) que representa los asientos del cine.
  """
  lista_asientos_cinema = []
  for i in range(11):
      fila = []
      for j in range(11):
          fila.append('O')
      lista_asientos_cinema.append(fila)
  return lista_asientos_cinema

#Función para imprimir el cinema
def imprimir_sala_cine(lista: list):
  """
  Imprime en pantalla la disposición actual de la sala de cine.

  Args:
      lista (list): Matriz 11x11 con los asientos. 'O' = disponible, 'X' = ocupado.
  """

  lista_letras11 = []
  letras = 'ABCDEFGHIJK'
  for letra in letras:
      lista_letras11.append(letra)
  print('='*60)
  print("Cibercinema UdeA (O disponible, X ocupado)".center(60))
  print(' '*4, end='')
  for c in lista_letras11:
      print(c, end='    ')
  print()
  for i,j in enumerate(lista):
      print(lista_letras11[i], end=' ')
      print(j)
  print('='*60)

#Función para guardar la reserva
def guardar_reserva(lista_asiento, cinema):
  """
  Registra una reserva marcando un asiento como ocupado en la matriz del cine.

  Args:
      lista_asiento (list|tuple): Asiento solicitado en formato [fila, columna] usando letras A-K.
      cinema (list): Matriz actual de asientos del cine.

  Returns:
      list: La matriz del cine actualizada tras guardar la reserva.

  Nota:
      También agrega el asiento al diccionario registrar_reserva[doc].
  """
  # Extrae fila y columna como letras (A-K)
  fila_letra = lista_asiento[0].upper()
  columna_letra = lista_asiento[1].upper()

  # Convertir las letras en índices (A=0, B=1, ..., K=10)
  letras = 'ABCDEFGHIJK'
  if columna_letra not in letras or fila_letra not in letras:
      print("Asiento inválido. Solo se aceptan letras A-K.") #Preguntarle al profesor
      return cinema

  col = letras.index(columna_letra)
  fila = letras.index(fila_letra)

  # Validar si ya está ocupado
  if cinema[fila][col] == 'X' and doc in registrar_reserva:
      print('\nEl asiento ya está ocupado, seleccione otro')

  elif doc not in registrar_reserva:
    registrar_reserva[doc] = []
  registrar_reserva[doc].append(fila_letra + columna_letra)
  cinema[fila][col] = 'X'
  print('\nCargando...')
  print('La reserva fue guardada exitosamente')
  return cinema

#Función para imprimir la factura
def factura(doc):
  """
  Imprime la factura de compra para el usuario especificado.

  Args:
      doc (int|str): Número de documento del usuario.

  La factura incluye:
      - Datos del cliente
      - Asientos reservados
      - Precio total según vínculo
      - Fecha y hora de emisión
  """

  # Datos del usuario
  nombre = registrar_user[doc][0].upper()
  apellido = registrar_user[doc][1].upper()
  vinculo = registrar_user[doc][2]

  # Asientos reservados
  if doc in registrar_reserva:
      asientos = registrar_reserva[doc]
  else:
      asientos = []

  # Precio según vínculo
  precio = precios[vinculo.lower()]

  # Cálculos
  cantidad = len(asientos)
  total = cantidad * precio
  fecha = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

  print("\n" + "="*80)
  print("FACTURA CIBERCINEMA UdeA".center(80))
  print("="*80)
  print(f"Fecha y hora:".ljust(39) + f"{fecha}".rjust(40))
  print(f"Documento:".ljust(39)+   f"{doc}".rjust(40))
  print(f"Cliente:".ljust(39)+ f"{nombre} {apellido}".rjust(40))
  print(f"Vínculo:".ljust(39)   +  f"{vinculo}".rjust(40))
  print(f"Valor por boleta:".ljust(39) +f"${precio:,}".rjust(40))
  print("-"*80)
  print("Asientos reservados:")

  if cantidad == 0:
      print(" (No hay reservas registradas)")
  else:
      for a in asientos:
          print(f" ->{a}")

  print("-"*80)
  print(f"Cantidad de asientos: {cantidad}")
  print(f"TOTAL A PAGAR: ${total:,}")
  print("="*80)
  actualizar_csv(nombre_archivo)

#Función para validar el número que el usuario ingrese
def validar_numero(entrada):
  """
  Solicita un número de documento y valida que cumpla las restricciones:
  - Solo dígitos
  - Longitud entre 3 y 15 caracteres

  Args:
      entrada (str): Texto mostrado al pedir el número.

  Returns:
      int: Número validado.
  """
  while True:
    numero = input(f'{entrada}--->')
    if (not numero.isdigit()) or (not (3 <= len(numero) <= 15)):
      if (not numero.isdigit()) and (not (3 <= len(numero) <= 15)):   # verifica que solo haya dígitos | Preguntar si es posible usar esta función o debe ser de otra forma
        print(f"Error: el documento {numero} debe tener entre 3 y 15 dígitos y no tener letras ni simbolos.")
        continue
      elif not (3 <= len(numero) <= 15):
        print(f"Error: el documento {numero} debe tener entre 3 y 15 dígitos.")
        continue
      elif not numero.isdigit():
        print(f"Error: el documento {numero} solo debe contener numeros, no letras ni simbolos.")
        continue
    else:
      numero = int(numero)
      break
  return numero

#Función para validar la cadena que el usuario ingrese
def validar_string(entrada):
  """
  Solicita una cadena y valida que:
  - Tenga al menos 3 caracteres
  - No contenga dígitos

  Args:
      entrada (str): Etiqueta utilizada en el mensaje de entrada.

  Returns:
      str: Cadena validada.
  """
  while True:
    cadena = input(f'{entrada}--->')
    if len(cadena) < 3 or any(char.isdigit() for char in cadena): #Preguntar si se puede usar esa función
      if len(cadena) < 3 and any(char.isdigit() for char in cadena):
          print(f"Error: el {entrada}: < {cadena} > debe tener al menos 3 letras y no contener números.")
      elif len(cadena) < 3:
          print(f"Error: el {entrada}: < {cadena} > tiene {len(entrada)} letras, debe tener al menos 3.")
      elif any(char.isdigit() for char in cadena):
          print(f"Error: el {entrada}: < {cadena} > no debe contener números.")
      continue
    else:
      break
  return cadena

#Función para validar si el documento está registrado
def validar_documento(doc):
  """
  Verifica si un documento ya se encuentra registrado.

  Args:
      doc (int|str): Número de documento del usuario.

  Returns:
      bool: True si está registrado, False en caso contrario.
  """
  if doc in registrar_user:
      return True
  else:
      return False

#Función para agregar los datos del usuario en el diccionario
def registrar_usuario(doc, entrada):
  """
  Registra un nuevo dato asociado a un usuario en el diccionario registrar_user.

  Args:
      doc (int|str): Documento del usuario.
      entrada (str): Información que se va a guardar (nombre, apellido o vínculo).

  Returns:
      list: Lista actualizada de datos del usuario.
  """
  if doc not in registrar_user:
    registrar_user[doc] = []
  registrar_user[doc].append(entrada)
  return registrar_user[doc]

#Función para cancelar la reserva
def cancelar_reserva(lista_asiento, cinema, doc):
  """
  Cancela una reserva marcando el asiento como disponible ('O').

  Args:
      lista_asiento (list|tuple): Asiento en formato [fila, columna] con letras A-K.
      cinema (list): Matriz del cine.
      doc (int|str): Documento del usuario que realizó la reserva.

  Returns:
      list: Matriz del cine actualizada.

  Nota:
      También elimina el asiento reservado del diccionario registrar_reserva.
  """
  fila_letra = lista_asiento[0].upper()
  columna_letra = lista_asiento[1].upper()

  letras = "ABCDEFGHIJK"

  if fila_letra not in letras or columna_letra not in letras:
      print("Asiento inválido.")
      return cinema

  fila = letras.index(fila_letra)
  col = letras.index(columna_letra)

  if doc in registrar_reserva and (fila_letra + columna_letra) in registrar_reserva[doc]:
    registrar_reserva[doc].remove(fila_letra + columna_letra)
    if cinema[fila][col] == 'X':
      cinema[fila][col] = 'O'
      print(f'Ha cancelado correctamente el asiento{fila}{col}.')
    else:
      print("Usted no reservó ese asiento.")
  else:
    print("Usted no tiene reserva en este asiento.")

  return cinema

def total_reservas_registradas():
  """
  Calcula el total de reservas registradas en el sistema.

  Returns:
      int: Número total de reservas, sumando todas las listas asociadas
      a cada usuario en registrar_reserva.
  """
  return sum(len(v) for v in registrar_reserva.values())

def total_tiquetes_vendidos():
  """
  Calcula el total de tiquetes vendidos.

  Returns:
      int: Número total de tiquetes vendidos, equivalente a la suma de
      todas las reservas registradas.
  """
  return sum(len(i) for i in registrar_reserva.values())

def total_reservas_realizadas():
  """
  Obtiene la cantidad total de reservas realizadas por usuarios.

  Returns:
      int: Número de usuarios que han realizado al menos una reserva.
  """
  return len(registrar_reserva)

def total_pago_realizado():
  """
  Calcula el total del pago acumulado por todas las reservas registradas.

  El valor se determina multiplicando el número de reservas de cada usuario
  por el precio correspondiente a su tipo de usuario.

  Returns:
      int or float: Total pagado por todas las reservas.
  """
  total = 0
  for doc,reservas in registrar_reserva.items():
      precio = precios[ registrar_user[doc][2].lower()]
      total += len(reservas) * precio
  return total

def promedio_ventas_diario():
  """
  Calcula el promedio de tiquetes vendidos por usuario que ha realizado reservas.

  Returns:
      float: Promedio de tiquetes vendidos por usuario con reservas.
              Retorna 0 si no hay reservas registradas.
  """
  if len(registrar_reserva)==0:
      return 0
  total_asientos = total_tiquetes_vendidos()
  return total_asientos / len(registrar_reserva)

def lista_usuarios():
  """
  Imprime la lista de usuarios registrados con su nombre completo y tipo de usuario.

  Prints:
      str: Documento, nombres y tipo de cada usuario registrado en registrar_user.
  """
  for doc,datos in registrar_user.items():
      print(f"{doc}   --> {datos[0]} {datos[1]}   ({datos[2]})")

def reservasMayMen():
  """
  Identifica y muestra el usuario con más reservas y el usuario con menos reservas.

  Si no existen reservas registradas, imprime un mensaje indicándolo.

  Prints:
      str: Usuario con mayor número de reservas y usuario con menor número de reservas.
  """
  if not registrar_reserva:
      print("No hay reservas registradas.")
      return
  usuarios = list(registrar_reserva.keys())

  mayor_usuario = usuarios[0]
  menor_usuario = usuarios[0]

  for usuario in usuarios:

      cantidad = len(registrar_reserva[usuario])

      if cantidad > len(registrar_reserva[mayor_usuario]):
          mayor_usuario = usuario

      if cantidad < len(registrar_reserva[menor_usuario]):
          menor_usuario = usuario

  print("Usuario con más reservas:", mayor_usuario, len(registrar_reserva[mayor_usuario]))
  print("Usuario con menos reservas:", menor_usuario, len(registrar_reserva[menor_usuario]))


#Funcion para imprimir la cartelera
def imprimir_cartelera():
  """
  Imprime la cartelera disponible en Cibercinema UdeA con las funciones programadas para el fin de semana.
  Muestra:
  - Total de funciones programadas
  - Películas disponibles en cartelera
  - Horarios y disponibilidad de asientos por función

  """

  #Encabezado
  print('='*85)
  print('📽 CARTELERA DE CIBERCINEMA UDEA 📽'.center (85))
  print('='*85)
  print()

  #Información general
  print('🎞 Total de funciones programadas: 9')
  print('🙃 Películas en cartelera: 3')
  print()

  #Lista de peliculas en cartelera
  print('🎬😎 PELICULAS EN CARTELERA')
  print('='*85)
  print(' ° Orgullo y prejuicio')
  print(' ° El conjuro')
  print(' ° Mad Max:Fury Road')
  print()

  #Horarios
  print('📆 HORARIOS Y DISPONIBILIDAD:')
  print('-'*85)

  #Encabezados de la tabla
  print(f'{'IdPelicula':<12} {'Dia':<10} {'Hora':<10} {'Pelicula':<25}')
  print('-'*85)

#Datos de las funciones
  funciones = [
      (1, 'Viernes', '2pm', 'Orgullo y prejuicio'),
      (1, 'Viernes', '4pm', 'Orgullo y prejuicio'),
      (1, 'Viernes', '6pm', 'Orgullo y prejuicio'),
      (2, 'Sabado', '2pm', 'El conjuro'),
      (2, 'Sabado', '4pm', 'El conjuro'),
      (2, 'Sabado', '6pm', 'El conjuro'),
      (3, 'Domingo', '2pm', 'Mad Max:Fury Road'),
      (3, 'Domingo', '4pm', 'Mad Max:Fury Road'),
      (3, 'Domingo', '6pm', 'Mad Max:Fury Road')
  ]

  #Imprimir cada funcion
  for id_pelicula, dia, hora, pelicula in funciones:
      print(f'{id_pelicula:<12} {dia:<10} {hora:<10} {pelicula:<25}')
      print('='*85)

```

## **Código principal**

Este módulo constituye el punto de entrada principal del programa, donde se ejecuta el menú interactivo que permite al usuario navegar entre las diferentes secciones y funcionalidades del sistema.


```python
import datetime
#Mensaje de bienvenida
letrero = """
          ██████╗ ██╗███████╗███╗   ██╗██╗   ██╗███████╗███╗   ██╗██╗██████╗  ██████╗ ███████╗     █████╗
          ██╔══██╗██║██╔════╝████╗  ██║██║   ██║██╔════╝████╗  ██║██║██╔══██╗██╔═══██╗██╔════╝    ██╔══██╗
          ██████╔╝██║█████╗  ██╔██╗ ██║██║   ██║█████╗  ██╔██╗ ██║██║██║  ██║██║   ██║███████╗    ███████║
          ██╔══██╗██║██╔══╝  ██║╚██╗██║╚██╗ ██╔╝██╔══╝  ██║╚██╗██║██║██║  ██║██║   ██║╚════██║    ██╔══██║
          ██████╔╝██║███████╗██║ ╚████║ ╚████╔╝ ███████╗██║ ╚████║██║██████╔╝╚██████╔╝███████║    ██║  ██║
          ╚═════╝ ╚═╝╚══════╝╚═╝  ╚═══╝  ╚═══╝  ╚══════╝╚═╝  ╚═══╝╚═╝╚═════╝  ╚═════╝ ╚══════╝    ╚═╝  ╚═╝

 ██████╗██╗██████╗ ███████╗██████╗  ██████╗██╗███╗   ██╗███████╗███╗   ███╗ █████╗     ██╗   ██╗██████╗ ███████╗ █████╗
██╔════╝██║██╔══██╗██╔════╝██╔══██╗██╔════╝██║████╗  ██║██╔════╝████╗ ████║██╔══██╗    ██║   ██║██╔══██╗██╔════╝██╔══██╗
██║     ██║██████╔╝█████╗  ██████╔╝██║     ██║██╔██╗ ██║█████╗  ██╔████╔██║███████║    ██║   ██║██║  ██║█████╗  ███████║
██║     ██║██╔══██╗██╔══╝  ██╔══██╗██║     ██║██║╚██╗██║██╔══╝  ██║╚██╔╝██║██╔══██║    ██║   ██║██║  ██║██╔══╝  ██╔══██║
╚██████╗██║██████╔╝███████╗██║  ██║╚██████╗██║██║ ╚████║███████╗██║ ╚═╝ ██║██║  ██║    ╚██████╔╝██████╔╝███████╗██║  ██║
 ╚═════╝╚═╝╚═════╝ ╚══════╝╚═╝  ╚═╝ ╚═════╝╚═╝╚═╝  ╚═══╝╚══════╝╚═╝     ╚═╝╚═╝  ╚═╝     ╚═════╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝

"""

#Esqueleto del código principal
cinema = crear_cinema()

while True:
    print(letrero)
    print(menu_p())
    menu = input('\nIngrese la opción que desee--->')

    match menu:
        case '1':
        #Registrar usuario

          print('\nPROCESO DE REGISTRO\n')
          while True:

            doc = validar_numero('Documento')
            if validar_documento(doc):
              print(f'\n¡AVISO!: el documento {doc} ya se encuentra registrado en el sistema, inténtelo de nuevo\n')
              continue
            else:
              name = validar_string('Nombre')
              registrar_usuario(doc,name)
              lname = validar_string('Apellido')
              registrar_usuario(doc,lname)

              while True:
                  print('''
|  VINCULO CON LA UDEA  |  PRECIO BOLETA  |
|-----------------------|-----------------|
|1. Estudiante          |           $7,500|
|2. Docente             |          $10,000|
|3. Administrativo      |           $8,500|
|4. Oficial interno     |           $7,000|
|5. Publico externo     |          $15,000|
                  ''')
                  vin = input('\nIngrese su Vínculo--->')
                  if vin in ['1','2','3','4','5']:
                      vin = int(vin)-1
                      vin = vinculo[vin]
                      registrar_usuario(doc,vin)
                      break

                  else:
                      print(f'{vin} no es un vínculo válido. Por favor agregue el correcto')
              break
          print('\nProcesando información...')
          print('¡Usuario registrado exitosamente!\n')

          #print(registrar_user[doc])

        case '2':
            #Registrar reserva
            print('\nREGISTRAR RESERVA\n')
            doc = validar_numero('Documento')

            if not validar_documento(doc):
              print(f'\n¡AVISO!: el documento {doc} no se encuentra registrado en el sistema. Ir a la opción 1 del menú.\n')
              continue

            # Mostrar información del usuario
            if validar_documento(doc):
              imprimir_sala_cine(cinema)

              # Proceso de reserva
              while True:
                    asiento = input("Ingrese el asiento a reservar (ejemplo: AA, BC, KJ) o '0' para terminar: ").upper().strip()

                    if asiento == '0':
                        factura(doc)

                        break

                    # Validar que el formato es exactamente 2 letras
                    elif len(asiento) > 2 or not asiento.isalpha():
                        print("Error: recuerde que el formato válido solo son 2 letras y sin caracteres especiales (ej: AA, BK, CJ)")
                        continue

                    # Pasar asiento como lista de letras
                    lista_asiento = list(asiento)

                    # Llamamos la función guardar reserva
                    guardar_reserva(lista_asiento, cinema)

                    # Llamamos la función para ver la sala actualizada
                    imprimir_sala_cine(cinema)


        case '3':
            print('\nCANCELAR RESERVA\n')
            doc = validar_numero('Documento')

            if not validar_documento(doc):
                print(f"\n¡AVISO!: el documento {doc} no está registrado.\n")
                continue

            # Mostrar reservas actuales
            print("\nSus reservas actuales:")
            imprimir_sala_cine(cinema)

            while True:
                asiento = input("Ingrese el asiento a cancelar o '0' para terminar: ").upper()

                if asiento == '0':
                    print("Asiento eliminado con éxito")
                    actualizar_csv(nombre_archivo)

                    break

                if len(asiento) != 2 or not asiento.isalpha():
                    print("Formato inválido.")
                    continue

                lista_asiento = list(asiento)

                cinema = cancelar_reserva(lista_asiento, cinema, doc)

                # Mostrar sala actualizada
                imprimir_sala_cine(cinema)



        case '4':
        #Consultar funciones fin de semana
            print('\nFUNCIONES FIN DE SEMANA\n')
            imprimir_cartelera()

        case '5':
        #Administrador
            print('\nADMINISTRADOR/A\n')
            validar_admin('Usuario','Constraseña')
            while True:
              print(menu_a())
              m_a = input('\nIngrese la opción que desee--->')
              match m_a:
                case '1':
                    print("\nTOTAL RESERVAS REGISTRADAS:")
                    print(total_reservas_registradas(), '\n')
                case '2':
                    print("\nTOTAL TIQUETES VENDIDOS:")
                    print(total_tiquetes_vendidos(), '\n')
                case '3':
                    print("\nTOTAL RESERVAS REALIZADAS:")
                    print(total_reservas_realizadas(), '\n')
                case '4':
                    print("\nTOTAL PAGO REALIZADO:")
                    print(f"${total_pago_realizado():,}", '\n')
                case '5':
                    print("\nPROMEDIO POR VENTA:")
                    print(f"{promedio_ventas_diario():.2f}", '\n')
                case '6':
                    print("\nLISTA DE USUARIOS:\n")
                    lista_usuarios()
                    print()
                case '7':
                    reservasMayMen()

                case '8':
                  break
                case _:
                  print('\nHa ingresado un valor incorrecto, inténtelo de nuevo')
                  continue

        case '6':
        #Salir

            break

        case _:
            print('\nHa ingresado un valor incorrecto, inténtelo de nuevo')
            continue
```

    
              ██████╗ ██╗███████╗███╗   ██╗██╗   ██╗███████╗███╗   ██╗██╗██████╗  ██████╗ ███████╗     █████╗ 
              ██╔══██╗██║██╔════╝████╗  ██║██║   ██║██╔════╝████╗  ██║██║██╔══██╗██╔═══██╗██╔════╝    ██╔══██╗
              ██████╔╝██║█████╗  ██╔██╗ ██║██║   ██║█████╗  ██╔██╗ ██║██║██║  ██║██║   ██║███████╗    ███████║
              ██╔══██╗██║██╔══╝  ██║╚██╗██║╚██╗ ██╔╝██╔══╝  ██║╚██╗██║██║██║  ██║██║   ██║╚════██║    ██╔══██║
              ██████╔╝██║███████╗██║ ╚████║ ╚████╔╝ ███████╗██║ ╚████║██║██████╔╝╚██████╔╝███████║    ██║  ██║
              ╚═════╝ ╚═╝╚══════╝╚═╝  ╚═══╝  ╚═══╝  ╚══════╝╚═╝  ╚═══╝╚═╝╚═════╝  ╚═════╝ ╚══════╝    ╚═╝  ╚═╝
    
     ██████╗██╗██████╗ ███████╗██████╗  ██████╗██╗███╗   ██╗███████╗███╗   ███╗ █████╗     ██╗   ██╗██████╗ ███████╗ █████╗ 
    ██╔════╝██║██╔══██╗██╔════╝██╔══██╗██╔════╝██║████╗  ██║██╔════╝████╗ ████║██╔══██╗    ██║   ██║██╔══██╗██╔════╝██╔══██╗
    ██║     ██║██████╔╝█████╗  ██████╔╝██║     ██║██╔██╗ ██║█████╗  ██╔████╔██║███████║    ██║   ██║██║  ██║█████╗  ███████║
    ██║     ██║██╔══██╗██╔══╝  ██╔══██╗██║     ██║██║╚██╗██║██╔══╝  ██║╚██╔╝██║██╔══██║    ██║   ██║██║  ██║██╔══╝  ██╔══██║
    ╚██████╗██║██████╔╝███████╗██║  ██║╚██████╗██║██║ ╚████║███████╗██║ ╚═╝ ██║██║  ██║    ╚██████╔╝██████╔╝███████╗██║  ██║
     ╚═════╝╚═╝╚═════╝ ╚══════╝╚═╝  ╚═╝ ╚═════╝╚═╝╚═╝  ╚═══╝╚══════╝╚═╝     ╚═╝╚═╝  ╚═╝     ╚═════╝ ╚═════╝ ╚══════╝╚═╝  ╚═╝
                                                                                                                                                                                                                                                                                                                                                      
    
    
    
    MENU PRINCIPAL
    
    1. Registrar usuario
    2. Registrar reserva
    3. Cancelar reserva
    4. Consultar funciones fin de semana
    5. Administrador
    6. Salir
    
    
    Ingrese la opción que desee--->6
    
