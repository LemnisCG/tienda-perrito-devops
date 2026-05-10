# Etapa 1: Construcción (Builder)
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install --production
COPY . .

# Etapa 2: Producción (Capas limpias y usuario no root)
FROM node:18-alpine
WORKDIR /app
# Copiamos solo lo necesario desde la etapa builder
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/server.js ./
COPY --from=builder /app/package.json ./

# Cambiamos al usuario no root 'node' por seguridad
USER node

EXPOSE 3001
CMD ["npm", "start"]