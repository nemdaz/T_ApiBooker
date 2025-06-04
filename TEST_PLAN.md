# PLAN DE PRUEBAS DE SISTEMAS

### 1. Introducción

##### Nombre

| Nombre              | Detalle                                        | Versión |
| :------------------ | :--------------------------------------------- | -------- |
| PPS_010100_00000001 | Plan de pruebas para el API del sistema Booker | v1.0.0   |

##### Componentes

| Tipo       | Código | Descripción |
| :--------- | :------ | :----------- |
| Sistema    | 01      | Booker       |
| Subsistema | 0101    | Booker API   |
| Módulo    | 010100  | Todos        |

##### Responsables

| Código | Rol                | Nombre  | Función                                  |
| :------ | :----------------- | :------ | :---------------------------------------- |
| 01      | Autor              | Nem Daz | Elaboración del Plan de Pruebas          |
| 01      | Líder de proyecto | Nem Daz | Liderar la ejecución del Plan de Pruebas |

##### Documentos relacionados

| Descripción                           | Origen/Fuente                                                                                                 | Version |
| :------------------------------------ | :------------------------------------------------------------------------------------------------------------ | :------ |
| Definición del sistema Booker         | [https://restful-booker.herokuapp.com/apidoc/index.html](https://restful-booker.herokuapp.com/apidoc/index.html) | v1.0.0  |
| Especificación del API Restful Booker | [https://restful-booker.herokuapp.com/apidoc/index.html](https://restful-booker.herokuapp.com/apidoc/index.html) | v1.0.0  |

### 2. Objetivo

La finalidad del presente documento es definir las pautas y estrategias que nos permitirán cumplir con la certificación de calidad del componente 010100 del sistema Booker.

El objetivo general es definir las condiciones que nos permitan ejecutar las pruebas y en consecuencia nos entregue un sistema que cumpla con las funcionalidades requeridas por todos los interesados.

El plan de pruebas debe incluir las pautas necesarias para recrear un ambiente de pruebas automatizados y de integración continua.

### 3. Alcance

El presente documento cumple con servir de guía en el proceso de ejecución de pruebas para los responsables del proyecto.

El plan de pruebas se enmarca al modulo 010100 del sistema Booker la cual corresponde a funcionalidades del API Restful definidas (Ver punto 1 en "Documentos relacionados").

### 4. Entorno de Pruebas

##### Ambiente de Pruebas

| Tipo               | Nombre        | Detalle                                                            |
| :----------------- | :------------ | :----------------------------------------------------------------- |
| Dispositivo Laptop | Lenovo Yoga 7 | Ryzen 7 Serie 4000,<br />16GB RAM, 500GB SSD, <br />Windows 11 HSL |
| API                | Booker API    | URL Base: https://restful-booker.herokuapp.com                     |

##### Herramientas

| Tipo     | Nombre               | Detalle                                                   |
| :------- | :------------------- | :-------------------------------------------------------- |
| Software | Postman v10.9.3      | Herramienta de diseño, prueba y monitorización de APIs. |
| Software | VSCode v1.75.0       | Editor/IDE.                                               |
| Software | SourceTree 3.4.8     | Gestor de control de versiones git.                       |
| Software | Git                  | Herramienta de control de versiones.                       |
| Servicio | GitHub               | Repositorio en la nube para el control de versiones git. |
| Software | Java 17 o 21         | Software para soportar ficheros .war y .jar                 |
| Software | Jenkins v2.504.2 LTS | Herramienta para la integración continua                 |
| Software | NodeJS               | *Necesario para instalar la herramienta newman*         |
| Software | newman (cli)         | Cliente de linea de comandos de Postman                   |
| Software | jenkins-cli          | Cliente de linea de comandos de Jenkins                   |

### 5. Configuración del Entorno de Pruebas

De acuerdo a lo indicado en el punto "4. Entorno de Pruebas" se realiza la configuración del entorno de pruebas.

##### Instalación y cuentas

- Descargar el sistema de control de versiones desde la url https://git-scm.com/download/win en su version para el SO Windows.
- Descargar e instalar el sistema administrador de control de versiones SourceTree desde la url https://www.sourcetreeapp.com/ en su version para el SO Windows.
- Descargar e instalar el editor/ide VScode desde la url https://code.visualstudio.com/sha/download?build=stable&os=win32-x64.
- Descargar e instalar Postman; la descarga del instalador se realiza desde la url https://www.postman.com/downloads/ en su version para el SO Windows.
- Crear una cuenta en el servicio cloud de control de versiones https://github.com/.
- Descargar la version war de Jenkins desde la url https://www.jenkins.io/download/.
- Descargar e instalar NodeJs de manera global, usar la url https://nodejs.org/en/.

##### Configuración

**Postman**

- Abrir el aplicativo instalador y crear un espacio de trabajo (workspace) especifico para las labores de pruebas.
- Nos ubicamos en el workspace creado y añadimos una colección en la cual se almacenara los objetivos/scripts de pruebas.
- Nos ubicamos en la configuración de entorno (environments) del aplicativo y creamos el entorno QA Env, en este entorno se almacenara las variables de entorno necesarias para los scripts de pruebas en Postman.
- Para llevar el control del archivo de postman en GitHub podemos realizar alguna de las siguientes acciones:

  - Configurar el workspace de postman dentro del espacio de trabajo local (Carpeta clonada con SourceTree).
  - Cada que vayamos avanzando con la creación de nuestro script en Postman, exportemos la colección y lo coloquemos en el espacio de trabajo local (Carpeta clonada con SourceTree).

**GitHub**

- En el panel de trabajo de la plataforma ubicarnos en la opción "New repository" y crear el repositorio "YpTest_APIBooker", esto por defecto nos crea en branch main y el archivo README.md.

**SourceTree**

- Abrimos el aplicativo, seguimos los pasos que nos indica para el uso del aplicativo (solo la primera vez que se inicia), una vez que estamos en la interfaz principal nos ubicamos en la opción "*File - Clone/New*", seleccionamos la opción Clone e ingresamos los datos que nos solicita dicha interfaz:

  - La url del repositorio, creado previamente en GitHub.
  - La ruta local donde se clonará el repositorio en nuestro equipo de trabajo. Esta ruta será nuestro espacio de trabajo local para este plan de pruebas.
- Una vez clonado el repositorio de GitHub, verificamos la creación de nuestro espacio de trabajo, de acuerdo a configuraciones previas nuestra carpeta debe tener el nombre "YpTest_APIBooker". *Ejm: D:\Workspace\Yape\YpTest_APIBooker*

**VSCode**

- Abrimos el aplicativo, nos ubicamos en la opción *"**File - Open Folder"* y abrimos el folder "YpTest_APIBooker" que corresponde a nuestro espacio de trabajo. Aquí trabajemos con los archivos necesarios para el plan de pruebas.

**NodeJS**

- Instalamos Newman para disponer de la linea de comandos de Postman.

  ```
  npm install -g newman
  ```

**Newman**

- Verificamos que el comando exista ejecutando el comando: `newman --version`

**Java**

- Instalar Java 17 según las instrucciones oficiales para Windows (https://docs.oracle.com/en/java/javase/17/install/overview-jdk-installation.html).

- Verificar con:

  ```
  java --version
  ```

**Jenkins**

- Con el archivo war descargado, crear una ruta de instalación manual para Jenkins, como por Ejm: *D:\Workspace\Jenkins* y en ella colocar el archivo war.
- Crear una archivo de configuración (runJenkins.bat) de inicio de Jenkins.

  ```
  set JENKINS_HOME=local-jenkins-config
  java -Dfile.encoding=UTF-8 -jar jenkins.war --httpPort=9090
  ```

  Ejecutar *runJenkins.bat* para iniciar Jenkins en la ruta: *localhost:9090*
- Al ejecutar Jenkins por primera vez dejar la configuración por defecto y establecer el usuario y clave.
- Al ingresar al panel de control de Jenkins por primera vez, instalar el plugin NodeJS, reiniciar Jenkins.
- Volvemos a ingresar a Jenkins en la opción *"Panel de Control / Administrar Jenkins / Global Tool Configuration"* y ubicamos la sección NodeJS, en ella pulsamos en *"Añadir NodeJS"*, colocamos un nombre (Ejm. My Local NodeJS), quitamos el check *"Instalar automáticamente"* y finalmente ingresamos nuestro directorio de instalación de NodeJS (Ejm: *D:\Program Files\nodejs*). Guardamos los cambios y salimos.
- *NOTA:* Si queremos programar un cron en Jenkins tomar como referencia esta herramienta: *https://crontab.cronhub.io/*

### 6. Estrategias de Pruebas

Para el cumplimiento de los objetivos se plantean estrategias de pruebas las cuales estarán en función a los siguientes tipos, niveles y técnicas de pruebas.

| Tipo de Prueba      | Nivel de Prueba       | Técnica de Prueba                                                             |
| :------------------ | :-------------------- | :----------------------------------------------------------------------------- |
| Prueba Funcional    | Prueba de componentes | Pruebas de equivalencia y valores limites.<br />Pruebas de humo/exploratorias. |
| Prueba No Funcional | Prueba de componentes | Pruebas de rendimiento.<br />Pruebas de humo/exploratorias.                    |

###### Actividades estratégicas:

- Identificar y analizar la documentación del objeto de prueba.
- Considerando el alcance del plan de pruebas de debe reconocer y aplicar los conocimientos del probador para el uso optimo de las herramientas de pruebas.
- Los probadores (testers) deben identificar los roles y responsabilidades de los miembros del proyecto a fin de tener una reacción temprana ante posibles eventos fuera del alcance del probador.
- Se identifica en un primer momento las funcionalidades de camino feliz (Happy Path).
- Se analiza funcionalidades alternativas no esperadas o no contempladas en la definición del sistema (Unhappy Path).
- Se diseña y construye los casos de pruebas considerando las funciones principales (core) del sistema o módulo.
- Se elabora uno o varios set de datos de entrada para los casos de pruebas definidos según sea requerido por la misma.
- Se automatiza las pruebas haciendo uso de las herramientas definidas en el punto "Entorno de Pruebas / Herramientas".
- Para conservar los avances de los archivos y objetos de pruebas se hace uso del sistema de control de versiones.

### 7. Escenario de Pruebas

Dado las funcionalidades definidas para el sistema objeto (Ver punto 1 en "Documentos relacionados") de este plan de pruebas se debe abordar los escenarios de pruebas:

a) Comprobación de disponibilidad del sistema (API).

b) Generación de Token válido.

c) Las operaciones de lectura deben devolver objetos en la estructura definida en la documentación del sistema.

