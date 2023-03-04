# kafka-practice
This repository contains initial configuration for an practice excercice using Kafka.

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#kafka">Kafka</a></li>
    <li><a href="#postgre-sql">PostgreSQL</a></li>
    <li>
	  <a href="#practice">Practice</a>
	  <ul>
		<li><a href="#twitter-simulator">Twitter Simulator</a></li>
		<li><a href="#requirements">Requirements</a></li>
      </ul>
	</li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->
## About The Project

This repository will allow us to locally configure two Kafka services (zookeeper, broker, control-center) and PostgreSQL (postgresq, pgadmin) using docker descktop.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started (1)

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
1. Open a git bash RIGHT IN THE DIRECTORY where the file "docker-compose-kafka.yml" is located.
    (Not recommended:You can do it with cmd but you must be as administrator)
2. Open the docker application "Docker desktop" or at least make sure to start it via CMD or that the service is running.
3. Execute the following command:
	```sh
	docker-compose -f nombre_archivo_compose.yml up
	```
    So for our case: docker-compose -f docker-compose-kafka.yml up
4. Wait a couple of minutes for all the dependencies to download and if the logs do not show an error, then you can check with the web 
   client that kafka is running. you can verify with the web client that kafka is running: http://localhost:9021/
    (Web client: also executed because its use is specified in the file "yml")
	
#### PostgreSQL
1. Open a git bash JUST IN THE DIRECTORY where the file is located "docker-compose-postgresql.yml" 
    (Not recommended: You can do it with cmd but you must be as administrator)
2. Open the docker application "Docker desktop" or at least make sure to start it via CMD or that the service is running.
3. Execute the following command: 
	```sh
	docker-compose -f nombre_archivo_compose.yml up
	```
    So for our case: docker-compose -f docker-compose-postgresql.yml up
4. Wait a couple of minutes for all the dependencies to download and if the logs do not show an error, then
    you can verify with the web client that PostgreSQL is running: http://localhost:80/
    (According to the port defined in the "ports" variable of the yml file. Web client: also executed because its use is specified in the "yml" file.)
4.1. In the Ui where the access credentials are requested, insert the username or email that I indicate as the value for the variable called 
     "PGADMIN_DEFAULT_EMAIL" in the yml file (if you have not edited the file, the value should be "admin@admin.com")
5. In the Ui where the access credentials are requested, insert the username or email that I indicate as the value for the variable called 
     PGADMIN_DEFAULT_PASSWORD in the yml file (if you have not edited the file, the value should be "admin")
6. When you open the PgAdmin interface or main screen, create a new connection to the DB with the postgress super user, 
     following these steps:
       
		A - In the left panel, right click on the option "Servers" and then choose the option "create" and
                    then the "server" option
		B - In the displayed UI, fill in the "Name" box by placing the name of your choice for your connection.
		C - In the UI, go to the "Connection" tab.
		D - In the "Host" box, put the name "postgres" (This is because we are not connecting to a local host but to 
					a service exposed by the PostgreSQL docker image we have created. As specified in the yml file in 
					the "services" section, the name of that service is "postgres").
		E - In the "Port" box you must specify the PORT that you specified in the "postgres" service in the yml file 
					(if you have not edited the file, it should be the value "5432").
		F - In the "Username" box you must indicate the USER that you specified in the "POSTGRES_USER" variable of the yml file 
					(if you have not edited the file, it should be the value "root").
        G - In the "Password" box you must enter the password you specified in the "POSTGRES_PASSWORD" variable of the yml file 
					(if you have not edited the file, it should be the value "root").
    
<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Practice

### Twitter Simulator

The purpose of this exercise is to have two microservices:
- The first one is going to expose a post type end-point that is going to receive messages (JSON). And post messages in kafka topic (publisher).
- The second will consume those messages and store them in the PostgreSQL database.

### Requirements
- Entity-relationship diagram.
- High level design.
- Architecture decisions.
- Detailed explanation of kafka for the publisher and the consumer.
- Implementation of the exercise applying 90% test coverage.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[Java.ico]: https://img.shields.io/badge/Java-DD0031?style=for-the-badge&logo=java&logoColor=white
[Java-url]: https://www.oracle.com/java/technologies/javase/jdk18-archive-downloads.html
[Docker.ico]: https://img.shields.io/badge/Docker-F0FFFF?style=for-the-badge&logo=docker&logoColor=blue
[Docker-url]: https://www.docker.com/products/docker-desktop/
[GitBash.ico]: https://git-scm.com/favicon.ico
[GitBash-url]: https://git-scm.com/downloads
