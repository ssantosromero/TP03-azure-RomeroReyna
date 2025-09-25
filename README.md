# TP03 - Introducción a Azure DevOps

## Información del Estudiante
- **Nombre:** Santos Romero Reyna
- **Materia:** Ingeniería de Software III
- **Año:** 2025

## Acceso al Proyecto de Azure DevOps

### URLs del Proyecto
- **Organización:** https://dev.azure.com/tp03-ingsoft-RomeroReyna
- **Proyecto Principal:** https://dev.azure.com/tp03-ingsoft-RomeroReyna/Sample01
- **Proyecto con Repositorio:** https://dev.azure.com/tp03-ingsoft-RomeroReyna/Sample02

### Credenciales de Acceso
- **Usuario:** santosromeroreyna@hotmail.com
- **Acceso:** Mediante invitación o solicitar acceso al propietario

## Estructura del Proyecto

### Work Items Organizados
- **Epic:** Sistema de Gestión de Usuarios Web (ID: 3)
- **User Stories:**
  - Como usuario quiero registrar una cuenta nueva (ID: 4)
  - Como usuario quiero iniciar sesión en el sistema (ID: 5) 
  - Como administrador quiero gestionar perfiles de usuarios (ID: 6)

### Sprints Configurados
- **Sprint 1:** 25/09/2025 - 09/10/2025 (14 días)
- **Sprint 2:** 10/10/2025 - 23/10/2025 (14 días)

## Repositorio y Control de Versiones

### Repositorio Importado
- **Nombre:** SimpleWebAPI
- **Origen:** https://github.com/ingsoft3ucc/SimpleWebAPI.git
- **Tecnología:** ASP.NET Core Web API

### Instrucciones para Clonar
```bash
git clone https://dev.azure.com/tp03-ingsoft-RomeroReyna/Sample02/_git/SimpleWebAPI
cd SimpleWebAPI
```

### Configuración de Autenticación
1. Crear Personal Access Token en Azure DevOps
2. Usar el token como password al clonar
3. Usuario: santosromeroreyna@hotmail.com

## Branches y Pull Requests

### Branches Creados
1. **feature/add-logging**
   - Vinculado a User Story 5 (login)
   - Cambios: Actualización de README con funcionalidad de login

2. **feature/update-controller**  
   - Vinculado a User Story 6 (administración)
   - Cambios: Actualización de WeatherForecastControllerTests.cs

### Políticas de Branch Configuradas
- **Require minimum reviewers:** 1
- **Check for linked work items:** Habilitado
- **Require pull request before merge:** Habilitado

### Pull Requests Completados
- **PR #1:** Agregue funcionalidad login (feature/add-logging → main)
- **PR #2:** Updated WeatherForecastControllerTests.cs (feature/update-controller → main)

## Pipelines y Builds

### Estado de Pipelines
- Build automático configurado mediante archivo .github/workflows
- Pipelines ejecutados exitosamente en cada Pull Request

## Evidencia de Funcionamiento

### Capturas Incluidas
1. **Board con Work Items:** Epic y User Stories organizados en Sprint
2. **Pull Requests:** Ambos PRs con políticas aplicadas
3. **Branch Policies:** Configuración de revisores requeridos
4. **Work Item Linking:** PRs vinculados a User Stories

## Problemas Encontrados y Soluciones

### Problema 1: Autenticación Git
- **Issue:** Error de autenticación al clonar repositorio
- **Solución:** Creación de Personal Access Token y configuración como password

### Problema 2: Multiple PRs desde mismo branch
- **Issue:** No se podía crear segundo PR desde feature/add-logging
- **Solución:** Creación de segundo branch feature/update-controller desde main

### Problema 3: Jerarquía de Work Items
- **Issue:** Dificultad para vincular User Stories al Epic
- **Solución:** Uso de "Related Work" > "Add link" > "Parent" en el Epic

## Estructura del Proyecto

```
Sample01/
├── Work Items (Epic + User Stories + Tasks + Bugs)
├── Sprints (2 semanas cada uno)
└── Metodología Agile

Sample02/  
├── SimpleWebAPI/ (código importado)
├── Branches (main, feature/add-logging, feature/update-controller)
├── Pull Requests (con políticas aplicadas)
└── Branch Policies (reviewers + work item linking)
```

## Conclusiones del TP

Este trabajo práctico permitió aplicar los conceptos fundamentales de Azure DevOps:

1. **Organización del trabajo** mediante Boards y metodología Agile
2. **Control de versiones** con branches, PRs y políticas
3. **Trazabilidad** vinculando código con work items
4. **Colaboración** mediante procesos de code review

El proyecto demuestra un flujo completo de DevOps desde la planificación hasta la entrega, cumpliendo con las mejores prácticas de desarrollo colaborativo.