d) Las operaciones de creación, modificación y eliminación deben retornar la confirmación de la correcta ejecución de la operación.

e) Todas las operaciones cumplen su funcionalidad siempre que se cumpla con los formatos de los datos de entrada.

f) Todas las operaciones devuelven error (controlado o no) si no se cumple con la especificación/estructura definida para los datos de entrada.

e) Otros escenarios contemplados por el probador según lo requiera.

### 8. Diseño de Pruebas

Haciendo uso de el o los documentos de definición del sistema y en concordancia con los escenarios de pruebas contemplados a efecto de este plan de pruebas, se construye los casos de pruebas.

Los casos de pruebas son de tipo funcional y no funcional siendo asi que deben cumplir con:

- Prefijo y nombre de caso de prueba.
- Pre-requisitos y requisitos del caso de prueba.
- Datos de entrada para el caso de prueba.
- Detalle del caso de prueba.
- Resultado esperado del caso de prueba.
- Los casos de prueba pueden incluir los pasos de prueba.
- Los pasos de prueba tiene datos de entrada (incluidos en los datos de entrada de la prueba).
- Cada paso de prueba tiene un orden y resultado esperado.
- La ejecución satisfactoria de todos los pasos de la prueba hace cumplir el resultado esperado general de la prueba.

### 9. Criterios de Aceptación

