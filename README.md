# Proyecto final de analisis y sistemas

### **docker-compose.yml**
Este es un archivo docker-compose.yml utilizado para definir y ejecutar múltiples contenedores en Docker.

En este archivo, se definen cinco servicios: **postgres,** **redis,** **nginx,** **api,** **client** y **worker.**  
- El servicio postgres utiliza la imagen oficial de Postgres y establece la contraseña de la base de datos.
- El servicio redis utiliza la imagen oficial de Redis.
- El servicio nginx es el servidor web y se basa en la imagen que se construye a partir de un Dockerfile.dev en la carpeta de nginx. Depende de los servicios api y client, y está expuesto en el puerto 3050.
- El servicio api es la API del servidor y se basa en la imagen que se construye a partir de un Dockerfile.dev en la carpeta de server. Se definen algunas variables de entorno, incluidas las credenciales de acceso a la base de datos y la dirección y el puerto del servidor Redis.
- El servicio client es la aplicación cliente y se basa en la imagen que se construye a partir de un Dockerfile.dev en la carpeta de client. También utiliza un volumen para montar el directorio de la aplicación cliente en el contenedor.
- El servicio worker es el trabajador y se basa en la imagen que se construye a partir de un Dockerfile.dev en la carpeta de worker. También utiliza un volumen para montar el directorio del trabajador en el contenedor y se definen las credenciales de Redis.

Cada uno de estos servicios puede ser construido y ejecutado mediante el comando **docker-compose up.** 

---

## **client**
- **Dockerfile.dev:** Es un archivo Dockerfile que construye una imagen de contenedor de Docker utilizando la imagen base de **node:16-alpine.** Este archivo define el directorio de trabajo, copia el archivo **package.json** al directorio de trabajo, ejecuta el comando **npm install** para instalar las dependencias del proyecto, copia todo el contenido de la aplicación al directorio de trabajo y finalmente ejecuta el comando **"npm run start"** para iniciar la aplicación.


- **package.json:** Es un archivo **package.json** que contiene la información del proyecto, incluyendo su nombre, versión, dependencias, scripts, configuración de eslint y la lista de navegadores compatibles. En este archivo se especifican las dependencias que serán instaladas a través del comando **"npm install"** en el primer código, y se definen los comandos que pueden ser ejecutados a través del comando **"npm run nombre del script".** En este caso, se definen los scripts start, build, test y eject que son comandos comunes en proyectos React. También se especifica la configuración de eslint que se utiliza para analizar y corregir problemas de estilo en el código, y la lista de navegadores compatibles con el proyecto.
  
  
- **.gitignore:** Este es un archivo .gitignore que especifica los archivos y directorios que deben ser ignorados por Git. Esto significa que Git no rastreará ni incluirá estos archivos y directorios en el repositorio. En este caso, se ignoran los siguientes:
  
1. **/node_modules:** Directorio donde se instalan las dependencias de Node.js.
2. **/.pnp y .pnp.js:** Archivos relacionados con Plug'n'Play (PnP) de Yarn.
3. **/coverage:** Directorio donde se almacenan los resultados de cobertura de pruebas.
4. **/build:** Directorio donde se almacenan los archivos generados para la producción.
5. **.DS_Store:** Archivo creado por el Finder de macOS que almacena información sobre la carpeta.
6. **.env.local, .env.development.local, .env.test.local y .env.production.local:** Archivos de configuración de entorno local que deben ser ignorados.
7. __npm-debug.log*, yarn-debug.log* y yarn-error.log*:__ Archivos de registro de depuración que pueden ser generados por los gestores de paquetes NPM y Yarn.
---

### **client\public**
- **index.html:** Es un archivo HTML que se utiliza como plantilla para la aplicación React. Este archivo define la estructura básica de la página HTML, incluyendo metadatos como la descripción de la página, el título y los iconos de la aplicación. También incluye una etiqueta de script que define el elemento de la página HTML donde se va a renderizar la aplicación React, así como un mensaje de "noscript" que se muestra si JavaScript está deshabilitado en el navegador del usuario.
  

- **manifest.json:** Es un archivo **manifest.json,** que es utilizado para proporcionar metadatos que se usan cuando se instala una aplicación web en un dispositivo móvil o de escritorio. En este caso, el archivo define el nombre corto y largo de la aplicación, los iconos que se usan para representar la aplicación, la URL de inicio, el modo de presentación, el color del tema y el color de fondo. Estos metadatos se usan para proporcionar una experiencia más nativa y de alta calidad para los usuarios que instalan la aplicación en sus dispositivos.
  

