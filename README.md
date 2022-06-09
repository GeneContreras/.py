# .py
Proyecto orientado a la venta de pasajes de Vuelos DUOC


#En este apartado, las variables simulan una matriz de 7x6. 
#Cada uno de los siete elementos posee seis números (entre el 1 y el 42), los cuales son agrupados de forma creciente sin que se repita ningún valor.
#Las variables son distribuídas de la siguiente manera: asientos = ([1,2,3,4,5,6] , [7,8,9,10,11,12] , [13,14,15,16,17,18] , [19,20,21,22,23,24] , [25,26,27,28,29,30] , [31,32,33,34,35,36] , [37,38,39,40,41,42])
#Es preciso señalar, que los asientos no disponibles aparecen predeterminados en el ejercicio. Por lo anterior, estos son reemplazados con una X.

asientos = ([1,2,3,4,5,6],
            [7," x"," x ",10,11,12],
            ["x ","x ","x ",16,"x ",18],
            [19,20,21,22,23,24],
            [25,26,27,"x ",29,30],
            ["x ",32,33,34,35,36],
            ["x ",38,"x ",40,41,"x "])

#En esta lista se guardarán los datos del pasajero.
#Donde aparece el número 0, irán los datos del teléfono, rut y asiento. 
#Lo anterior no permitirá que se ingresen caracteres que no sean números, tal como se describe a continuación: [NOMBRE(str), RUT(int), TELEFONO(int), BANCO(str), ASIENTO_SELECCIONADO(int)]

pasajero = ["",0,0,"",0]

#En esta lista se permite guardar la coordenada del asiento seleccionado (elemento,número de asiento)

asiento=[0,0]

#FUNCIONES
    
def consultar(): #Esta función permite mostrar la matriz como se escribió en el primer apartado. Después del pasaje número 30, se escribe una línea que categoriza los pasajes normales y los VIP.
 for i in range(0,7):
   if i == 0: #Aquí se escribe esta linea por separado, dado que los asientos 1,2,3,4,5 y 6 sólo tienen un dígito y en conjunto con los espacios agregados es posible mostrar el menú de manera ordenada.
     print("| ",asientos[i][0],"  ",asientos[i][1],"  ",asientos[i][2]," ","     ",asientos[i][3],"  ",asientos[i][4],"  ",asientos[i][5]," |")
   if i == 1: #Aquí se escribe esta linea por separado, dado que los asientos 7, x y x sólo tienen un dígito y en conjunto con los espacios agregados es posible mostrar el menú de manera ordenada.
     print("| ",asientos[i][0]," ",asientos[i][1]," ",asientos[i][2]," ","    ",asientos[i][3]," ",asientos[i][4]," ",asientos[i][5],"|")
   if i == 5: #Esta condición se agregó sólo para que se dibuje el separador de los tipos de pasajes en la quinta línea que correspondía.
     print("|_______________     _______________|")   
   if i >1 and i < 7: #Desde la línea 2 en adelante, se escriben los valores de manera creciente.
     print("| ",asientos[i][0]," ",asientos[i][1]," ",asientos[i][2]," ","    ",asientos[i][3]," ",asientos[i][4]," ",asientos[i][5],"|")   
      
def mostrar():  #Esta función permite mostrar los datos del pasajero.
    
    print("__________________________")
    print("NOMBRE   :",pasajero[0])
    print("RUT      :",pasajero[1])
    print("TELEFONO :",pasajero[2])
    print("BANCO    :",pasajero[3])
    print("__________________________")
    print("")

    
