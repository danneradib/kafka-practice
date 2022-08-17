# kafka-practice
This repository contains initial configuration for an practice excercice using Kafka.

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Prerequisites</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

This repository will allow us to locally configure two Kafka services (zookeeper, broker, control-center) and PostgreSQL (postgresq, pgadmin) using docker descktop.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Prerequisites

To perform this exercise we need to have the following elements installed locally:

* [![Java][Java.ico]][Java-url]
* [![Docker][Docker.ico]][Docker-url]
* [![GitBash][GitBash.ico]][GitBash-url]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Installation

#### Kafka
1. Abra un git bash JUSTO EN EL DIRECTORIO donde se encuentra el archivo "docker-compose-kafka.yml"
    (No recomendado:Puede hacerlo con cmd pero debe estar como administrador)
2. Abra la aplicaciòn de docker "Docker desktop" o almenos asegurese de inicarla por CMD o que el servicio este corriendo
3. Ejecute el siguiente comando:
	```sh
	docker-compose -f nombre_archivo_compose.yml up
	```
    Osea para nuestro caso asi: docker-compose -f docker-compose-kafka.yml up
4. Espere un par de minutos para que se bajen todas las dependencias y si los logs no muestran un error, entonces 
    puede verificar con el cliente web que kafka este ejecutandose: http://localhost:9021/
    (Cliente web: tamben ejecutado por que se especifica su uso en el arhcivo "yml")
	
#### PostgreSQL
1. Abra un git bash JUSTO EN EL DIRECTORIO donde se encuentra el archivo "docker-compose-postgresql.yml" 
    (No recomendado:Puede hacerlo con cmd pero debe estar como administrador)
2. Abra la aplicaciòn de docker "Docker desktop" o almenos asegurese de inicarla por CMD o que el servicio este corriendo
3. Ejecute el siguiente comando: 
	```sh
	docker-compose -f nombre_archivo_compose.yml up
	```
    Osea para nuestro caso asi: docker-compose -f docker-compose-postgresql.yml up
4. Espere un par de minutos para que se bajen todas las dependencias y si los logs no muestran un error, entonces 
    puede verificar con el cliente web que PostgreSQL este ejecutandose: http://localhost:80/
    (Acorde al puerto definido en la vaiable "ports" del archivo yml. Cliente web: tamben ejecutado por que se especifica su uso en el arhcivo "yml")
4.1. En la Ui donde se piden las credenciales de acceso, inserte el username o correo que indico como valor para la variable llamada 
     "PGADMIN_DEFAULT_EMAIL" en el archivo yml (si no ha Editado el archivo, el valor debe ser "admin@admin.com")
5. En la Ui donde se piden las credenciales de acceso, inserte el username o correo que indico como valor para la variable llamada 
     PGADMIN_DEFAULT_PASSWORDen el archivo yml (si no ha Editado el archivo, el valor debe ser "admin")
6. Al abrir la interfaz o pantalla principal de PgAdmin, cree una nueva conexiòn a la Bd con el super usuario de postgress, siguiendo los 
    siguientes pasos:
       
		A - En el panel izquierdo, click derecho sobre la opciòn "Servers" y a continuaciòn escoja la opciòn "create" y
                    luego la opciòn "server"
		B - En la UI desplegada, llene la casilla "Name" colocandole el nombre que usted desee a su conexiòn.
		C - En la UI despelgada, vaya a la pestaña "Connection".
		D - En la casilla "Host", coloque el nombre "postgres" (Lo anterior por que no nos vamos  conectar a local 
			host sino a un servicio expuesto por la imagen de docker de PostgreSQL que hemos creado. Como bien se especifico 
			en el archivo yml en la secciòn "services", el nombre de ese servicio es "postgres").
		E - En la casilla "Port" se debe indicar el PUERTO que se especifico en para el servicio "postgres" en el archivo yml 
                    (si no ha editado el archivo, deberìa ser el valor "5432").
		F - En la casilla "Username" se debe indicar el USUARIO que se especifico en la variable "POSTGRES_USER" del archivo yml 
                    (si no ha editado el archivo, deberìa ser el valor "root").
                F - En la casilla "Password" se debe indicar la contraseña que se especifico en la variable "POSTGRES_PASSWORD" del archivo yml 
                    (si no ha editado el archivo, deberìa ser el valor "root").    
    
<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[Java.ico]: https://img.shields.io/badge/Java-DD0031?style=for-the-badge&logo=java&logoColor=white
[Java-url]: https://www.oracle.com/java/technologies/javase/jdk18-archive-downloads.html
[Docker.ico]: https://www.docker.com/wp-content/uploads/2022/05/Docker_Temporary_Image_Social_Thumbnail_1200x630_v5.png
[Docker-url]: https://www.docker.com/products/docker-desktop/
[GitBash.ico]: https://git-scm.com/favicon.ico
[GitBash-url]: https://git-scm.com/downloads