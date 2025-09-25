# Decisiones de Desarrollo - TP03 Azure DevOps

## 1. Configuración Inicial del Proyecto

1) Creé la organización en Azure DevOps:
- **Nombre elegido:** tp03-ingsoft-RomeroReyna

2) Configuré el proyecto Sample01:
```bash
# En Azure DevOps > + New Project
# Project name: Sample01
# Visibility: Private
# Work item process: Agile
```

**Metodología elegida:** Agile
**Justificación:** Agile me da Epic, User Stories, Tasks y Bugs. Basic solo tiene Issues y Tasks, sin Epics ni User Stories. Para cumplir el TP necesitaba crear específicamente Epics y User Stories.

3) Configuré los sprints:
```bash
# Project Settings > Boards > Team configuration > Iterations
Sprint 1: 25/09/2025 - 09/10/2025 (14 días)
Sprint 2: 10/10/2025 - 23/10/2025 (14 días)
```

**Por qué 2 semanas:** Cumple exactamente el requisito del TP y es duración estándar en la industria.

## 2. Gestión del Trabajo con Azure Boards

4) Creé la estructura de Work Items:
```bash
# Boards > Work Items > + New Work Item
Epic 3: Sistema de Gestión de Usuarios Web
├── User Story 4: Como usuario quiero registrar una cuenta nueva
├── User Story 5: Como usuario quiero iniciar sesión en el sistema  
└── User Story 6: Como administrador quiero gestionar perfiles de usuarios
```

5) Vinculé User Stories al Epic:
```bash
# En Epic > Related Work > Add link > Parent
# Seleccioné cada User Story individualmente
```

**Por qué esta estructura:** Epic coherente que cubre flujo completo (registro → login → administración). Cada User Story orientada a un rol específico.

6) Asigné work items al Sprint 1:
```bash
# En cada work item > Iteration > Sample01\Iteration 1\Sprint 1
```

## 3. Control de Versiones con Azure Repos

7) Creé proyecto Sample02 para el repositorio:
```bash
# + New Project
# Project name: Sample02
# Work item process: Agile
```

8) Importé repositorio desde GitHub:
```bash
# Sample02 > Repos > Files > Import repository
# Clone URL: https://github.com/ingsoft3ucc/SimpleWebAPI.git
# Repository name: SimpleWebAPI
```

**Por qué SimpleWebAPI:** Código real ASP.NET Core, no dummy code. Tiene tests y estructura para demostrar branching real.

9) Configuré políticas de branch:
```bash
# Repos > Branches > main > ... > Branch policies
✓ Require minimum reviewers: 1
✓ Check for linked work items: Enabled  
✓ Require pull request before merge: Enabled
```

**Justificación:** Estas políticas garantizan calidad del código y trazabilidad completa entre work items y cambios.

10) Creé feature branches:
```bash
# Repos > Branches > + New branch
# Name: feature/add-logging
# Based on: main
# Work items to link: User Story 5
```

11) Hice cambios y commits:
```bash
# Edité README.md agregando "Hola estoy editando esto"
# Commit message: "Updated README.md"
# Work item vinculado: User Story 5
```

12) Creé Pull Request:
```bash
# Repos > Pull requests > + New pull request
# Source: feature/add-logging
# Target: main
# Title: "Agregue funcionalidad login"
# Description: "Login para autentificacion de usuarios"
```

13) Repetí proceso para segundo branch:
```bash
# feature/update-controller vinculado a User Story 6
# Cambios en WeatherForecastControllerTests.cs
# PR: "Updated WeatherForecastControllerTests.cs"
```

## 4. Problemas Encontrados y Soluciones

### Problema 1: Autenticación Git
**Issue:** Error "Authentication failed" al intentar clonar
**Solución aplicada:**
```bash
# 1. Generé Personal Access Token en Azure DevOps
# 2. Usé token como password en lugar de contraseña normal
# Username: santosromeroreyna@hotmail.com
# Password: [personal access token]
```

### Problema 2: Jerarquía Work Items  
**Issue:** No encontraba campo "Parent" al crear User Story
**Solución:** Ir al Epic → Related Work → "Add an existing work item as a parent" → Seleccionar cada User Story

### Problema 3: Multiple PRs desde mismo branch
**Issue:** "An active pull request already exists between the selected branches"
**Solución:** Creé segundo branch (feature/update-controller) desde main para el segundo PR

### Problema 4: Configuración de branch policies
**Issue:** Los PRs no requerían aprobación inicialmente
**Solución:** Configuré policies desde Repos > Branches > main > Branch policies

## 5. Evidencia de Funcionamiento

14) Estados finales de Pull Requests:
```bash
# PR #1: feature/add-logging → main
✓ Work items must be linked: User Story 5
⏳ At least 1 reviewer must approve
✓ No merge conflicts

# PR #2: feature/update-controller → main  
✓ Work items must be linked: User Story 6
⏳ At least 1 reviewer must approve
✓ No merge conflicts
```

15) Board con work items organizados:
```bash
Epic 3: Sistema de Gestión de Usuarios Web (Sprint 1)
├── User Story 4: Como usuario quiero registrar una cuenta nueva (New)
├── User Story 5: Como usuario quiero iniciar sesión en el sistema (New)  
└── User Story 6: Como administrador quiero gestionar perfiles de usuarios (New)
```

## 6. Reflexión: Aplicación Real en Equipos de Desarrollo

### Lo que aplicaría del TP:
- **Work items claros** como hice: Epic → User Stories con descripciones específicas
- **Branch por funcionalidad** - evita que se pise el código entre compañeros  
- **Pull Requests obligatorios** - que otro revise tu código antes de subir a main
- **Políticas de branch** como configuré - garantiza calidad antes del merge

### Herramientas que investigaría:
- **Azure Pipelines** para que corra tests automáticamente cuando hago push
- **SonarQube** que detecta bugs y code smells automáticamente
- **Work item templates** para estandarizar User Stories en el equipo
- **Branch naming conventions** como feature/, hotfix/, release/

### Reglas que establecería:
- **main siempre tiene que funcionar** - nada roto en producción
- **Code review de al menos 1 persona** - 4 ojos ven más que 2
- **Linking obligatorio** work items ↔ PRs para trazabilidad
- **Definition of Done** clara para cada User Story

### Para proyectos grandes:
- **Epic por módulo** - cada dev se enfoca en su area
- **Sprint planning** con Azure Boards para organizar backlog
- **Daily standups** tracking por work items asignados
- **Automated testing** que se ejecute en cada PR

### Por qué elegí este flujo:
Me permitió aplicar DevOps end-to-end: desde planificación ágil (Boards) hasta entrega controlada (Repos con policies). La trazabilidad work item → branch → PR → code es clave para equipos reales.

**Tiempo total invertido:** ~2 horas
**Valor del ejercicio:** Dominar Azure DevOps como plataforma integrada, no herramientas separadas.
