# Si tienes Mac con chip M1, la primera linea del Dockerfile es
FROM --platform=linux/amd64 python:latest as base

# De lo contrario, es
FROM python:latest as base

# Para ejecutar el proyecto, correr este comando en la terminal:
docker-compose up --build

# Tarea:
1. Copia el archivo tarea_shp que esta adentro de la carpeta tareas
2. Pegalo en esa misma carpeta y a la copia cambiale el nombre para que se vea como tarea_shp_tunombre (no borrar archivo original)
3. Resuelve los ejercicios en el archivo que creaste
4. Haz un pull request