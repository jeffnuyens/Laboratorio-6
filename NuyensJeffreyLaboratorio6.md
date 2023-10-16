### Título: Laboratorio 6
### Autor: Jeffrey Nuyens
### Carnet: 20210420
### Fecha: 2023-10-15


```python
import re
```

### 1. Genere una expresión regular que sea capaz de detectar las placas de un vehículo particular guatemalteco.


```python
string_placas = "P407BTJ PABC123 P516DJH P492GZC"
pattern_placas = r"P[0-9]{3}[BCDFGHJKLMNPQRSTVWXYZ]{3}"
result = re.findall(pattern_placas, string_placas)
print("Placas de vehículos particulares guatemaltecos:", result)
```

    Placas de vehículos particulares guatemaltecos: ['P407BTJ', 'P516DJH', 'P492GZC']


### 2.	Genere una expresión regular que valide si un archivo es de tipo .pdf o jpg. 
### a.	Ejemplo1.pdf, prueba2.PDF, respuestas_del_examen.jpg, amor.JPG



```python
string_archivos = "Ejemplo1.pdf prueba2.PDF respuestas_del_examen.jpg amor.JPG"
pattern_archivos = r"([\w-]+(?:\.pdf|\.jpg|\.PDF|\.JPG)\b)"
result = re.findall(pattern_archivos, string_archivos)
print("Archivos válidos de tipo .pdf o .jpg:", result)
```

    Archivos válidos de tipo .pdf o .jpg: ['Ejemplo1.pdf', 'prueba2.PDF', 'respuestas_del_examen.jpg', 'amor.JPG']


### 3.	Genere una expresión regular para validar contraseñas de correo. Una contraseña de correo debe contener por lo menos 8 caracteres, una letra mayúscula y un carácter especial.


```python
string_pass = "Contrasena1! abcDEF1234$ myPass#"
pattern_pass = r"(?=.*[A-Z])(?=.*[!@#$%^&*])[A-Za-z\d!@#$%^&*]{8,}"
result = re.findall(pattern_pass, string_pass)
print("Contraseñas válidas de correo:", result)
```

    Contraseñas válidas de correo: ['Contrasena1!', 'abcDEF1234$']


### 4.	Cree una expresión regular para validar un numero de carnet de la Universidad Galileo, por ejemplo 19002324 donde los primeros dos dígitos representan el año en el que el alumno se inscribió los cuales pueden variar desde el 01 (año 2001) hasta el 30 (año 2030). Los siguientes dos dígitos son cero (00) los cuales van por default y los últimos cuatro dígitos son un número que va desde el 1110 hasta el 8970. Para dar su respuesta utilice la notación de expresiones regulares.


```python
pattern_carnet = r"\b(?:0[1-9]|1[0-9]|2[0-9]|30)00(?:11[1-9][0-9]|1[2-9][0-9]{2}|[2-7][0-9]{3}|8[0-8][0-9]{2}|89[0-6][0-9]|8970)\b"
string_carnet = "19002324 15001110 29008970 31001234"
result = re.findall(pattern_carnet, string_carnet)
print("Carnets Universidad Galileo:", result)
```

    Carnets Universidad Galileo: ['19002324', '15001110', '29008970']


### 5.	Cree una expresión regular que encuentre todas las palabras de la primera línea, pero ninguna de la segunda.
### a.	pit, spot, spate, slap two, respite
### b.	pt,Pot,peat,part



```python
string_texto = "pit, spot, spate, slap two, respite, pt, Pot, peat, part"
pattern_texto = r'\b(?:(?!pt|Pot|peat|part)\w)+\b(?=[^,]*,)'
result = re.findall(pattern_texto, string_texto)
print("Palabras de la primera línea:", result)
```

    Palabras de la primera línea: ['pit', 'spot', 'spate', 'slap', 'two', 'respite']


### 6.	Cree una expresión regular para obtener los números telefónicos de Guatemala. Estos pueden contener al inicio +502 o 502, pueden estar separados por un espacio en blanco o un guión o juntos. Notar que los números telefónicos pueden empezar únicamente con 4,5,6 o 2.
### a.	+50254821151, 4210-7640, 52018150, 2434 6854, 11234569, 50211234578



```python
string_telefonos = "+50254821151, 4210-7640, 52018150, 2434 6854, 11234569, 50241234578"
pattern_telefonos = r'(?:502|\+502)?[4562]\d{2,3}[\s-]?\d{4}'
resultados_telefonos = re.findall(pattern_telefonos, string_telefonos)
print("Números telefónicos de Guatemala:", resultados_telefonos)
```

    Números telefónicos de Guatemala: ['+50254821151', '4210-7640', '52018150', '2434 6854', '50241234578']


### 7.	Genere una expresión regular que sea capaz de obtener correos de la UFM.


```python
string_ufm = "correo1@ufm.edu correo2@ejemplo.com correo3@ufm.edu"
pattern_ufm = r"\b[\w\.-]+@ufm\.edu\b"
result = re.findall(pattern_ufm, string_ufm)
print("Correos de la UFM:", result)
```

    Correos de la UFM: ['correo1@ufm.edu', 'correo3@ufm.edu']


### 8.	En el mundo distópico de Eurasia, Big Brother le asigna un identificador único a cada ciudadano. Genere una expresión regular que valide las identificaciones. Composición del id:
### a.	El id inicia con 0 a 3 letras minúsculas (puede tener 0 letras minúsculas hasta tres letras minúsculas)
### b.	Luego es seguido por una cadena de dígitos que puede ser de 2 a 9 dígitos respectivamente.
### c.	Inmediatamente después de la cadena de dígitos, se encuentra por lo menos tres letras mayúsculas.
### d.	Ej: abc012333ABCDEEEE



```python
string_id = "abc012333ABCDEEEE xyz987654FGHFFFFF pqr1234ABCDER"
pattern_id = r"[a-z]{0,3}\d{2,9}[A-Z]{3,}"
result = re.findall(pattern_id, string_id)
print("Identificador de ciudadano en Eurasia:", result)
```

    Identificador de ciudadano en Eurasia: ['abc012333ABCDEEEE', 'xyz987654FGHFFFFF', 'pqr1234ABCDER']

