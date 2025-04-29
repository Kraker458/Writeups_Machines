#htb 
***
## **Información de la máquina:**
### Sistema operativo de la máquina: **Linux Ubuntu** (version ????)
### Guia de la máquina:
#### **Los servicios que podemos observar son:**
**SSH (puerto 22)**
>*Método de conexión segura* en la que utilizaremos para poder acceder a la máquina y por lo tanto conseguir las flags (códigos)

**https (Puerto 80)**
>Servicios web con diferentes puertos con los que probaremos seguidamente que contenido tienen, un punto importante a tener en cuenta es que *muchas veces la información que nos da el escaneo podemos encontrar algún exploit*, viendo la versión del servicio o del componente que utiliza como aplicación.

**Explicación del comando utilizado:**
>Nmap es una herramienta de escaneo de redes y servicios de máquinas para las auditorías. Es una herramienta muy importante ya que nos puede dar información para una posible explotación de alguna vulnerabilidad del servicio.
>*Características:*
>**(-p):** sirve para poder especificar que puertos nos interesa que nmap escanee. También podemos hacer (-p-) para hacer un escaneo de todos los puertos de una máquina.
>**(-sV):** Esta opción sirve para que nmap nos diga las versiones de la máquina para así buscar vulnerabilidades por la versión del servicio.
>**(-min--rate 5000):** Esta característica tiene como función acelerar la velocidad de escaneo poniendo que mínimo haga 7000 peticiones por segundo.
>**(-open):** Con esta opción hacemos que el resultado de nmap solo nos muestre los puertos abiertos de la máquina.
>**(-o):** Esta característica hace referencia a que el "output" del comando nmap se almacene dentro del archivo en este caso "nmap_Underpass.txt"
![[Pasted image 20250429215604.png]]

***NOTA:***

***
#### **Explicación del Comando: `gobuster dir`**
>*Gobuster* es una **herramienta de escaneo de fuerza bruta de directorios y archivos** en servidores web, crucial para **auditorías de seguridad** al descubrir recursos ocultos.

##### **Modo de Operación:**
- `dir`: Indica el modo de **descubrimiento de directorios y archivos**. Similar a los modos de escaneo de Nmap.
##### **Objetivo:**
- `-u 'http://10.10.11.48/'`: Especifica la **URL objetivo** del escaneo.
    - `-u`: Opción para la **URL**.
    - `'http://10.10.11.48/'`: **Dirección IP del servidor web** a auditar, comenzando la búsqueda desde la raíz (`/`).
##### **Lista de Palabras:**
- `-w /home/kraker458/Desktop/SecLists/Discovery/Web-Content/directory-list-2.3-big.txt`: Define la **lista de palabras (wordlist)** para adivinar nombres de directorios y archivos.
    - `-w`: Opción para la **wordlist**.
    - `/home/kraker458/Desktop/SecLists/Discovery/Web-Content/directory-list-2.3-big.txt`: **Ruta al archivo de texto** con una gran cantidad de nombres comunes. Gobuster prueba cada entrada añadiéndola a la URL base. Similar a cómo Nmap usa información para identificar servicios.
##### **Rendimiento:**
- `-t 200`: Establece el **número de hilos (threads)** para realizar peticiones simultáneamente.
    - `-t`: Opción para el **número de hilos**.
    - `200`: Realiza hasta **200 peticiones HTTP simultáneas**, acelerando el escaneo (similar a `-min-rate` en Nmap para la velocidad).
##### **Extensiones de Archivo:**
- `-x html,php,txt,js,.,git,php`: Especifica las **extensiones de archivo** a buscar, además de directorios.
    - `-x`: Opción para las **extensiones**.
    - `html,php,txt,js,.,git,php`: **Lista de extensiones** separadas por comas. Gobuster busca archivos con estas extensiones dentro de los directorios y en la raíz. `.` para archivos sin extensión y `.git` para repositorios Git expuestos.
##### **Propósito del Comando:**
>Identificar **directorios y archivos no evidentes** en el servidor web, que podrían contener **información sensible, ser puntos de entrada para vulnerabilidades o revelar la estructura interna** de la aplicación web. Los resultados mostrarán los recursos para los que el servidor responde con un código de estado de existencia (por defecto, 200 OK).


***
