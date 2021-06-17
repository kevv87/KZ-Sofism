## Info
Librería numérica de [[C++]].
Otra info en el PDF.

## Operaciones
### Conversión a double
Para convertir una expresión a double, primero hay que verificar que sea una expresión numérica, siendo así se castea a numérico y luego a double.
```c++
if(is_a<numeric>(f)){
  double d = ex_to<numeric>(f).to_double();
}
```

## Compilar 
Para compilar programas que utilizan esta librería, [[Matplotlibcpp]] y [[CLN]], se utiliza el comando (Última revisión Mie 12 abr, con Python 3.9):
```
g++ biseccion.cpp -lginac -lcln -std=c++11\
                  -I/usr/local/Cellar/python@3.9/3.9.4/Frameworks/Python.framework/Versions/3.9/include/python3.9\
                  -D WITHOUT_NUMPY\
                  -L/usr/local/Cellar/python@3.9/3.9.4/Frameworks/Python.framework/Versions/3.9/lib\
                  -lpython3.9\
                  -lpthread -lutil -ldl\
                  -rdynamic
```

### Explicación del comando de compilación
- Inicialmente se especifica el archivo a compilar
- Luego se cargan las librerías
	- Estas librerías deben estar presentes en /usr/local/lib
- Luego se le dice qué versión de c++ usamos
- Se procede a especificar la ubicación del header de [[Python]] `Python.h`
	- La ubicación en el ejemplo es la de *Mac*
- Se le dice que ignore [[Numpy]] con `-D WITHOUT_NUMPY`
- Luego se le tiene que especificar la ubicación de la librería `libpython3.9.so`
	- En un sistema normal de linux no es necesario ubicarla, sin embargo en [[MacOs]] sí y está instalada en la dirección que se pone de ejemplo.
- Luego se le especifica que cargue unas librerías que se supone que tienen que venir en la librería `libpython3.9.so`, pero que *algunas veces no se incluyen*, entonces para evitar inconvenientes se meten manualmente.
- Por último, *en el caso de Mac y de algunos otros sitemas operativos* la librería de Python no tiene el formato `.so`, si no `.dydl` o `.a`, *si este es el caso* se debe especificar al linker que son *librerías dinámicas* y se realiza mediante la opción `-rdynamic`