- **robots.txt:** El archivo **robots.txt** es un archivo de texto plano que se utiliza para informar a los motores de búsqueda y otros robots de rastreo web acerca de las páginas del sitio que pueden o no pueden ser rastreadas. El protocolo **"robots.txt"** es una especie de acuerdo entre los sitios web y los motores de búsqueda para definir las reglas de acceso a los contenidos del sitio.
  En la página web https://www.robotstxt.org/robotstxt.html se pueden encontrar toda la información relacionada con este protocolo, incluyendo una descripción detallada del formato y la sintaxis del archivo **robots.txt,** las reglas y directivas que se pueden utilizar, ejemplos prácticos, recomendaciones, entre otros recursos. Además, también se pueden encontrar otras herramientas y utilidades relacionadas con el protocolo **"robots.txt".**
---

### **client\src**
- **App.css:** Este código es una hoja de estilos CSS que se utiliza en una aplicación web. Define estilos para diferentes elementos HTML en la página.

Por ejemplo, la clase **".App"** establece el texto centrado en la página. ".App-logo" establece el tamaño y otros atributos de una imagen de logo en la aplicación. La regla **"@media (prefers-reduced-motion: no-preference)"** establece una animación de rotación para el logo si el usuario no tiene preferencia de reducción de movimiento. La clase **".App-header"** establece el fondo, altura mínima, alineación y tamaño de fuente del encabezado de la aplicación.

La última regla **"@keyframes App-logo-spin"** establece los fotogramas clave para la animación del logo. En este caso, el logo girará 360 grados en 20 segundos.

- **App.js:** Este código es un ejemplo de una aplicación web de React que utiliza el enrutamiento con React Router.
El componente App define el esqueleto de la aplicación, que consiste en un encabezado que contiene un logotipo, un enlace *"Learn React"* y dos enlaces de navegación, *"Home"* y *"Other Page".*

El componente **Router** de React Router envuelve todo el contenido de la aplicación y establece las rutas para los componentes que se mostrarán en cada enlace.
El contenido principal de la aplicación se define dentro de la etiqueta div con la clase App. Los componentes de React que se muestran en cada ruta se definen mediante la etiqueta **Route.**

En este ejemplo, hay dos rutas definidas: la ruta principal "/" se asigna al componente Fib, mientras que la ruta *"/otherpage"* se asigna al componente **OtherPage.**
Cada vez que el usuario hace clic en uno de los enlaces de navegación, React Router cambia la URL y carga el componente correspondiente.
  

- **App.test.js:** Este es un código de prueba automatizada (unit test). El propósito de este test es verificar si un enlace que dice "Learn React" se encuentra presente en la interfaz de usuario.
Para hacer esto, se utiliza la biblioteca de pruebas automatizadas **React Testing Library.** La función render renderiza el componente App en una simulación de navegador web, permitiendo que las pruebas interactúen con la interfaz de usuario como lo haría un usuario real.

Luego, se usa la función **screen.getByText** para buscar un elemento que contenga el texto *"learn react"* y se espera que esté presente en el documento (es decir, que exista). Si el elemento no está presente, la prueba fallará.

En resumen, el código de prueba automatizada verifica que el enlace *"Learn React"* se encuentra presente en la aplicación, lo que garantiza que la aplicación se renderiza correctamente y que el enlace funciona correctamente

- **Fib.js:** Este código implementa un componente React llamado *Fib,* que interactúa con la aplicación en el servidor a través de la biblioteca de axios para hacer solicitudes HTTP. La aplicación del servidor es un servicio que calcula los números de la secuencia de Fibonacci.
  

El estado del componente tiene tres campos: **seenIndexes,** **values** e **index.** seenIndexes es una lista de los índices cuyos números correspondientes de Fibonacci ya han sido calculados. values es un objeto que mapea cada índice a su correspondiente número de Fibonacci. index es la entrada actual del usuario que se utiliza para agregar un nuevo índice a la lista de índices calculados.

