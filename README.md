<div align="center">

# 🏢 Lobo Alquileres

**SaaS multi-tenant para administrar alquileres: inmuebles, contratos, cuotas y ajustes por inflación.**

![Java](https://img.shields.io/badge/Java-17-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-compose-2496ED?style=flat-square&logo=docker&logoColor=white)

</div>

## Qué resuelve

Una inmobiliaria o un propietario con varias unidades suele llevar contratos, vencimientos y aumentos en planillas. Lobo Alquileres centraliza todo en una aplicación web donde cada organización (*tenant*) ve únicamente sus propios datos.

## Funcionalidades

- **Autenticación y roles** con JWT y Spring Security.
- **Personas** (propietarios, inquilinos) e **inmuebles**.
- **Contratos** que generan automáticamente el cronograma de **cuotas**.
- **Registro de pagos**, estados de cuota (pagada, vencida, etc.) y gastos adicionales.
- **Motor de ajuste por inflación** (IPC / ICL) con alertas.
- **Generación de documentos en PDF**.
- **Multi-tenant** y registro de pagos de suscripción.
- **API documentada** con Swagger / OpenAPI.

## Stack

| Capa | Tecnologías |
|---|---|
| Backend | Java 17, Spring Boot 3, Spring Security, Spring Data JPA, Bean Validation, Flyway, JWT (jjwt), Lombok |
| Frontend | React 18, TypeScript, Vite, Tailwind CSS, shadcn/ui (Radix), TanStack Query, Zustand, React Hook Form + Zod, React PDF |
| Base de datos | PostgreSQL 16 con migraciones versionadas (Flyway) |
| Infra | Docker Compose (PostgreSQL + pgAdmin) |

## Arquitectura

Backend en **capas** (`controller → service → repository`), con DTOs de request/response para no exponer las entidades y la lógica de negocio aislada de HTTP. El frontend está organizado por **features**, con una capa `api/` que concentra la comunicación con el backend. El detalle completo está en [`estructura.md`](estructura.md).

## Cómo levantarlo

Necesitás **Java 17**, **Maven**, **Node 18+** y **Docker**.

```bash
# 1. Base de datos (PostgreSQL + pgAdmin)
docker compose up -d

# 2. Backend
cd lobo-alquileres-backend
mvn spring-boot:run

# 3. Frontend
cd lobo-alquileres-frontend
npm install
npm run dev
```

En Windows también podés usar `arrancar-backend.bat` y `arrancar-frontend.bat`. Las migraciones de Flyway crean el esquema y cargan datos de ejemplo al iniciar el backend.

> Las credenciales de `docker-compose.yml` son solo para desarrollo local.

## Autora

**Carolina Lobo** · [LinkedIn](https://www.linkedin.com/in/carolina-lobo-469705297) · lobocarolina99@gmail.com
