## IBM UrbanCode Build con MySQL en Docker

Acá se muestra como ejecutar mediante Docker (container) una versión de evaluacion de UCB con base de datos MySql.

#### Construir la imagen
1) Descargar todos los archivos de este repositorio a un directorio local.
2) Mediante command line, moverse dentro del directorio local.
3) Ejecutar docker build utilizando el archivo Dockerfile.

```
git clone https://github.com/IBMInnovationLabUY/dojo-ucb.git
docker build -t <namespace>/ucb-server:<version> .
```

 ** Nota: ** En el Dockerfile se podrán configurar las diferentes variables de entorno en caso de ser necesario.
´´´
ENV HTTPS_PORT=8443 JMS_PORT=7919 MYSQL_PORT=3306 DB_NAME="ibm_ucb" DB_USER="ibm_ucb" DB_PASSWORD="password"
´´´
También podrán indicarse a la hora de ejecutar la imagen
```
docker run -d -e BUILD_SERVER_HOSTNAME=<server-hostname-or-ip> -e DB_HOST=<db-hostname-or-ip> -p <some-port>:8443 -p <another-port>:7919 mkorejo/ucb-server
```

#### Ejecutar la imagen
 Se debe ejecutar dentro del directorio `docker-compose up` que utilizara el archivo docker-compose.yml para crear los containers de MySql y UCB con las imagenes creadas.
 
#### Usando UCB
Si todo salio correctamente podremos ingresar a https://localhost:9443/ con usuario: admin y password: admin, pa comenzar a usar UCB.
