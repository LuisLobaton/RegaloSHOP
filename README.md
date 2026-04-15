# RegaloShop – Plataforma E-commerce lista para producción

RegaloShop es una solución full-stack para lanzar una tienda de regalos y ropa con catálogo, carrito y flujo básico de checkout. Incluye infraestructura lista para AWS (VPC, ALB, ECS Fargate, autoscaling) y un pipeline reproducible para construir imágenes y desplegarlas de extremo a extremo.

## Arquitectura y componentes
- **Frontend**: SPA React + Vite servida por Nginx (`frontend/`), comunica con la API usando `/api`.
- **Backend**: API REST Express.js con PostgreSQL (`backend/`), incluye seeds y migraciones.
- **Infraestructura**: Terraform (`infra/terraform/`) define VPC privada con dos AZ, NAT Gateway, ALB público, ECS Fargate para frontend/backend, políticas de autoscaling por CPU y Requests.
- **Contenedores & despliegue**: Ansible (`infra/ansible/`) construye imágenes Docker, las publica en ECR y, opcionalmente, fuerza despliegues en ECS.

## Requisitos previos
- Node.js 18+ y npm 9+
- Docker 24+ (para build local y push a ECR)
- PostgreSQL 14+ (local o gestionado)
- Terraform 1.5+
- Ansible 2.14+
- AWS CLI v2 con credenciales que permitan administrar ECR/ECS/VPC/ALB
