# Concurrencia en Python

## Video Clase 2 - Codigo Fuente
```
procesosEjemplo.py
procesosEjemplo2.py
threadsEjemplo.py
globalVarsEjemplo.py
globalContador.py
```

## Ejercicio:

```
textoAnimado.py
```
El siguente programa, utiliza el [Interfaces gráficas de usuario Tk (tkinter)](https://docs.python.org/es/3/library/tk.html) para generar animaciones de texto.
Las animaciones consisten en un caracter que se repite a lo largo de una línea, a una determinada velocidad.

Leer y analizar el código y tratar de deducir que hace cada bloque.

## Preguntas (responder en el campus):

1. Como podría modidificar el caracter a imprimir en las lineas animadas?
Modificando la linea de llamado. 
Ejemplo: 
crearAnimacion(10,10, 'X') <-- en esa linea se le pasa el caracter a imprimir y la posicion de colocacion.
Si quisiera imprimir O en lugar de X seria: crearAnimacion(10,10, 'O')
2. Como podría modificar la velocidad a la que se escriben los caracteres?
Modificando el tiempo de retardo que es 0.25 por un numero menor.
Ejemplo:
retardo: float=0.10 
3. Las animaciones de esta versión se ejecutan en forma Secuencial: explique por que.
Es un ejercicio secuencial, no es concurrente.
4. Modificar el código de modo que las animaciones se ejecuten en forma concurrente utilizando Threads.
#Ejecuta tres animaciones
#crearAnimacion(10,10, 'X')
#crearAnimacion(10,30, 'Y')
#crearAnimacion(10,50, 'Z')

thread_1 = threading.Thread(target=crearAnimacion, args=(10,10,"X",))
thread_2 = threading.Thread(target=crearAnimacion, args=(10,30,"Y",))
thread_3 = threading.Thread(target=crearAnimacion, args=(10,50,"Z",))

thread_1.start()
thread_2.start()
thread_3.start()
5. Como modificaría el código para utiliar Procesos en lugar de Threads. Que diferencias habría al ejecutarlo?
   Bonus: Implementar el punto 5 en codigo que funcione.
   Para que el codigo utilice procesos se pone:
   if __name__ == '__main__':
    animacionX = multiprocessing.Process(target=crearAnimacion, args=(10,10,"X",))
    animacionY = multiprocessing.Process(target=crearAnimacion, args=(10,30,"Y",))
    animacionZ = multiprocessing.Process(target=crearAnimacion, args=(10,50,"Z",))

    animacionX.start()
    animacionY.start()
    animacionZ.start()
   Lo que crea esto es que se abran 4 ventanas, 3 para cada animacion y 1 para el programa, y cada animacion se corra en su ventana correspondiente.

   Para que el codigo funcione correctamente se impolementa run():
   if __name__ == '__main__':
    animacionX = multiprocessing.Process(target=crearAnimacion, args=(10,10,"X",))
    animacionY = multiprocessing.Process(target=crearAnimacion, args=(10,30,"Y",))
    animacionZ = multiprocessing.Process(target=crearAnimacion, args=(10,50,"Z",))

    animacionX.run()
    animacionY.run()
    animacionZ.run()



<sub>[Daniel Buaon - unahur-progra-concu-1-2021](https://github.com/unahur-progra-concu-1-2021)</sub>
