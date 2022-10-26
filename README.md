
# Laboratorio CI/CD

## Integrantes: Santiago Ospina, Isabella Manrique

## Ejercicio 1
Primero, en [Azure portal](https://portal.azure.com/#home), abriremos
el Azure Cloud Shell que nos servira como terminal.

![](Resources/1.png)

Luego, podremos desplegar un grupo de recursos con el siguiente comando:
```
az group create --name ResourceGroup --location westus
```
![](Resources/2.png)

Ahora crearemos una App Service Plan con el siguiente comando:
```
az appservice plan create --resource-group ResourceGroup --name MyPlan --sku S1
```
![](Resources/3.png)

Para crear una Web App, insertaremos el siguiente comando. El nombre debe ser unico:
```
az webapp create --resource-group ResourceGroup --plan MyPlan --name WebAppCVDS
```
![](Resources/4.png)

Y por ultimo crearemos el servidor de MySQL con un nombre unico
```
az mysql server create --resource-group ResourceGroup --name mySQLserverCVDS --admin-user mysqldbuser --admin-password P2ssw0rd@123 --sku-name GP_Gen5_2
```

Ahora podremos ver en los recursos el servidor que creamos.

![](Resources/5.png)

Es importante que podamos guardar el nombre del servidor y el name login de esta:

![](Resources/6.png)

Luego, en las configuraciones de seguridad permitiremos a los servicios de Azure hacer uso de este recurso:

![](Resources/7.png)

## Ejercicio 2

Actualizaremos la informacion de la Weeb App, ajustado a java:

![](Resources/8.png)

Despues de eso podremos ver que el servicio esta activo y se muestra asi:

![](Resources/9.png)

Para conectarnos con la base de datos, tendremos que crear un nuevo hilo de conexion con las configuraciones de creacion del servidor de MySQL
que creamos antes:

![](Resources/10.png)

## Ejercicio 3

Ahora, iremos al [Demo Generator](https://azuredevopsdemogenerator.azurewebsites.net/?TemplateId=77371&Name=MyShuttle) y crearemos un ambiente con la plantilla de
MyShuttle y alli entraremos a la opcion de Pipelines:

![](Resources/11.png)

Buscaremos la opcion de 'MyShuttleBuild' y la editaremos con las siguientes configuraciones:

![](Resources/12.png)
![](Resources/13.png)

Despues de que se haya ejecutado de forma correcta, iremos a la parte de 'Releases':

![](Resources/14.png)

Ahora editaremos la parte de MyShuttleRelease y agregaremos el artefacto de MyShuttleBuild:
![](Resources/15.png)

Editaremos la primera etapa con ambas tareas y llenaremos los campos requeridos para poder continuar:
![](Resources/16.png)
![](Resources/17.png)

Ejecutamos el Pipeline que acabamos de editar con la opcion de create release:
![](Resources/18.png)

Si todo esta configurado de forma correcta, se ejecutara con exito:
![](Resources/19.png)

https://webappcvds.azurewebsites.net/CVDS
