<h1> Aplicación OshinStar </h1>

> <u> Guía de instalación del paquete de documentación técnica. </u>

 - 💻  [Repositorio Documentacion](https://github.com/Oshinstar-com/Docs-Backend)


### Descargando e instalando la Documentación Backend (Docs-Backend):

Se debe seguir una serie de pasos para el despliegue de la aplicación, esto es usado en su mayoría por y para desarrolladores.


> - Con el siguiente comando dentro de la terminal:

```
git clone https://github.com/Oshinstar-com/Docs-Backend
```

En caso de no tener "git" instalado, ejecutar:

```
sudo apt updat -y
sudo apt install git -y
```




Cerciórese de tener las credenciales para el acceso al repositorio de GitHub, puesto que al momento de clonar el repositorio Git le pedirá su username y password. 

Copia la url en la terminal y ejecutas hasta que descargue el paquete en la pc.






















Ya con el paquete descargado se dirige desde la terminal a la carpeta contenedora.
Instalación y configuración de Docker y Docker Compose:

Visite las URL https://docs.docker.com/engine/install/ubuntu/ y https://docs.docker.com/compose/install/ para obtener las instrucciones más actualizadas sobre cómo instalar Docker y Docker Compose.   

a) Instalación de Docker

Instale las dependencias necesarias para el uso de repositorios por HTTPS copiando y pegando las siguientes líneas de comando en su terminal:

 sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

De igual manera, añada la clave GPG de Docker copiando el siguiente comando en su terminal:  

 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

Añada el repositorio a las fuentes de APT corriendo el siguiente comando en su terminal:

echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
Instale Docker:

sudo apt-get update -y
sudo apt-get install docker-ce docker-ce-cli containerd.io

b) Instalación de Docker Compose

En su terminal pegue el siguiente comando para descargar el repositorio de Docker Compose:

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Aplique las permisiones de archivo ejecutable al archivo descargado:

sudo chmod +x /usr/local/bin/docker-compose



Generando un Token de acceso personal en GitHub

La generación de un token de acceso permite a Docker el acceso al repositorio que contiene la documentación. 

Para generar un nuevo token de acceso, visite su perfil de GitHub en   https://github.com/settings/profile. Diríjase al apartado Developer settings y presione el botón Personal Access tokens.



Presione el botón de Generate new token e introduzca una nota en el campo Note. Dentro de las permisiones disponibles en la sección de scope marque la opción de write:packages. 



Presione Generate token en la parte inferior izquierda para generar el nuevo token. Asegurese de copiar el contenido del token generado en un archivo de texto. 

Levantando el contenedor Docker

Dentro de la carpeta Docs-Backend, copie el archivo de texto con el token de autenticación generado previamente.
Utilice el comando siguiente para cargar el token de autenticación. Reemplace <TOKEN.txt> con el nombre del archivo que contiene token generado y <USERNAME> con su nombre de usuario de GitHub.

cat <TOKEN.txt> | sudo docker login https://docker.pkg.github.com -u <USERNAME> --password-stdin

Levante el contenedor Docker con el servidor web de la documentación utilizando el comando:
sudo docker-compose up











Ingresar a la url por defecto http://0.0.0.0:4000/ para revisar la documentación.

Ingresar a la url por defecto http://0.0.0.0:4000/admin/ para cambios y edición la documentación.