El proyecto es aprobado si se satisface los siguientes criterios de aceptación:

| Nro. | Descripción                                                                                                          |
| :--- | :-------------------------------------------------------------------------------------------------------------------- |
| 1    | El sistema/módulo debe cumplir satisfactoriamente el 100% de las ejecuciones de los casos de pruebas funcionales.    |
| 2    | El sistema/módulo debe cumplir satisfactoriamente el 100% de las ejecuciones de los casos de pruebas no funcionales. |

### 10. Producto de trabajo de pruebas

| Tipo de Prueba                                  | Tipo de Ejecución       | Producto                               | Descripción                                                                                                                                                                                                      |
| :---------------------------------------------- | :----------------------- | :------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pruebas Funcionales<br />Pruebas No Funcionales | Automatizada             | ***TEST_CASES.DataEntry***                | La carpeta contiene el set de datos necesarios para las pruebas.<br />Existe un archivo JSON por cada caso de prueba.<br />No todos los archivos tienen contenido, pero se crearon a fin de mantener el orden.    |
| Pruebas Funcionales<br />Pruebas No Funcionales | Automatizada             | ***TEST_CASES.postman_collection.json***  | Este producto es el archivo JSON que contiene toda la colección de pruebas.<br />Estas pruebas fueron diseñadas y creadas en postman.<br />Este archivo es resultado de exportar la colección desde postman. |
| Pruebas Funcionales<br />Pruebas No Funcionales | Automatizada             | ***TEST_CASES.postman_environment.json*** | Este archivo es resultado de exportar la configuración del entorno desde postman.<br />Es necesario para la automatización, pues contiene valores iniciales de la pruebas.                                     |
| N/A                                             | N/A                      | ***TEST_CASES.md***                       | Lista de casos de pruebas elaborados y posteriormente implementados en postman.                                                                                                                                    |
| N/A                                             | Automatizada             | ***TEST_CASES.jenkins_job.xml***          | Archivo de configuración de del JOB necesario para la integración continua en Jenkins.                                                                                                                          |
| N/A                                             | Manual<br />Automatizada | ***TEST_CASES.build_steps.bat***          | Archivo de instrucciones de postman (newman) necesario para la creación de JOB en Jenkins.                                                                                                                        |
| N/A                                             | Manual                   | ***resources/jenkins-cli.jar***           | Herramienta que nos permite importar la configuración del Job en Jenkins.                                                                                                                                         |
