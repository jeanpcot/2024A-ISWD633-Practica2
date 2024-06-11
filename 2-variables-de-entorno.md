# Variables de Entorno
### ¿Qué son las variables de entorno
Son variables que utiliza ese contenedor de docker para funcionar. Existen casos que no sirven los contendores si no definen las variables

### Para crear un contenedor con variables de entorno
```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

docker run -d --name nginxContainer -e username=admin -e role=admin -p 80:80 nginx

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
![image](https://github.com/jeanpcot/2024A-ISWD633-Practica2/assets/161987855/8eefe7f7-bba6-4f71-a8fc-db0b66397d6d)
![image](https://github.com/jeanpcot/2024A-ISWD633-Practica2/assets/161987855/a6095bc2-479b-4d10-b783-d794f1e029d8)


### Crear un contenedor con mysql:8 , mapear todos los puertos
# COMPLETAR
![image](https://github.com/jeanpcot/2024A-ISWD633-Practica2/assets/161987855/ca1b6f5d-de09-4c3a-8b10-eb2e10ab31cb)

### ¿El contenedor se está ejecutando?
No 

### Identificar el problema
No estan definidas las variables de entorno

### Eliminar el contenedor creado con mysql:8 
docker rm msql

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
docker run -d --name msql --env-file=varEntorno.env -P mysql:8

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR 
![image](https://github.com/jeanpcot/2024A-ISWD633-Practica2/assets/161987855/ec08f232-a265-4b73-9e7f-4774d2b0c06a)


### ¿Qué bases de datos existen en el contenedor creado?
![image](https://github.com/jeanpcot/2024A-ISWD633-Practica2/assets/161987855/428ea588-68ec-41ca-86d6-38b8ea0c11b6)
