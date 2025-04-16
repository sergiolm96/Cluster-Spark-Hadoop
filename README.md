Proyecto de Procesamiento de Logs con Hadoop y PySpark
======================================================

Descripción
-----------

Este proyecto tiene como objetivo procesar un archivo de logs (`access.log`) utilizando **Hadoop** como sistema de almacenamiento distribuido (HDFS) y **PySpark** para procesar y analizar los datos. Los datos se cargan desde un archivo local a un contenedor de Hadoop y luego se procesan con PySpark para obtener información como las IPs más frecuentes, las solicitudes por hora y los errores más comunes.

El proyecto utiliza **Docker** para orquestar los contenedores y establecer un entorno de trabajo en el que tanto Hadoop como PySpark interactúan para procesar los datos.

Tecnologías utilizadas
----------------------

- **Docker**: Para crear y gestionar los contenedores de Hadoop y PySpark.

- **Hadoop** (HDFS): Sistema de archivos distribuido utilizado para almacenar el archivo de logs.

- **PySpark**: API de Python para Apache Spark, utilizada para procesar y analizar los datos en paralelo.

- **Jupyter Notebooks**: Para facilitar la visualización y análisis interactivo de los resultados utilizando PySpark.

Arquitectura
------------

El proyecto está compuesto por los siguientes servicios, definidos en un archivo `docker-compose.yml`:

1. **PySpark**:

    - Utiliza la imagen `jupyter/pyspark-notebook:latest`.

    - Permite ejecutar código de PySpark en un entorno interactivo de Jupyter.

    - Los datos y scripts se montan en el contenedor para que se puedan acceder y modificar fácilmente.

2. **Hadoop NameNode**:

    - Utiliza la imagen `bde2020/hadoop-namenode:latest`.

    - Gestiona el sistema de archivos distribuido HDFS.

    - Crea el directorio `/logs/input` en HDFS para almacenar los logs.

3. **Hadoop DataNode**:

    - Utiliza la imagen `bde2020/hadoop-datanode:latest`.

    - Almacena los datos del sistema de archivos distribuido HDFS.

    - Depende del NameNode para la sincronización y almacenamiento de los datos.

Requisitos previos
------------------

Para ejecutar este proyecto, necesitas tener las siguientes herramientas instaladas:

- **Docker**: Para ejecutar los contenedores.

- **Docker Compose**: Para gestionar múltiples contenedores Docker de forma sencilla.

- **Python**: Para ejecutar los scripts de PySpark en el entorno de Jupyter.

Instalación
-----------

Sigue estos pasos para ejecutar el proyecto en tu máquina local:

1. **Clona el repositorio**:

    bash

    CopiarEditar

    `git clone <https://github.com/sergiolm96/Cluster-Spark-Hadoop.git>
    cd <directorio-del-repositorio>`

2. **Asegúrate de tener Docker y Docker Compose instalados**:

    Puedes verificar si tienes Docker y Docker Compose instalados con los siguientes comandos:

    bash

    CopiarEditar

    `docker --version
    docker-compose --version`

3. **Configura el archivo `docker-compose.yml`**:

    Revisa y ajusta el archivo `docker-compose.yml` según tus necesidades. Asegúrate de que los volúmenes de datos y scripts estén correctamente montados.

4. **Inicia los contenedores**:

    Una vez que tengas todo configurado, ejecuta el siguiente comando para iniciar los contenedores de Hadoop y PySpark:

    bash

    CopiarEditar

    `docker-compose up`

    Este comando descargará las imágenes necesarias y levantará los contenedores de Hadoop y PySpark.

5. **Accede a Jupyter**:

    Después de que los contenedores estén en funcionamiento, puedes acceder a Jupyter Notebook en `http://localhost:8888` desde tu navegador web. Aquí podrás ejecutar los scripts de PySpark para analizar los logs.

6. **Carga y procesa los logs**:

    Los logs (`access.log`) se encuentran en el volumen `./data`, lo que permite acceder a ellos desde Jupyter para el procesamiento y análisis.

Estructura de archivos
----------------------

`project-root/
│
├── data/                # Contiene los archivos de logs (access.log)
│
├── src/                 # Código fuente y scripts de PySpark
│
├── docker-compose.yml   # Archivo de configuración de Docker Compose
│
├── requirements.txt     # Requisitos para el entorno Python
│
└── README.md            # Este archivo`


Conclusión
----------

Este proyecto es un buen punto de partida para trabajar con Hadoop y PySpark, permitiendo procesar grandes volúmenes de datos en un entorno distribuido. Con las mejoras propuestas, puedes expandir su funcionalidad y escalabilidad para adaptarse a proyectos más grandes y complejos. La integración con Docker facilita la creación de entornos aislados y portables, mientras que PySpark permite realizar análisis de datos a gran escala de manera eficiente.