def datos_pasajero(): #Esta función permite ingresar y corroborar los datos del pasajero

    rut=True        #Flags para los while
    telefono=True
    
    pasajero[0]=input("INGRESE SU NOMBRE: ") #Se asigna el input NOMBRE al primer valor de la lista PASAJERO
    
    while rut:
        try:
            pasajero[1]=int(input("INGRESE SU RUT (sin CV ni puntos: ")) #Se asigna el input RUT el segundo valor de la lista PASAJERO.
        except ValueError:  #El valor que se solicita ingresar es un número (int). Si se ingresa cualquier otro caracter lo considera como VALUE ERROR y desplegará el siguiente mensaje:
            print("DATO INVALIDO")
        else:
            if pasajero[1]<5000000 or pasajero[1]>25000000: #esto comprueba si el rut está entre los 5 y 25 millones
                print("DATO INVALIDO")
            else:   #si no salta ningun error, sale del while, sino sigue dentro del loop hasta que se ingrese un dato valido
                rut=False
                
    while telefono: #Se asigna el input TELEFONO al tercer valor de la lista PASAJERO. Además se valida que ingrese los 8 dígitos.
        
        try:
            pasajero[2]=int(input("INGRESE SU TELEFONO: "))
        except ValueError:
            print("DATO INVALIDO")
        else:
            if pasajero[2]<9999999 or pasajero[2]>99999999:
                print("DATO INVALIDO")
            else:
                telefono=False
                
    pasajero[3]=input("INGRESE SU BANCO: ") #Se asigna el input BANCO al cuarto valor de la lista PASAJERO.
   
    mostrar() #Con esta función se muestra el registro de los datos ingresados.
     
def comprar(): #Esta funcion ejecuta la compra y sustituye el número del asiento por una X.
  
    compra=True
    while compra:
        try:
            asiento_seleccionado=int(input("SELECCIONE SU ASIENTO: ")) #Se valida que ASIENTO sea número y que esté dentro de los rangos correspondientes (1 y 42).
        except ValueError:
            print("ASIENTO INVALIDO")
        else:
            if asiento_seleccionado > 42 or asiento_seleccionado < 1: #Si ASIENTO está fuera del rango no es válido y se despliega el siguiente mensaje:
                print("ASIENTO INVALIDO")
            elif asiento_seleccionado == pasajero[4]: #Si el asiento seleccionado ya se compró, se despliega el siguiente mensaje:
                print("ASIENTO NO DISPONIBLE")
                compra=False
            else:             
                for i in range(0,7): #Este for se usa para ir de fila en fila
                    for c in range (0,6): #Este for se usa para ir de numero en numero detro de cada fila
                        if asientos[i][c] == asiento_seleccionado: #Aquí se valida si el valor del numero en la fila que se esta leyendo es igual al ASIENTO que ingresó el usuario.
                            if asiento_seleccionado>30: 
                                print("ASIENTO VIP") #Si el número de asiento es mayor que 30 y menor o igual a 42, imprime el mensaje "ASIENTO VIP".
                                valor=240000 #precio
                            else:
                                print("ASIENTO NORMAL") #Si el número de asiento es menor o igual a 30, imprime el mensaje "ASIENTO NORMAL".
                                valor=74900 #Valor del pasaje
                            print("VALOR PASAJE: ",valor)
                            print("")
                            aceptar=input("DESEA COMPRAR ESTE ASIENTO? (Y para confirmar) ")
                            if aceptar == "y" or aceptar == "Y":
                                print("EL ASIENTO HA SIDO SELECCIONADO")
                                    
                                if pasajero[4]!=0:  #Se reestablece el asiento antes comprado para que no se quede con una X y lo reescribe con el anterior numero de asiento guardado. SOLO SI YA SE COMPRO UN PASAJE.
                                    x = asiento[0]
                                    y = asiento[1]
                                    asientos[x][y]= pasajero[4] #Reescribe el asiento donde antes se puso una X
                                
                                asientos[i][c]="x" #Se eemplaza el numero de la fila en la fila seleccionada por la X
                                asiento[0]= i #Guarda las coordenadas de la matriz
                                asiento[1]= c
                                pasajero[4]=asiento_seleccionado #Guarda asiento comprado en lista PASAJERO        
                            compra=False #Sale del while                         
                                
    if pasajero[3]=="bancoDUOC":    #Comprueba si el BANCO del usuario es igual a bancoDUOC y le descuenta 15% desplegando el siguiente mensaje:
        print("")
        print("FELICIDADES! TIENES UN 15% POR PERTENER A BANCO DUOC!")
        print("VALOR ANTES: ",valor) #Muestra valor original
        valor=valor*0.85 #Descuenta -15%
        print("VALOR PASAJE: ",valor) #Muestra valor final aplicado el descuento


