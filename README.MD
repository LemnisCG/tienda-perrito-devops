# Innovatech Chile - Tienda de Perritos (Docker & CI/CD)

Este repositorio contiene la infraestructura como código para el despliegue automatizado de la aplicación mediante contenedores, orquestación y flujos CI/CD en AWS.

## Estructura del Proyecto
- **/frontend**: SPA sencilla servida a través de Nginx (Dockerfile Multi-stage).
- **/backend**: API REST desarrollada en Node.js y Express (Usuario no root).
- **/db**: Base de datos MySQL con script de inicialización automática.
- **.github/workflows**: Pipelines de automatización para despliegue continuo en EC2.

## Ejecución Local
Para levantar el stack completo de microservicios en un entorno local, asegúrate de tener Docker instalado y ejecuta en la raíz del proyecto:
\`\`\`bash
docker-compose up -d --build
\`\`\`
Los servicios estarán disponibles en:
- Frontend: http://localhost:80
- Backend: http://localhost:3001

## Despliegue en AWS
El despliegue está completamente automatizado mediante GitHub Actions. Al realizar un \`push\` hacia la rama \`deploy\`, el pipeline:
1. Construye las imágenes Docker.
2. Sube las imágenes a Amazon ECR.
3. Actualiza y ejecuta los contenedores en las instancias EC2 correspondientes mediante AWS Systems Manager (SSM) asd.