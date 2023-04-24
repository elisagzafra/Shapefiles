# Si tienes Mac con chip M1, la primera linea del Dockerfile es
FROM --platform=linux/amd64 python:latest as base

# De lo contrario, es
FROM python:latest as base