def anular(): #Esta función reemplaza la X de la matriz por el numero del asiento y reescribe los datos del pasajero.
    opcion=True    
    while opcion:
        seleccion=input("DESEA ANULAR SU PASAJE? Y/N ") #Pregunta si desea anular el pasaje.
        if seleccion == "y" or seleccion == "Y": #Si escribe y o Y continúa la anulación.
            x = asiento[0]
            y = asiento[1]
            asientos[x][y]= pasajero[4] #Reescribe el asiento donde antes se puso una X.
            pasajero[0]= "" #Reestablece la lista de pasajeros.
            pasajero[1]= 0
            pasajero[2]= 0
            pasajero[3]= ""
            pasajero[4]= 0
            mostrar()
            opcion=False #Sale del while
        elif seleccion == "n" or seleccion == "N": #Si escribe n o N, se despliega el mensaje agradeciendo la preferencia.
            print("MUCHAS GRACIAS POR SU PREFERENCIA")
            opcion=False
        else:
            print("SELECCION INVALIDA") #Valida que el usuario escriba lo que se solicitó. (Y, y, N ó n) Si no aplica, no terminará el ciclo.        

def modificar(): #Esta función permite reescribir el NOMBRE(pasajero[0]) y y/o el TELEFONO(pasajero[2] solo si se ingresa el NOMBRE y el ASIENTO correctamente.  
    dato=True
    while dato:
        try:
            dato1= int(input("INGRESE SU ASIENTO ")) #Pregunta por el número de asiento(int). Si ingresa otro carácter que no sea número, la operación será inválida.
        except ValueError:
            print("DATO INVALIDO")
        else:
            dato=False
    dato2= input("INGRESE SU NOMBRE ") #Pregunta por nombre(str). 
    if dato1 == pasajero[4] and dato2 == pasajero[0]: #Valida que los datos ingresados coincidan con lo de la lista PASAJERO.
        print("VALIDACION EXITOSA!")
        opcion=True
        while opcion: #Si los datos conciden, entra a esta while que es un menu de seleccion (se copiaron las mismas lineas de COMPRAR() para ingresar y validar los datos). 
            print("1.NOMBRE PASAJERO")
            print("2.TELEFONO PASAJERO")
            print("3.CANCELAR")
            seleccion=input("SELECCIONE DATO A MODIFICAR ")
            if seleccion == "1": #Opción nombre
                pasajero[0]=input("INGRESE SU NOMBRE: ")
            elif seleccion == "2": #Opción telefono
                telefono=True
                while telefono:
                    try:
                        pasajero[2]=int(input("INGRESE SU TELEFONO: ")) #Si ingresa un caracter tipo str la operación es inválida. Debe ingresar 8 dígitos numéricos.
                    except ValueError:
                        print("DATO INVALIDO")
                    else:
                        if pasajero[2]<9999999 or pasajero[2]>99999999:
                            print("DATO INVALIDO")
                        else:
                            telefono=False
            elif seleccion == "3":
                opcion=False   #Opción cancelar
            else:
                print("SELECCION INVALIDA") #Si no selecciona alguna de las opciones que corresponda (1,2 ó 3)

        mostrar()        
    else:
        print("VALIDACION FALLIDA") #La operación no es válida si no coinciden el NOMBRE y el número de ASIENTO ingresados con los guardados.


#MENU PRINCIPAL

print("____________________________")
print("BIENVENIDO A VUELOS DUOC")
print("____________________________")

master=True
while master:
    print("1. VER ASIENTOS DISPONIBLES")
    print("2. COMPRAR ASIENTO")
    print("3. ANULAR VUELO")
    print("4. MODIFICAR DATOS DE PASAJERO")
    print("5. SALIR")
    print("")
    menu=input("SELECCIONE UNA OPCION:")   
    if menu=="1": #Sólo muestra la matriz
        consultar()
        print("")
    elif menu=="2": #Ingresa datos de pasajero, muestra sus datos y pregunta por el asiento a comprar
        datos_pasajero()
        comprar()
        print("")

    elif menu=="3": #Borra los cambios realizados
        if pasajero[4]!=0:
            anular()
            print("")
        else:
            print("NO TIENE ASIENTO COMPRADO")

    elif menu=="4": #Reescribe NOMBRE o TELEFONO
        if pasajero[4]!=0:
            modificar()
            print("")
        else:
            print("NO TIENE ASIENTO COMPRADO")

    elif menu=="5":   #Salir
        print("MUCHAS GRACIAS POR SU PREFERENCIA")
        master=False
    else:
        print("SELECCION INVALIDA") #Si no ingresa los valores señalados, la operación no puede ser realizada.