El método **componentDidMount** se llama automáticamente después de que se monta el componente. Se utiliza para obtener los valores actuales y los índices calculados, que se almacenan en el estado.
El método fetchValues hace una solicitud HTTP a **/api/values/current** para obtener los valores actuales de la secuencia de Fibonacci y actualiza el estado del componente con los valores devueltos.
El método **fetchIndexes** hace una solicitud HTTP a **/api/values/all** para obtener los índices calculados y actualiza el estado del componente con los índices devueltos.
El método **handleSubmit** se llama cuando el usuario envía un formulario para agregar un nuevo índice. Hace una solicitud HTTP POST a **/api/values** con el índice actual y luego borra el campo de entrada.
Los métodos **renderSeenIndexes** y **renderValues** se utilizan para representar los valores actuales y los índices calculados en la interfaz de usuario. renderSeenIndexes muestra los índices ya calculados en forma de lista, mientras que **renderValues** muestra el cálculo correspondiente para cada índice.

En resumen, este componente React se utiliza para mostrar los valores calculados de la secuencia de Fibonacci y permitir que el usuario agregue nuevos índices a calcular.
  

- **index.css:** Este código define estilos para la página web en general y para el código fuente. En particular, el estilo para el body establece un margen de 0 y define una serie de fuentes de texto para que se usen en la página web, siendo la primera de ellas -apple-system, que es la fuente de sistema predeterminada en dispositivos Apple. Los estilos adicionales para code establecen una fuente específica para el código fuente que se puede usar en la página. También hay algunas propiedades específicas de la fuente que mejoran su legibilidad en diferentes sistemas operativos.

- **index.js:** El siguiente código es el punto de entrada del proyecto de React. Este archivo principal **index.js** importa los módulos de React y ReactDOM, el componente App, el archivo CSS **index.css** y una función reportWebVitals para medir el rendimiento de la aplicación.
Luego, se llama a la función **ReactDOM.render()** para renderizar el componente App en el elemento HTML con el ID *"root"* del archivo **index.html.** Esto significa que todo el contenido de la aplicación de React se renderizará dentro de la etiqueta **div id="root"/div** en el archivo HTML.

Finalmente, se llama a la función **reportWebVitals()** para medir el rendimiento de la aplicación. Esta función puede ser reemplazada con otra función que envíe los resultados de rendimiento a un servidor de análisis para un seguimiento más detallado del rendimiento de la aplicación.
  

- **logo.svg:** Este código es un fragmento de una imagen SVG que representa el logo de React, una biblioteca de JavaScript para construir interfaces de usuario.
El código define un grupo de elementos gráficos (<g>) que representan el logo de React en sí mismo, utilizando el atributo fill para establecer el color de relleno de los elementos. El logo está compuesto por una serie de paths, que definen las formas que componen el logo.

Además, el código incluye coordenadas **(viewBox)** para definir el área de visualización de la imagen SVG. En este caso, se define un rectángulo que mide 841.9 unidades de ancho por 595.3 unidades de alto.

- **OtherPage.js:** Este código define un componente de React llamado **"OtherPage"** que renderiza un mensaje de texto *"Im some other page!"* y un enlace usando la etiqueta "Link" de React Router. El enlace se muestra como *"Go back home"* y cuando se hace clic en él, redirige al usuario a la página de inicio del sitio web.
El componente **OtherPage** es exportado como un módulo por defecto, lo que permite que sea importado y utilizado en otros archivos de la aplicación de React.
  

- **reportWebVitals.js:** Este código exporta una función llamada **reportWebVitals** que acepta un parámetro **onPerfEntry.** Si onPerfEntry es una función, la función **reportWebVitals** utiliza la función **import()** para cargar un módulo llamado **web-vitals.** Luego, se llama a varias funciones de **web-vitals** para registrar los valores de distintas métricas de rendimiento en el objeto **onPerfEntry** que se pasó como parámetro.

En resumen, este código es parte de una herramienta para medir el rendimiento web en la aplicación React y se utiliza para registrar las métricas de rendimiento en **onPerfEntry** para que puedan ser recopiladas y analizadas más tarde.
  

- **setupTests.js:** El código importa el paquete **"@testing-library/jest-dom",** que es una biblioteca de utilidades para realizar pruebas de unidades de interfaz de usuario en React. Esta biblioteca proporciona funciones de aserción adicionales que se pueden usar en pruebas Jest, para verificar si los elementos de la interfaz de usuario se comportan como se espera. Por ejemplo, esta biblioteca agrega la función **toHaveTextContent()** para verificar si un elemento tiene un determinado contenido de texto. Al importar el paquete en un archivo de prueba, se pueden utilizar estas funciones adicionales de aserción.
---

