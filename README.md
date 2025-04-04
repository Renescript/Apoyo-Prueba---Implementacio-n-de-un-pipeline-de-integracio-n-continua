# Integrantes equipo:
- Sandrino Escobar

# Proyecto

Este proyecto muestra una API básica de Node.js para gestionar tareas, integrada con Docker para la contenerización y Jenkins para el pipeline de CI/CD.

## Capacidades de la API

- Listar todas las tareas
- Obtener una tarea por ID

## Correr de manera local

1. Instalar dependencias: `npm install`  
2. Correr el servidor: `npm start`

## Correr con Docker

1. Construir la imagen: `docker build -t task-api .`  
2. Correr el contenedor: `docker run -p 3000:3000 task-api`

Resultado Test en jenkins:

Primero, intencionalmente hicimos fallar los tests para que la pipeline fallara:

<img width="1180" alt="test-failed" src="https://github.com/user-attachments/assets/d3ed9b60-6f5d-45d4-a4af-f85122c30b00" />

<img width="1293" alt="test-failed2" src="https://github.com/user-attachments/assets/f2b22af8-a066-4edf-b6f1-07a752c38e1e" />

Luego con los tests pasando:

<img width="1352" alt="test-passed" src="https://github.com/user-attachments/assets/011c9af7-eaf0-4f29-9047-2ef49f635fcf" />

La pipeline se completa exitosamente:

<img width="1418" alt="pipeline-succeeded1" src="https://github.com/user-attachments/assets/bd6f3c85-07db-43ff-a400-528ba5939559" />

<img width="1423" alt="pipeline-succeeded2" src="https://github.com/user-attachments/assets/ff25714c-f2e1-40d5-89fe-7273b116455c" />

Y con eso la imagen queda corriendo exitosamente para poder hacer pruebas con Postman:

<img width="865" alt="postman1" src="https://github.com/user-attachments/assets/80a7508e-8216-4c84-a14e-9e27495cfad9" />

<img width="873" alt="postman2" src="https://github.com/user-attachments/assets/10e59b13-c994-4401-b5cf-ac8502fcd6cc" />



