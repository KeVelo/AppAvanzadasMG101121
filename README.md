Esta aplicación es un proyecto web sencillo que muestra noticias en tiempo real utilizando la API de NewsAPI. Los datos se actualizan automáticamente cada 10 segundos, mostrando noticias de última hora.

Características

Visualización de Noticias: Muestra el título, la descripción, y el enlace a las noticias más recientes.

Actualización Automática: Los datos se actualizan automáticamente cada 10 segundos sin necesidad de recargar la página.

Interfaz Moderna: Un diseño simple pero elegante, enfocado en la presentación clara de la información.
Tecnologías Utilizadas

React: Para el desarrollo de la interfaz de usuario.

Axios: Para realizar solicitudes HTTP a la API.

NewsAPI: Para obtener las noticias más recientes.
Requisitos
Node.js (v14 o superior)
npm (v6 o superior)


Instalación
Sigue estos pasos para instalar y ejecutar la aplicación en tu entorno local:

Clona el repositorio:

git clone https://github.com/KeVelo/AppAvanzadasMG101121.git
cd parcialnoticias

Instala las dependencias:
npm install

Configura la API Key de NewsAPI:
Obtén una API Key gratuita desde NewsAPI. Luego, crea un archivo .env en la raíz del proyecto con la siguiente línea:

REACT_APP_NEWS_API_KEY=tu_apikey

Ejecuta la aplicación:
npm start

La aplicación se abrirá en http://localhost:3000.


Descripción de la API
La aplicación utiliza la NewsAPI para obtener las noticias más recientes. NewsAPI permite obtener titulares de diversas fuentes de noticias, filtrados por país, categoría, y otras opciones.

Ejemplo de solicitud a la API:

https://newsapi.org/v2/top-headlines?country=us&apiKey=tu_apikey

Endpoint: https://newsapi.org/v2/top-headlines

Parámetros:

country: Código del país (ej. us para Estados Unidos)

apiKey: Tu clave de API de NewsAPI


Cómo se Conectó la Aplicación a la API

La aplicación se conecta a la API de NewsAPI utilizando Axios para realizar solicitudes HTTP GET. Los datos obtenidos se almacenan en el estado de React, y se actualizan automáticamente cada 10 segundos usando un temporizador.

Código de Ejemplo:

useEffect(() => {
  const obtenerNoticias = async () => {
    try {
      const respuesta = await axios.get(`https://newsapi.org/v2/top-headlines?country=us&apiKey=${process.env.REACT_APP_NEWS_API_KEY}`);
      setNoticias(respuesta.data.articles);
    } catch (error) {
      console.error("Error al obtener datos:", error);
    }
  };

  obtenerNoticias();
  const intervalo = setInterval(obtenerNoticias, 10000);

  return () => clearInterval(intervalo);
}, []);

Visualización de Datos en Tiempo Real

Los datos se visualizan en una lista que muestra el título, la descripción, y un enlace para leer más detalles de cada noticia. La aplicación actualiza esta lista automáticamente cada 10 segundos, lo que permite ver las noticias más recientes en tiempo real sin necesidad de recargar la página.