### **nginx**
- **default.conf:** El código proporcionado es una configuración de servidor Nginx que se utiliza comúnmente para servir aplicaciones web en producción.
La sección **upstream** define dos servidores backend llamados **client** y **api** que escuchan en los puertos 3000 y 5000, respectivamente. Luego, se define un servidor principal que escucha en el puerto 80.

La sección **location** se utiliza para enrutar las solicitudes HTTP entrantes. La primera ubicación **/** redirige todas las solicitudes a la aplicación web en el servidor backend **client.** La ubicación **/ws** se utiliza para enrutar todas las solicitudes WebSocket a la misma aplicación web en el servidor backend **client.**
La ubicación **/api** se utiliza para enrutar todas las solicitudes API a la aplicación backend en el servidor **api.** La línea **rewrite /api/(.*) /$1 break;** elimina la cadena "/api" del URI de la solicitud entrante antes de enrutar la solicitud al servidor backend **api.**

En resumen, este archivo de configuración de Nginx se utiliza para enrutar las solicitudes HTTP y WebSocket entrantes a las aplicaciones web y API backend en servidores separados.


- **Dockerfile.dev:** El siguiente código es un archivo Dockerfile que especifica una imagen de Docker que utiliza el servidor web NGINX y configura el archivo de configuración predeterminado de NGINX con el archivo "default.conf" en el directorio actual.
La primera línea especifica la imagen base que se utilizará para construir la nueva imagen. En este caso, la imagen de Docker que contiene NGINX se utilizará como la imagen base.
La segunda línea copia el archivo de configuración "default.conf" del directorio actual al directorio "/etc/nginx/conf.d/" en la imagen de Docker.
---
  
### **server**
- **Dockerfile.dev:** Este es un archivo Dockerfile que describe cómo construir una imagen de Docker para una aplicación Node.js.

El código comienza con la instrucción **FROM,** que indica que la imagen de Docker se basará en la imagen **node:16-alpine.**
Luego se establece el directorio de trabajo para la aplicación en **/app** utilizando la instrucción **WORKDIR.**
A continuación, se copia el archivo **package.json** en el directorio de trabajo utilizando la instrucción **COPY.**
Se ejecuta el comando **npm install** para instalar las dependencias de la aplicación.

Finalmente, se copia todo el contenido del directorio actual (el código fuente de la aplicación) en el directorio de trabajo utilizando la instrucción **COPY.** La instrucción **CMD** se utiliza para especificar el comando que se ejecutará cuando se inicie un contenedor basado en esta imagen, que en este caso es **npm run dev,** que se utiliza para iniciar el servidor de desarrollo de Node.js.
  
  
- **index.js:** Este código es una aplicación Node.js que configura un servidor Express con varios endpoints para manejar una aplicación que toma un número entero como entrada, lo almacena en una base de datos PostgreSQL y también lo almacena en Redis a través de un mensaje insert. La aplicación tiene los siguientes componentes:

    - *Configuración de la aplicación:* Se importan los módulos **keys,** **express,** **body-parser,** **cors,** **pg,** y **redis.** Se crea una instancia de la aplicación Express y se configuran middlewares para permitir el manejo de solicitudes CORS y el análisis de JSON.
    - *Configuración de la base de datos:* Se crea una instancia de **pgClient** para conectarse a una base de datos PostgreSQL y se usa para crear una tabla llamada **values** en la base de datos.
    - *Configuración de Redis:* Se crea una instancia de **redisClient** y otra de **redisPublisher** para conectarse a un servidor Redis. El cliente se duplica para asegurarse de que siempre haya una conexión disponible.
    - *Manejadores de ruta:* Se definen varias rutas HTTP:
        1. **GET /:** Devuelve una respuesta de "Hola".
        2. **GET /values/all:** Obtiene los valores almacenados en la base de datos PostgreSQL y los devuelve como una respuesta JSON.
        3. **GET /values/current:** Obtiene los valores almacenados en Redis y los devuelve como una respuesta JSON.
        4. **POST /values:** Inserta un nuevo valor en la base de datos y en Redis. Si el índice enviado en la solicitud es mayor que 40, se devuelve una respuesta de error con un estado HTTP 422.

