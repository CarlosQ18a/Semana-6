# Informe del Proyecto: Despliegue de Aplicación Frontend con Backend Simulado usando Docker

## 1. Título  
**Despliegue y prueba de una aplicación frontend React conectada a un backend simulado (mockAPI) utilizando Docker y Docker Compose**

## 2. Fundamentos

Este proyecto tiene como finalidad simular un entorno de desarrollo moderno donde se integran un frontend y un backend, desplegados a través de contenedores Docker. El backend se simula con json-server, una herramienta ligera que permite crear una API REST completa a partir de un archivo JSON. El frontend se desarrolla con React y es servido desde un contenedor NGINX.

Se aplicaron los siguientes conceptos:
- Contenerización de aplicaciones frontend con Docker, optimizando su despliegue y escalabilidad.
- Simulación de backend REST mediante json-server, útil para pruebas en fases tempranas del desarrollo.
- Manejo de puertos expuestos y enlaces entre contenedores, permitiendo la comunicación entre servicios independientes.
- Uso de Docker Compose (opcionalmente) para facilitar el manejo de múltiples contenedores.
- Solución de errores comunes como conflictos de puertos y fallos de conexión entre servicios.
- Trabajo con GitHub para clonar y configurar repositorios de forma colaborativa.

## 3. Conocimientos Previos Requeridos
- Conceptos básicos de contenedores Docker (imágenes, volúmenes, puertos).
- Uso de la línea de comandos para clonar repositorios con Git.
- Familiaridad con Node.js y gestión de paquetes con npm.
- Conocimientos en el desarrollo de aplicaciones frontend (React).
- Comprensión de cómo funciona una API REST y cómo se consumen desde el frontend.

## 4. Objetivos del Proyecto
- Clonar un repositorio de backend simulado y levantarlo con json-server.
- Clonar el repositorio del frontend y ejecutar el proyecto localmente para verificar su funcionamiento.
- Crear un archivo Dockerfile que permita contenerizar el frontend.
- Construir la imagen Docker del frontend y ejecutarla exponiéndola en el puerto 3000.
- Comprobar que el frontend desplegado consume correctamente los datos del backend simulado.
- 
## 5. Equipos y Herramientas Necesarias
- PC con Docker y Docker Compose instalados.
- Git para la gestión de versiones y clonación de repositorios.
- Node.js y npm para ejecutar el backend simulado.
- Editor de código, como Visual Studio Code.
- Navegador web moderno para validar resultados.

## 6. Material de apoyo

- [Repositorio Backend MockAPI](https://github.com/Daviddotcoms/mockAPI)  
- Documentación oficial de Docker: [https://docs.docker.com/](https://docs.docker.com/)  
- json-server: [https://github.com/typicode/json-server](https://github.com/typicode/json-server)  

## 7. Procedimiento
### Paso 1: Clonación y ejecución del backend simulado
```bash
git clone https://github.com/Daviddotcoms/mockAPI.git
cd mockAPI
npm install
npm start
```
<img src = "MOCKAPI/Captura de pantalla 2025-05-16 085452.png" width = "400">


El backend simulado queda disponible en: http://localhost:3100

Endpoints disponibles:
- `/classmates`
- `/teachers`
<img src = "MOCKAPI/Captura de pantalla 2025-05-16 090516.png" width = "400">

## Paso 2: Clonación y prueba del frontend en modo desarrollo

Se clonó el proyecto frontend (repositorio externo o personal).

Se ejecutó con:
```bash
npm install
npm run dev
```
Se verificó que el frontend accediera correctamente a http://localhost:3100.

## Paso 3: Creación del archivo Dockerfile para el frontend

Este Dockerfile realiza una construcción por etapas. La primera construye la app con React y la segunda sirve los archivos estáticos desde NGINX.


<img src = "" width = "400">

<img src = "" width = "400">

## Paso 4: Construcción de la imagen Docker

```bash
docker build -t suda-frontend .
```

<img src = "" width = "400">
## Paso 5: Ejecución del contenedor del frontend
```bash
docker run -d -p 3000:80 suda-frontend
```
<img src = "" width = "400">

El puerto 3000 fue elegido para evitar conflictos con el puerto 8080 previamente ocupado.

## Paso 6: Verificación de la comunicación entre frontend y backend

Se accedió a http://localhost:3000 y se verificó que la aplicación mostraba correctamente la información del backend mockAPI.
En caso de errores CORS o fallos de red, se revisaron las rutas y configuraciones del fetch/Axios en el código frontend.

<img src = "" width = "400">

## 8. Resultados Obtenidos

- Backend corriendo estable en http://localhost:3100, respondiendo a peticiones GET.
- Frontend desplegado correctamente mediante Docker, visible en http://localhost:3000.
- Comunicación exitosa entre ambos servicios, con datos mostrados en la interfaz.
- Se resolvió el conflicto de puerto cambiando la exposición de 8080 a 3000.
  
<img src = "" width = "400">

<img src = "" width = "400">


## 9. Bibliografía

- Docker, Inc. (2024). Documentación oficial de Docker.
Recuperado de: https://docs.docker.com/

- Typicode. (2024). json-server: Fake REST API.
Recuperado de: https://github.com/typicode/json-server

- ReactJS. (2024). Documentación oficial de React.
Recuperado de: https://react.dev/

- Node.js Foundation. (2024). Documentación oficial de Node.js.
Recuperado de: https://nodejs.org/en/docs

- GitHub, Inc. (2024). Repositorio mockAPI utilizado en el proyecto.
Recuperado de: https://github.com/Daviddotcoms/mockAPI

- NGINX. (2024). Using NGINX for serving static files.
Recuperado de: https://docs.nginx.com/

