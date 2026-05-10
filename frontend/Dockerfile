# Etapa 1: Preparación (Builder)
FROM alpine:latest AS builder
WORKDIR /app
COPY index.html app.js default.conf ./

# Etapa 2: Producción
FROM nginx:alpine
# Limpiamos el contenido por defecto
RUN rm -rf /usr/share/nginx/html/*
# Copiamos desde el builder
COPY --from=builder /app/index.html /app/app.js /usr/share/nginx/html/
COPY --from=builder /app/default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80