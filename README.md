# Lista de Tareas Pendientes con Vue.js

## Descripción

Este proyecto es una aplicación de lista de tareas pendientes desarrollada con Vue.js. Permite a los usuarios agregar, visualizar y gestionar tareas de manera eficiente. Las tareas se organizan cronológicamente y se almacenan en el `localStorage` del navegador para asegurar la persistencia de datos entre sesiones.

## Características

- **Agregar Tareas**: Los usuarios pueden agregar nuevas tareas con una descripción y una categoría (Personal o Trabajo).
- **Persistencia de Datos**: Las tareas y el nombre del usuario se guardan en `localStorage`, manteniendo la información al recargar la página.
- **Visualización de Tareas**: Las tareas se muestran en orden cronológico ascendente basado en la fecha de creación.
- **Edición del Nombre del Usuario**: El nombre del usuario se puede editar haciendo clic sobre el texto, cambiando entre un `span` y un `input` editable para una mejor experiencia de usuario.
- **Interfaz Reactiva**: Utiliza la reactividad de Vue.js para actualizar automáticamente la interfaz de usuario cuando cambian los datos.

## Tecnologías Utilizadas

- **Vue.js**: Framework de JavaScript utilizado para construir la interfaz de usuario.
- **HTML/CSS**: Para la estructura y el diseño de la aplicación.
- **localStorage**: Para almacenar los datos de manera persistente en el navegador.

## Instalación

1. Clona el repositorio:
   ```bash
   git clone https://github.com/Omarsx1/TodoList-_App.git


## Instala las dependencias:

npm install

## Inicia el servidor de desarrollo:

npm run dev

## Uso

Abre la aplicación en tu navegador en http://localhost:3000 (o la URL que indique tu terminal).

Introduce tu nombre en el campo correspondiente.

Agrega nuevas tareas proporcionando una descripción y seleccionando una categoría.

Las tareas se almacenarán y mostrarán en orden cronológico.

- **Contribución**

¡Las contribuciones son bienvenidas! Si deseas mejorar este proyecto, por favor sigue estos pasos:

Haz un fork del proyecto.

Crea una nueva rama (git checkout -b feature/nueva-caracteristica).

Realiza los cambios necesarios y haz commit (git commit -m 'Agrega nueva característica').

Sube tus cambios (git push origin feature/nueva-caracteristica).

Abre un Pull Request.