Finalmente, la aplicación escucha en el puerto 5000 y registra un mensaje en la consola para indicar que está escuchando.
  

- **keys.js:** El código exporta un objeto con propiedades que corresponden a las variables de entorno de Redis y PostgreSQL. Estas variables son obtenidas a través del objeto **process.env** de Node.js, que proporciona acceso a las variables de entorno del sistema operativo. El objeto exportado puede ser importado y utilizado en otros archivos de Node.js para acceder a estas variables.


- **package.json:** Este es un archivo **package.json** utilizado en un proyecto de Node.js para describir las dependencias y los scripts del proyecto.

En este caso, las dependencias incluyen **express,** **pg,** **redis,** **cors,** **nodemon,** y **body-parser.** Estas son las bibliotecas que se utilizarán en el proyecto.
Los scripts incluyen **dev** y **start.** El script **dev** inicia el servidor con **nodemon,** que es una herramienta de reinicio automático para el servidor Node.js. El script **start** inicia el servidor de Node.js sin **nodemon.**

---  

### **worker**
- **Dockerfile.dev:** Este código es un archivo Dockerfile que se utiliza para construir una imagen de Docker.
La imagen se basa en la imagen "node:alpine", lo que significa que está utilizando una versión ligera de la imagen base de Node.
  
    - El comando **"WORKDIR"** establece el directorio de trabajo para la aplicación en **"/app".**
    - El comando **"COPY"** copia el archivo **"package.json"** al directorio de trabajo actual.
    - El comando **"RUN"** ejecuta el comando **"npm install"** en el directorio actual, lo que instala todas las dependencias necesarias para la aplicación.
    - El segundo comando **"COPY"** copia todo el contenido de la aplicación al directorio actual.
    - Por último, el comando **"CMD"** inicia la aplicación con el comando **"npm run dev",** que se especifica en el archivo **"package.json".**
  
  
- **index.js:** Este código es parte de una aplicación para calcular la serie Fibonacci. La función **fib(index)** calcula el número de Fibonacci para un índice dado.

Luego, se utiliza Redis como base de datos en memoria para almacenar los índices y sus respectivos números de Fibonacci. El cliente de Redis se crea utilizando las credenciales de conexión definidas en el archivo **keys.js.**
El objeto **sub** se utiliza para suscribirse al canal "insert" en Redis, lo que significa que escuchará los mensajes que se publiquen en ese canal. Cuando se recibe un mensaje en el canal "insert", se calcula el número de Fibonacci correspondiente y se guarda en la base de datos Redis utilizando el índice como clave y el número de Fibonacci como valor.

En resumen, este código escucha los mensajes publicados en el canal "insert" de Redis y calcula el número de Fibonacci correspondiente para el índice recibido, que se almacena en Redis.
  

- **keys.js:** Este módulo de Node.js exporta un objeto que contiene dos propiedades: **redisHost** y **redisPort.** El valor de cada propiedad se asigna utilizando el objeto **process.env,** que permite acceder a las variables de entorno del sistema operativo. En este caso, el código espera que existan dos variables de entorno llamadas **REDIS_HOST** y **REDIS_PORT,** y asigna sus valores a las propiedades correspondientes del objeto que se exporta. Esto significa que cuando se utiliza el módulo **keys** en otro archivo de Node.js, se puede acceder a las propiedades **redisHost** y **redisPort** y utilizar sus valores para conectarse a un servidor de Redis.


- **package.json:** El código se trata de un archivo package.json, el cual se utiliza para definir las dependencias y scripts necesarios para un proyecto Node.js.

Las dependencias definidas son **nodemon** y **redis.** **nodemon** es una herramienta que se utiliza para monitorear cambios en los archivos del proyecto y reiniciar automáticamente el servidor. **redis** es una base de datos en memoria que se utiliza para almacenar información de forma rápida y eficiente.
Los scripts definidos son **start** y **dev.** El script **start** se utiliza para iniciar el servidor Node.js mediante el comando **node index.js.** El script **dev** se utiliza durante el desarrollo para iniciar el servidor con **nodemon,** lo que permite que el servidor se reinicie automáticamente cada vez que se realizan cambios en el código.

---
  
