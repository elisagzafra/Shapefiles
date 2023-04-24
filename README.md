# Si tienes Mac con chip M1, la primera linea del Dockerfile es
FROM --platform=linux/and64/amd64 python:3.9.1 as base

# De lo contrario, es
FROM python:latest as base