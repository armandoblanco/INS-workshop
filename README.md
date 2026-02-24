# 🏛️ Workshop: GitHub Copilot para INS

## Desarrollo Asistido por IA con .NET 8

![GitHub Copilot](https://img.shields.io/badge/GitHub%20Copilot-Enabled-green)
![.NET 8](https://img.shields.io/badge/.NET-8.0-purple)
![Duración](https://img.shields.io/badge/Duración-3%20horas-blue)

---

## 📋 Tabla de Contenidos

- [Introducción](#-introducción)
- [Conceptos Clave de GitHub Copilot](#-conceptos-clave-de-github-copilot)
- [Pre-requisitos](#️-pre-requisitos)
- [Agenda del Workshop](#-agenda-del-workshop)
- [Laboratorio 1: Especificaciones con IA](#-laboratorio-1-especificaciones-con-ia-30-min)
- [Laboratorio 2: REST API con .NET](#-laboratorio-2-rest-api-con-net-45-min)
- [Laboratorio 3: Frontend con Agente Especializado](#-laboratorio-3-frontend-con-agente-especializado-30-min)
- [Laboratorio 4: Pruebas y Documentación](#-laboratorio-4-pruebas-y-documentación-20-min)
- [Laboratorio 5: Características Avanzadas](#-laboratorio-5-características-avanzadas-15-min)
- [Referencia Rápida](#-referencia-rápida)
- [Recursos Adicionales](#-recursos-adicionales)

---

## 🎯 Introducción

Este workshop práctico te guiará en el desarrollo de un **Sistema de Registro de Seguro de Vehículos** para el INS (Grupo INS) utilizando **GitHub Copilot** como asistente de desarrollo. Aprenderás a:

- ✅ Generar especificaciones técnicas con IA
- ✅ Crear APIs REST con Minimal API
- ✅ Desarrollar frontends con estilo institucional
- ✅ Escribir pruebas unitarias automáticamente
- ✅ Crear agentes personalizados especializados
- ✅ Traducir código legacy a tecnologías modernas

### Estándares del Proyecto

| Aspecto | Estándar |
|---------|----------|
| **Tipo** | API REST |
| **Tecnología** | C# .NET 8 |
| **Arquitectura** | Minimal API |
| **Idioma** | Español (código, comentarios, documentación) |
| **Base de datos** | InMemory (sin dependencias externas) |
| **Frontend** | Blazor WebAssembly |

---

## 🧠 Conceptos Clave de GitHub Copilot

### ¿Qué es @workspace?

El **@workspace** es un participante de chat que proporciona contexto sobre todo tu espacio de trabajo (proyecto) a GitHub Copilot.

#### ¿Para qué sirve?

| Función | Ejemplo |
|---------|---------|
| **Buscar código** | `@workspace ¿dónde se define la clase Poliza?` |
| **Entender el proyecto** | `@workspace ¿qué hace este proyecto?` |
| **Encontrar patrones** | `@workspace ¿cómo se implementan los endpoints?` |
| **Generar código contextual** | `@workspace crea un nuevo endpoint similar a los existentes` |

#### ¿Cuándo usarlo?

- ✅ Cuando necesitas que Copilot entienda la estructura de tu proyecto
- ✅ Para generar código que siga los patrones existentes
- ✅ Para buscar implementaciones específicas
- ✅ Para preguntas sobre arquitectura del proyecto

#### Ejemplo práctico:

```
# Sin @workspace - Copilot no conoce tu proyecto
"Crea endpoints para pólizas de seguro"
→ Genera código genérico

# Con @workspace - Copilot analiza tu proyecto
"@workspace Crea endpoints para pólizas de seguro"
→ Genera código siguiendo TUS patrones y convenciones
```

---

### Modos de GitHub Copilot Chat

GitHub Copilot tiene **tres modos principales** de operación. Es crucial entender cuándo usar cada uno:

#### 1️⃣ Modo Ask (Preguntar) 💬

| Característica | Descripción |
|----------------|-------------|
| **Ícono** | 💬 Burbuja de mensaje |
| **Función** | Solo responde preguntas, **NO modifica archivos** |
| **Uso ideal** | Explorar, entender, planificar, aprender |

**Cuándo usar Modo Ask:**
- 🔍 Investigar cómo implementar algo
- 📚 Entender código existente
- 🤔 Comparar opciones de diseño
- 📋 Planificar antes de implementar

**Ejemplo:**
```
[Modo Ask]
"¿Cuál es la mejor forma de implementar autenticación JWT en .NET 8?"

→ Copilot EXPLICA las opciones pero NO crea archivos
```

---

#### 2️⃣ Modo Agent (Agente) 🤖

| Característica | Descripción |
|----------------|-------------|
| **Ícono** | 🤖 Robot o chispa |
| **Función** | **PUEDE crear y modificar archivos** automáticamente |
| **Uso ideal** | Implementar cambios, crear código, refactorizar |

**Cuándo usar Modo Agent:**
- ✏️ Crear nuevos archivos
- 🔧 Modificar código existente
- 🏗️ Implementar funcionalidades completas
- 🔄 Refactorizar código

**Ejemplo:**
```
[Modo Agent]
"Crea endpoints Minimal API para pólizas de seguro con operaciones CRUD"

→ Copilot CREA el archivo PolizaEndpoints.cs con todo el código
```

---

#### 3️⃣ Modo Plan (Planificar) 📋

| Característica | Descripción |
|----------------|-------------|
| **Ícono** | 📋 Lista o documento |
| **Función** | Genera un **plan detallado ANTES de ejecutar** |
| **Uso ideal** | Tareas complejas que involucran múltiples archivos |

**Cuándo usar Modo Plan:**
- 📁 Crear múltiples archivos relacionados
- 🏛️ Implementar funcionalidades que cruzan capas
- 🔍 Revisar cambios antes de aplicarlos
- ⚠️ Tareas donde quieres control sobre cada paso

**Ejemplo:**
```
[Modo Plan]
"Implementa la funcionalidad completa de Coberturas con entidad, DTOs 
y endpoints Minimal API"

→ Copilot MUESTRA el plan:
  1. Crear Cobertura.cs (entidad)
  2. Crear CoberturaDto.cs (DTOs)
  3. Crear CoberturaEndpoints.cs (Minimal API)
  4. Registrar endpoints en Program.cs

→ Tú APRUEBAS cada paso antes de que se ejecute
```

---

#### Comparativa de Modos

| Aspecto | Ask 💬 | Agent 🤖 | Plan 📋 |
|---------|--------|----------|---------|
| Modifica archivos | ❌ No | ✅ Sí | ✅ Sí (con aprobación) |
| Velocidad | Rápido | Rápido | Más lento |
| Control | N/A | Bajo | Alto |
| Ideal para | Aprender | Implementar | Tareas complejas |
| Riesgo | Ninguno | Medio | Bajo |

---

### Agentes Personalizados (@nombre-agente)

Los **agentes personalizados** son "expertos" que puedes crear para tareas específicas. Se definen en archivos Markdown en `.github/agents/`.

#### ¿Cómo funcionan?

1. Creas un archivo `.github/agents/mi-agente.md`
2. Defines el rol, reglas y conocimiento del agente
3. Lo invocas con `@mi-agente` en el chat

#### ¿Para qué sirven?

| Uso | Ejemplo |
|-----|---------|
| **Especialización** | Agente experto en frontend con estilos INS |
| **Consistencia** | Agente que siempre sigue los estándares del equipo |
| **Revisión** | Agente que revisa código según checklist |
| **Dominio** | Agente que conoce terminología específica de seguros |

#### Ejemplo de agente:

```markdown
# .github/agents/frontend-ins.md

# Agente: Frontend INS

## Rol
Eres experto en desarrollo frontend para el Grupo INS.

## Reglas
- Usar colores institucionales (#003B71, #00A651)
- Todo el texto en español
- Componentes accesibles (WCAG AA)
```

**Uso:**
```
@frontend-ins Crea un componente de tarjeta para mostrar pólizas de seguro
```

---

### Comandos Especiales (/comando)

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `/tests` | Genera pruebas unitarias | Selecciona código → `/tests` |
| `/doc` | Genera documentación XML | Selecciona clase → `/doc` |
| `/fix` | Propone corrección de errores | Selecciona código con error → `/fix` |
| `/explain` | Explica código seleccionado | Selecciona código → `/explain` |
| `/new` | Crea nuevo archivo/proyecto | `/new crear clase Poliza` |

---

## 🛠️ Pre-requisitos

### Software Necesario

```powershell
# Verificar instalaciones
dotnet --version  # Debe ser 8.0 o superior
code --version    # Visual Studio Code
git --version     # Git
```

> **📝 NOTA:** Este taller usa **base de datos en memoria** (InMemory Database) para no requerir instalación de software adicional como SQL Server o SQLite. Los datos se pierden al reiniciar la aplicación, pero es perfecto para desarrollo y pruebas.

### Extensiones de VS Code

1. **GitHub Copilot** - Extensión principal
2. **GitHub Copilot Chat** - Chat integrado
3. **C# Dev Kit** - Soporte para .NET

### Cuenta de GitHub

- Necesitas una cuenta con acceso a GitHub Copilot
- Puede ser licencia individual, de organización o educativa

---

## 📅 Agenda del Workshop

| Tiempo | Módulo | Descripción | Modo Copilot |
|--------|--------|-------------|--------------|
| 0:00 - 0:15 | Introducción | Setup y configuración | - |
| 0:15 - 0:45 | Lab 1 | Especificaciones y diseño | **Ask** → **Agent** |
| 0:45 - 1:30 | Lab 2 | REST API para seguros de vehículos | **Agent** + **Plan** |
| 1:30 - 1:45 | ☕ Break | Descanso | - |
| 1:45 - 2:15 | Lab 3 | Frontend con Agente | **@frontend-ins** |
| 2:15 - 2:35 | Lab 4 | Pruebas y documentación | **Agent** |
| 2:35 - 2:50 | Lab 5 | Agentes y traducción | **Custom Agents** |
| 2:50 - 3:00 | Cierre | Q&A y recursos | - |

---

## 🔬 LABORATORIO 1: Especificaciones con IA (30 min)

### Objetivos
- ✅ Usar Modo Ask para explorar y diseñar
- ✅ Cambiar a Modo Agent para crear archivos
- ✅ Generar especificaciones técnicas completas

---

### Paso 1.1: Crear estructura inicial

**🤖 PROMPT en Modo Agent:**

```
Crea la estructura de carpetas inicial para el proyecto:
- docs/especificaciones
- src
- .github/agents
```

**📝 Alternativa manual (si el agente no ejecuta los comandos):**

```powershell
mkdir -p docs/especificaciones
mkdir -p src
mkdir -p .github/agents
```

---

### Paso 1.2: Explorar con MODO ASK 🔍

> **💡 IMPORTANTE:** Asegúrate de estar en **Modo Ask** (ícono de mensaje 💬 en Copilot Chat). Este modo NO modifica archivos, solo responde preguntas.

**📍 Cómo activar Modo Ask:**
1. Abre Copilot Chat (`Ctrl+Shift+I`)
2. Busca el selector de modo en la parte superior
3. Selecciona "Ask" o el ícono de mensaje

**🤖 PROMPT - Copia y pega en Copilot Chat:**

```
Soy arquitecto de software en el Grupo INS (Instituto Nacional de Seguros de Costa Rica) y necesito diseñar un sistema de registro de seguro de vehículos. 

Ayúdame a entender:

1. ¿Qué entidades principales necesitaría para un sistema que gestione:
   - Diferentes tipos de seguros de vehículos (Responsabilidad Civil, Comprensivo, Todo Riesgo, Básico)
   - Coberturas con diferentes tipos y montos
   - Registro de vehículos con datos técnicos (placa, marca, modelo, chasis)
   - Datos de asegurados con ubicación por provincia y cantón
   - Gestión de reclamos
   - Estadísticas agregadas por provincia

2. ¿Qué endpoints REST serían necesarios?

3. ¿Cómo organizar esto usando Minimal API de .NET 8?

4. ¿Qué consideraciones de seguridad debo tener para datos de seguros y datos personales?
```

**📝 Observa:** Copilot responde con información detallada pero **NO crea ningún archivo**. Esto es ideal para la fase de exploración.

---

### Paso 1.3: Refinar el diseño con preguntas de seguimiento

> **💡 NOTA:** Seguimos en Modo Ask para profundizar en el diseño.

**🤖 PROMPT de seguimiento:**

```
Gracias. Ahora explícame con más detalle:

1. ¿Cómo organizarías la funcionalidad de Pólizas usando Minimal API de .NET 8?
   - Muéstrame la estructura de carpetas
   - ¿Qué archivos tendría cada funcionalidad?

2. ¿Cómo agrupar los endpoints con MapGroup?

3. Dame un ejemplo de cómo se vería un endpoint POST para crear una póliza de seguro con Minimal API
```

---

### Paso 1.4: Cambiar a MODO AGENT para implementar 🤖

> **💡 IMPORTANTE:** Ahora cambia a **Modo Agent** (ícono de robot 🤖). Este modo **PUEDE crear y modificar archivos**.

**📍 Cómo activar Modo Agent:**
1. En Copilot Chat, busca el selector de modo
2. Selecciona "Agent" o el ícono de robot/chispa

**🤖 PROMPT en Modo Agent:**

```
Ahora sí, crea la especificación técnica completa del sistema.

Crea el archivo docs/especificaciones/especificacion-sistema.md con:

1. **Visión General**
   - Sistema REST API + Frontend para gestionar registro de seguros de vehículos del Grupo INS
   
2. **Estándares Técnicos**
   | Aspecto | Estándar |
   |---------|----------|
   | Tipo | API REST |
   | Tecnología | C# .NET 8 |
   | Arquitectura | Minimal API (.NET 8) |
   | Idioma | Español |

3. **Requisitos Funcionales**
   - CRUD de pólizas de seguro (Responsabilidad Civil, Comprensivo, Todo Riesgo, Básico)
   - Registro de vehículos con datos técnicos (placa, marca, modelo, año, chasis)
   - Gestión de coberturas con tipos y montos máximos
   

4. **Modelo de Datos** (diagrama Mermaid)

5. **Estructura de carpetas del proyecto**

6. **Endpoints de la API** (tabla completa)
```

**✅ Resultado esperado:** Copilot crea el archivo `docs/especificaciones/especificacion-sistema.md` automáticamente.

---

### Paso 1.5: Crear modelo de dominio con diagrama

**🤖 PROMPT en Modo Agent:**

```
Crea el archivo docs/especificaciones/modelo-dominio.md con:

1. Diagrama Mermaid de entidad-relación para:
   - Poliza (Id, NumeroPoliza, VehiculoId, AseguradoId, TipoSeguro, FechaInicio, FechaVencimiento, Estado, MontoAsegurado, Prima)
   - Vehiculo (Id, Placa, Marca, Modelo, Anio, NumeroChasis, TipoVehiculo, Color)
   - Cobertura (Id, PolizaId, Nombre, TipoCobertura, MontoMaximo, Deducible, EsObligatoria)
   - DetalleCobertura (Id, CoberturaId, Descripcion, Valor)
   - Asegurado (Id, Cedula, NombreCompleto, Provincia, Canton, Telefono, Correo)
   - Reclamo (Id, PolizaId, FechaIncidente, Descripcion, MontoReclamado, EstadoReclamo)
   - EstadisticaProvincial (Id, Provincia, TotalPolizas, MontoTotalAsegurado)

2. Descripción de cada entidad en español

3. Reglas de negocio

4. Catálogo de tipos (TipoSeguro, TipoCobertura, EstadoPoliza, EstadoReclamo, TipoVehiculo)
```

---

### Paso 1.6: Definir contratos de API

> **💡 NOTA:** Usamos `#file:` para referenciar archivos existentes y que Copilot use ese contexto.

**🤖 PROMPT en Modo Agent:**

```
Basándote en los endpoints definidos en #file:docs/especificaciones/especificacion-sistema.md, crea el archivo docs/especificaciones/contratos-api.md con la especificación detallada.

Para cada endpoint incluye:
- Esquema de solicitud (JSON)
- Esquema de respuesta (JSON)  
- Códigos de estado HTTP
- Ejemplos de uso
```

**✅ Verificar antes de continuar:**
- [ ] Existen los 3 archivos en `docs/especificaciones/`
- [ ] Los diagramas Mermaid se renderizan correctamente en VS Code
- [ ] La tabla de endpoints está completa

---

### 🛠️ Troubleshooting Lab 1

| Problema | Solución |
|----------|----------|
| Copilot no crea archivos | Verifica que estés en **Modo Agent**, no en Modo Ask |
| Los diagramas Mermaid no se ven | Instala la extensión "Markdown Preview Mermaid Support" |
| Copilot responde en inglés | Verifica que `.github/copilot-instructions.md` esté configurado con idioma español (Lab 2.1). Si aún no lo has creado, agrega "Responde en español" al final del prompt |

---

## 🔬 LABORATORIO 2: REST API con .NET (45 min)

### Objetivos
- ✅ Crear estructura de proyecto .NET
- ✅ Implementar Minimal API
- ✅ Usar Modo Plan para tareas complejas
- ✅ Generar código siguiendo estándares

---

### Paso 2.1: Crear instrucciones de Copilot

> **⚠️ IMPORTANTE:** Este paso debe ejecutarse **ANTES** de crear código para que Copilot siga los estándares desde el inicio.

**🤖 PROMPT en Modo Agent:**

```
Crea el archivo .github/copilot-instructions.md con instrucciones para que Copilot actúe como experto en .NET para el Grupo INS:

# Instrucciones para GitHub Copilot - Proyecto INS Seguros de Vehículos

## Idioma
- Todo el código, comentarios y documentación debe estar en **español**
- Mensajes de error en español
- Nombres de variables y métodos en español (excepto palabras técnicas estándar como Get, Set, Async)

## Estándares de Código
| Aspecto | Estándar |
|---------|----------|
| Tecnología | C# .NET 8 |
| Arquitectura | Minimal API (.NET 8) |
| Async | Usar async/await en todas las operaciones I/O |
| Nullable | Nullable reference types habilitados |
| Base de datos | Entity Framework Core InMemory (sin dependencias externas) |

## Nomenclatura
- Clases y métodos públicos: PascalCase en español (Poliza, ObtenerTodas)
- Variables privadas: _camelCase
- DTOs: EntidadDto, CrearEntidadSolicitud, ActualizarEntidadSolicitud

## Estructura del Proyecto
Cada funcionalidad debe estar en: /Funcionalidades/{Nombre}/
- {Nombre}.cs (Entidad)
- {Nombre}Dto.cs (DTOs)
- {Nombre}Endpoints.cs (Minimal API endpoints con MapGroup)

## Documentación
- XML comments en español para todas las APIs públicas
- Documentar parámetros y valores de retorno

## INS Específico
- Terminología oficial: Póliza, Cobertura, Asegurado, Reclamo, Vehículo, Prima
- Códigos de provincia según división territorial de Costa Rica (01-07)
- Provincias: San José, Alajuela, Cartago, Heredia, Guanacaste, Puntarenas, Limón
- Formatos de fecha: dd/MM/yyyy para display, ISO 8601 para API

## Seguridad
- Nunca loggear datos sensibles (cédula, datos personales)
- Validar todas las entradas del usuario

## Manejo de Errores
- Retornar ProblemDetails en errores HTTP
- Loggear excepciones con contexto suficiente
```

---

### Paso 2.2: Crear la solución y proyectos

> **💡 DEMOSTRACIÓN:** Este paso muestra cómo GitHub Copilot puede interactuar con la terminal para ejecutar comandos.

**🤖 PROMPT en Modo Agent:**

```
Crea la estructura del proyecto .NET en la carpeta src:

1. Una solución llamada INS.SegurosVehiculos
2. Un proyecto Web API llamado INS.SegurosVehiculos.API con .NET 8
3. Un proyecto de pruebas xUnit llamado INS.SegurosVehiculos.Pruebas
4. Agrega los proyectos a la solución
5. Agrega la referencia del proyecto de pruebas al API

Ejecuta los comandos en la terminal
```

**✅ Observa:** Copilot debería ejecutar los comandos `dotnet` automáticamente en la terminal integrada.

**📝 Alternativa manual:**

```powershell
cd src
dotnet new sln -n INS.SegurosVehiculos
dotnet new webapi -n INS.SegurosVehiculos.API -f net8.0 --use-minimal-apis
dotnet new xunit -n INS.SegurosVehiculos.Pruebas -f net8.0
dotnet sln add INS.SegurosVehiculos.API
dotnet sln add INS.SegurosVehiculos.Pruebas
dotnet add INS.SegurosVehiculos.Pruebas reference INS.SegurosVehiculos.API
```

---

### Paso 2.3: Usar MODO PLAN para tarea compleja 📋

> **💡 IMPORTANTE:** Activa **Modo Plan** (ícono de lista 📋). Este modo genera un plan detallado ANTES de ejecutar, permitiéndote revisar y aprobar cada paso.

**📍 Cómo activar Modo Plan:**
1. En Copilot Chat, busca el selector de modo
2. Selecciona "Plan" o "Edit" con planificación

**🤖 PROMPT en Modo Plan:**

```
Basándote en la especificación #file:docs/especificaciones/especificacion-sistema.md y el modelo de dominio #file:docs/especificaciones/modelo-dominio.md, implementa la funcionalidad principal de gestión de pólizas de seguro usando Minimal API.

Crea los archivos en src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/ con:

1. **Poliza.cs** — Entidad con propiedades del modelo de dominio:
   - Enums para estados y tipos según la especificación
   - Propiedades con Data Annotations para validación

2. **PolizaDto.cs** — DTOs para transferencia de datos (PolizaDto, CrearPolizaSolicitud, ActualizarPolizaSolicitud)

3. **PolizaEndpoints.cs** — Clase estática con método de extensión MapPolizaEndpoints(this WebApplication app) usando MapGroup("/api/v1/polizas"):
   - GET / (listar)
   - GET /{id} (obtener por id)
   - POST / (crear)
   - PUT /{id} (actualizar)
   - DELETE /{id} (eliminar)
   - Usar el DbContext directamente (sin repositorio)
   - Async/await en todas las operaciones
   - Documentación con WithName y WithOpenApi

Muéstrame el plan antes de ejecutar
```

**📝 Observa el plan:** Copilot analizará las especificaciones y mostrará un plan como:

```
📋 Plan de implementación:

1. ✏️ Crear src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/Poliza.cs
   - Entidad principal con propiedades y enums

2. ✏️ Crear src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/PolizaDto.cs
   - DTOs para transferencia de datos

3. ✏️ Crear src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/PolizaEndpoints.cs
   - Endpoints Minimal API con MapGroup

¿Aprobar plan?
```

**Revisa y aprueba** cada paso del plan.

**✅ Verificar:** Después de aprobar el plan, verifica que se crearon los 3 archivos en `src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/`

---

### Paso 2.4: Implementar DbContext

**🤖 PROMPT en Modo Agent:**

```
@workspace Basándote en las entidades creadas, crea el DbContext en src/INS.SegurosVehiculos.API/Datos/:

1. DbContext para Entity Framework Core InMemory
2. DbSets para Poliza (y Vehiculo si ya existe)

3. Método público InicializarDatosSemilla() que:
   - Verifique si ya existen datos
   - Si no hay datos, agregue 3 pólizas de ejemplo
   - Guarde los cambios
```

---

### Paso 2.5: Configurar Program.cs

**🤖 PROMPT en Modo Agent:**

```
@workspace Actualiza src/INS.SegurosVehiculos.API/Program.cs para configurar:

1. Entity Framework con base de datos en memoria:
   - Usar UseInMemoryDatabase("SegurosVehiculosDb")
   - No requiere connection string externo ni instalación de BD

2. Inyección de dependencias:
   - Registrar SegurosDbContext

3. Swagger/OpenAPI con:
   - Título: "API de Seguros de Vehículos - INS"
   - Versión: v1

4. Middleware:
   - Habilitar CORS para desarrollo (permitir localhost)
   - Usar Swagger en desarrollo

5. Registrar los endpoints Minimal API:
   - app.MapPolizaEndpoints()

6. Inicializar datos semilla al arrancar:
   - Obtener el DbContext del service provider
   - Llamar al método InicializarDatosSemilla()
```

---

### Paso 2.6: Instalar paquetes NuGet necesarios

> **💡 DEMOSTRACIÓN:** Copilot puede instalar paquetes NuGet directamente.

**🤖 PROMPT en Modo Agent:**

```
Instala el paquete NuGet en el proyecto INS.SegurosVehiculos.API:
- Microsoft.EntityFrameworkCore.InMemory
```

**📝 Alternativa manual:**

```powershell
cd src/INS.SegurosVehiculos.API
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

> **📝 NOTA:** Usamos `InMemory` en lugar de SQLite o SQL Server para no requerir instalación de software adicional. Los datos se almacenan en memoria y se pierden al reiniciar, pero los datos semilla se cargan automáticamente al iniciar.

---

### Paso 2.7: Ejecutar y probar la API

> **💡 DEMOSTRACIÓN:** Copilot puede compilar y ejecutar proyectos .NET.

**🤖 PROMPT en Modo Agent:**

```
Compila y ejecuta el proyecto INS.SegurosVehiculos.API
```

**📝 Alternativa manual:**

```powershell
cd src/INS.SegurosVehiculos.API
dotnet run
```

Abre en el navegador: `https://localhost:5001/swagger` o `http://localhost:5000/swagger`

**✅ Verificar:**
- Swagger UI muestra todos los endpoints
- GET /api/v1/polizas retorna las pólizas semilla
- POST /api/v1/polizas puede crear nuevas pólizas

> **💡 Si algo falla:** Revisa la consola de VS Code para ver errores de compilación o runtime.

---

### Paso 2.8: Implementar funcionalidad de Vehículos

**🤖 PROMPT en Modo Plan:**

```
Basándote en #file:docs/especificaciones/modelo-dominio.md, implementa la funcionalidad de Vehículos con Minimal API.

Crea en src/INS.SegurosVehiculos.API/Funcionalidades/Vehiculos/:
1. Vehiculo.cs — Entidad con propiedades: Placa, Marca, Modelo, Anio, NumeroChasis, TipoVehiculo, Color
2. VehiculoDto.cs — DTOs correspondientes
3. VehiculoEndpoints.cs — Endpoints Minimal API con MapGroup("/api/v1/vehiculos")
4. Actualizar el DbContext con el nuevo DbSet
5. Registrar app.MapVehiculoEndpoints() en Program.cs

Muéstrame el plan primero
```

**✅ Verificar antes de continuar:**
- [ ] La API compila sin errores (`dotnet build`)
- [ ] Swagger muestra endpoints de Pólizas y Vehículos
- [ ] Los datos semilla se cargan al iniciar

---

### 🛠️ Troubleshooting Lab 2

| Problema | Solución |
|----------|----------|
| Error "Package not found" | Ejecuta `dotnet restore` en la carpeta del proyecto |
| DbContext no registrado | Verifica que `Program.cs` tenga `builder.Services.AddDbContext<...>` |
| Swagger no aparece | Asegúrate de que `app.UseSwagger()` esté antes de `app.Run()` |
| Puerto en uso | Cambia el puerto en `launchSettings.json` o cierra otras instancias |
| Datos semilla no aparecen | Verifica que `InicializarDatosSemilla()` se llame en `Program.cs` |

---

## 🔬 LABORATORIO 3: Frontend con Agente Especializado (30 min)

> **⚠️ PRERREQUISITO:** Este laboratorio requiere haber completado el **Laboratorio 2**. Necesitas:
> - La solución `INS.SegurosVehiculos.sln` creada
> - El proyecto `INS.SegurosVehiculos.API` funcionando
> - El archivo `.github/copilot-instructions.md` configurado

### Objetivos
- ✅ Crear un agente personalizado especializado
- ✅ Usar el agente para desarrollo frontend
- ✅ Aplicar estilos institucionales del INS
- ✅ Consumir la API REST desde Blazor

---

### Paso 3.1: Crear el Agente de Frontend (versión básica) 🤖

> **💡 CONCEPTO:** Los agentes personalizados permiten crear "expertos" especializados que Copilot puede usar para tareas específicas.

**🤖 PROMPT en Modo Agent:**

```
Crea el archivo .github/agents/frontend-ins.md con un agente básico para desarrollo frontend:

# Agente: Frontend INS (@frontend-ins)

## Rol
Eres un experto en desarrollo frontend para el Grupo INS (Instituto Nacional de Seguros de Costa Rica).

## Idioma
- Todo el código, comentarios y textos de interfaz deben estar en **español**
- Usar terminología oficial de seguros (Póliza, Cobertura, Asegurado, Reclamo, Prima, etc.)

## Tecnologías
- Blazor WebAssembly (.NET 8)
- CSS3 con variables personalizadas (custom properties)
- HTML5 semántico

## Accesibilidad (WCAG AA)
- Contraste mínimo 4.5:1 para texto
- Todos los elementos interactivos accesibles por teclado
- Atributos ARIA donde corresponda

## Responsive Design
- Enfoque Mobile First
- Breakpoints: Móvil (< 576px), Tablet (576px - 992px), Desktop (> 992px)

## Reglas Importantes
1. SIEMPRE incluir estados de carga (spinners, skeletons)
2. SIEMPRE manejar errores con mensajes amigables en español
3. NUNCA usar inglés en textos visibles para el usuario
4. SIEMPRE documentar componentes con comentarios en español
```

---

### Paso 3.2: Analizar el sitio del INS con screenshot 📸 *(Opcional)*

> **💡 DEMOSTRACIÓN:** Copilot puede analizar imágenes para extraer información de diseño como colores, tipografía y estilos.
>
> **📝 NOTA:** Los pasos 3.2 y 3.3 son opcionales pero recomendados. Si los omites, el agente usará colores institucionales genéricos definidos en el paso 3.1.

**📍 Instrucciones:**
1. Abre el sitio oficial del Grupo INS: https://www.grupoins.com/
2. Toma un screenshot de la página principal (usa `Win+Shift+S` en Windows o `Cmd+Shift+4` en Mac)
3. Guarda la imagen o tenla en el portapapeles

**🤖 PROMPT en Modo Agent (adjunta el screenshot):**

```
Analiza este screenshot del sitio oficial del Grupo INS y extrae la siguiente información de diseño:

1. **Paleta de colores**: Identifica los colores principales usados en:
   - Header/navegación
   - Botones y llamadas a la acción
   - Fondos y textos
   - Acentos y elementos secundarios
   Proporciona los códigos hexadecimales exactos o aproximados

2. **Tipografía**: 
   - Fuentes utilizadas (o similares si no son identificables)
   - Jerarquía de tamaños (h1, h2, h3, texto base)

3. **Componentes UI identificados**:
   - Estilo de header y navegación
   - Estilo de tarjetas/cards
   - Estilo de botones
   - Estilo de footer

4. **Espaciado y layout**:
   - Márgenes y paddings aproximados
   - Estructura de grid

Genera esta información en formato que pueda agregar al agente frontend-ins.md
```

---

### Paso 3.3: Actualizar el agente con estilos del INS 🎨 *(Opcional)*

> **💡 NOTA:** Ahora actualizamos el agente básico con la información extraída del screenshot. (Requiere haber completado el paso 3.2)

**🤖 PROMPT en Modo Agent:**

```
Actualiza el archivo #file:.github/agents/frontend-ins.md agregando la información de diseño extraída del screenshot.

Agrega las siguientes secciones después de "Responsive Design":

## Paleta de Colores Institucional INS
(Incluye los colores identificados con sus códigos hex y uso recomendado)

## Tipografía
(Incluye las fuentes y escala de tamaños)

## Componentes Estándar
Describe el estilo visual para:
- Header Institucional
- Footer Institucional  
- Tarjetas (Cards)
- Botones
- Tablas

## Estructura de Archivos
Organiza los componentes Blazor así:
/Components
  /Layout
  /Paginas
  /Compartidos
/wwwroot
  /css
  /img
```

**✅ Resultado:** El agente ahora tiene toda la información de diseño institucional del INS extraída directamente del sitio oficial.

---

### Paso 3.4: Crear proyecto Blazor

**🤖 PROMPT en Modo Agent:**

```
Crea un proyecto Blazor WebAssembly llamado INS.SegurosVehiculos.Web con .NET 8 en la carpeta src y agrégalo a la solución INS.SegurosVehiculos.sln
```

**📝 Alternativa manual:**

```powershell
cd src
dotnet new blazorwasm -n INS.SegurosVehiculos.Web -f net8.0
dotnet sln add INS.SegurosVehiculos.Web
```

**✅ Verificar:** El proyecto aparece en la solución (`dotnet sln list`)

---

### Paso 3.5: Usar el Agente @frontend-ins 🎨

> **💡 IMPORTANTE:** A partir de ahora, usa el agente especializado escribiendo `@frontend-ins` al inicio de cada prompt relacionado con frontend.

**🤖 PROMPT con Agente:**

```
@frontend-ins Crea el archivo de estilos principal para el proyecto web.

Necesito un archivo CSS que:
- Defina variables con la paleta de colores institucional
- Incluya un reset CSS básico
- Configure la tipografía base importando las fuentes necesarias
- Tenga clases reutilizables para los componentes principales: botones, tarjetas, encabezado, navegación, pie de página y tablas
- Incluya clases utilitarias para layout y espaciado
- Agregue animaciones sutiles para transiciones y estados de carga

Usa los estilos definidos en el agente frontend-ins.md
```

---

### Paso 3.6: Crear Layout Principal

**🤖 PROMPT con Agente:**

```
@frontend-ins Crea el layout principal de la aplicación Blazor.

Quiero un diseño que replique la estructura del sitio oficial del INS con:

- Un encabezado institucional con el logo, título del sistema y navegación principal
- Una barra secundaria con breadcrumbs para mostrar la ubicación actual
- Un área de contenido principal centrada y con buen espaciado
- Un pie de página institucional con logo, enlaces legales, contacto y copyright

El layout debe ser completamente responsive y usar los estilos definidos en el tema CSS
```

---

### Paso 3.7: Crear Componentes Reutilizables

**🤖 PROMPT con Agente:**

```
@frontend-ins Crea componentes Blazor reutilizables para el sistema de seguros de vehículos.

Necesito los siguientes componentes:

1. **Tarjeta de Póliza**: Un componente que muestre la información de una póliza de seguro en formato card, incluyendo número de póliza, tipo de seguro, vehículo asegurado, fechas de vigencia, un badge de estado con colores según el estado, y un botón de acción que cambie según si la póliza está activa o vencida

2. **Widget de Estadística**: Un componente para mostrar métricas destacadas con un número grande, título descriptivo e ícono. Ideal para dashboards

3. **Indicador de Carga**: Un componente simple con spinner y mensaje personalizable para mostrar estados de carga

Todos los componentes deben:
- Recibir parámetros apropiados
- Usar los estilos del tema INS
- Ser responsive
- Tener documentación básica
```

---

### Paso 3.8: Crear Página Principal

**🤖 PROMPT con Agente:**

```
@frontend-ins Crea la página de inicio del Sistema de Seguros de Vehículos.

La página debe incluir:

1. Una sección hero llamativa con título, subtítulo motivacional sobre la importancia de asegurar tu vehículo, y un botón para registrar un nuevo seguro

2. Una sección de estadísticas destacadas usando los widgets, mostrando métricas como pólizas activas, vehículos asegurados, provincias cubiertas y reclamos procesados (usa datos de ejemplo por ahora)

3. Una sección que muestre las pólizas destacadas usando el componente de tarjeta, con datos de ejemplo hardcodeados

4. Una sección informativa explicando los beneficios de los diferentes tipos de seguros de vehículos

5. Un call-to-action final para contacto

La página debe ser la ruta principal ("/") y ser completamente responsive
```

---

### Paso 3.9: Crear Servicio HTTP

**🤖 PROMPT con Agente:**

```
@frontend-ins Crea un servicio para consumir la API REST de seguros de vehículos.

El servicio debe:

1. Definir los modelos/DTOs necesarios para representar pólizas, vehículos, respuestas paginadas y filtros de búsqueda

2. Crear una interface con métodos para:
   - Obtener lista de pólizas con filtros y paginación
   - Obtener una póliza por su identificador
   - Obtener pólizas destacadas para la página principal

3. Implementar el servicio usando HttpClient con:
   - Manejo de errores apropiado
   - Serialización JSON
   - URL base configurable

Por ahora, implementa con datos de ejemplo hardcodeados (mock) para poder probar sin la API. Incluye comentarios indicando dónde conectar con la API real
```

---

### Paso 3.10: Crear Página de Listado de Pólizas

**🤖 PROMPT con Agente:**

```
@frontend-ins Crea una página completa para listar y buscar pólizas de seguro.

La página necesita:

1. Un encabezado con título, subtítulo y contador de resultados encontrados

2. Una barra de filtros con:
   - Dropdown para filtrar por tipo de seguro
   - Dropdown para filtrar por estado de la póliza
   - Campo de búsqueda por texto (número de póliza, placa)
   - Botones para buscar y limpiar filtros

3. Un grid responsive de tarjetas de póliza usando el componente creado anteriormente

4. Manejo de diferentes estados de la página:
   - Estado de carga con el indicador
   - Estado vacío cuando no hay resultados
   - Estado de error con opción de reintentar

5. Paginación para navegar entre páginas de resultados

La página debe consumir el servicio de pólizas e inyectarlo apropiadamente
```

---

### Paso 3.11: Configurar Program.cs del Frontend

**🤖 PROMPT con Agente:**

```
@frontend-ins Configura el Program.cs del proyecto web para:

1. Registrar el HttpClient con la URL base de la API:
   - Usa https://localhost:5001 para desarrollo (mismo puerto configurado en la API)

2. Registrar el servicio de pólizas en el contenedor de inyección de dependencias

3. Cualquier otra configuración necesaria para que la aplicación funcione correctamente
```

---

### Paso 3.12: Actualizar referencias de estilos

**🤖 PROMPT con Agente:**

```
@frontend-ins Actualiza src/INS.SegurosVehiculos.Web/wwwroot/index.html para:

1. Agregar referencia al archivo tema-ins.css
2. Agregar Google Fonts (Montserrat y Open Sans)
3. Agregar meta tags apropiados en español
4. Título: "Sistema de Seguros de Vehículos - Grupo INS"

Mantén la estructura existente de Blazor
```

---

### Paso 3.13: Ejecutar el Frontend

**🤖 PROMPT en Modo Agent:**

```
Ejecuta ambos proyectos:
1. Primero inicia INS.SegurosVehiculos.API en una terminal
2. Luego inicia INS.SegurosVehiculos.Web en otra terminal
```

**📝 Alternativa manual:**

```powershell
# Terminal 1: Ejecutar API
cd src/INS.SegurosVehiculos.API
dotnet run

# Terminal 2: Ejecutar Frontend
cd src/INS.SegurosVehiculos.Web
dotnet run
```

Abre el navegador en la URL indicada (generalmente `https://localhost:5002` o similar).

**✅ Verificar antes de continuar:**
- [ ] El frontend carga sin errores en el navegador
- [ ] Los estilos INS se aplican correctamente
- [ ] La página de inicio muestra las secciones diseñadas

---

### 🛠️ Troubleshooting Lab 3

| Problema | Solución |
|----------|----------|
| El agente @frontend-ins no responde | Recarga VS Code después de crear el archivo del agente |
| CORS error al conectar con API | Verifica que la API tenga CORS habilitado para localhost |
| Estilos no se aplican | Revisa que `index.html` referencie el archivo CSS correcto |
| Componentes no se renderizan | Verifica los `@using` en `_Imports.razor` |
| HttpClient error | Confirma que la URL base coincida con el puerto de la API |

---

## 🔬 LABORATORIO 4: Pruebas y Documentación (20 min)

> **⚠️ PRERREQUISITO:** Este laboratorio requiere haber completado el **Laboratorio 2**. Necesitas:
> - El proyecto `INS.SegurosVehiculos.API` con las entidades y endpoints creados
> - El proyecto `INS.SegurosVehiculos.Pruebas` en la solución

### Objetivos
- ✅ Generar pruebas unitarias automáticamente
- ✅ Usar el comando /tests
- ✅ Generar documentación XML
- ✅ Crear README profesional

---

### Paso 4.1: Generar pruebas unitarias con /tests

> **💡 COMANDO ESPECIAL:** El comando `/tests` genera automáticamente pruebas unitarias para el código seleccionado.

**📍 Cómo usar /tests:**
1. Abre el archivo `src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/Poliza.cs`
2. Selecciona toda la clase (Ctrl+A en el archivo)
3. Abre Copilot Chat y escribe el prompt

**🤖 PROMPT:**

```
/tests Genera pruebas unitarias completas para esta entidad usando xUnit y FluentAssertions.

Quiero pruebas que cubran:

1. La creación de la entidad con datos válidos e inválidos (número de póliza vacío, nulo, fechas inconsistentes, montos negativos)

2. Los valores por defecto de las propiedades al crear una nueva instancia

3. Los métodos de comportamiento de la entidad (cambios de estado, validaciones de negocio)

Requisitos generales:
- Patrón Arrange-Act-Assert con comentarios en español
- Nombres de métodos descriptivos que indiquen qué se prueba y qué se espera
- Usar Theory con InlineData cuando haya múltiples casos similares
```

---

### Paso 4.2: Instalar paquetes de pruebas

**🤖 PROMPT en Modo Agent:**

```
Instala los paquetes de pruebas en INS.SegurosVehiculos.Pruebas:
- FluentAssertions
- Moq
- Microsoft.AspNetCore.Mvc.Testing (para pruebas de integración)
```

**📝 Alternativa manual:**

```powershell
cd src/INS.SegurosVehiculos.Pruebas
dotnet add package FluentAssertions
dotnet add package Moq
dotnet add package Microsoft.AspNetCore.Mvc.Testing
```

---

### Paso 4.3: Generar pruebas de integración

**🤖 PROMPT en Modo Agent:**

```
@workspace Crea pruebas de integración para los endpoints de pólizas.

Necesito pruebas que verifiquen el comportamiento completo de la API:

1. Pruebas para cada operación CRUD (obtener todos, obtener por id, crear, actualizar, eliminar)

2. Pruebas de casos de error (recurso no encontrado, datos inválidos)

3. Verificación de códigos de estado HTTP correctos para cada escenario

Configuración necesaria:
- Usar WebApplicationFactory para crear un servidor de pruebas en memoria
- Base de datos en memoria aislada para cada prueba
- Helpers para simplificar la creación de requests
```

---

### Paso 4.4: Generar documentación XML con /doc

> **💡 COMANDO ESPECIAL:** El comando `/doc` genera documentación XML automáticamente.

**📍 Cómo usar /doc:**
1. Abre `src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/PolizaEndpoints.cs`
2. Selecciona toda la clase
3. Usa el comando /doc

**🤖 PROMPT:**

```
/doc Genera documentación XML completa en español para estos endpoints.

Para la clase y cada método público incluye:
- Descripción clara de qué hace
- Documentación de todos los parámetros
- Descripción del valor de retorno
- Códigos de respuesta HTTP posibles con su significado

La documentación debe ser profesional, concisa y útil para que se muestre correctamente en Swagger/OpenAPI
```

---

### Paso 4.5: Habilitar documentación XML en el proyecto

**🤖 PROMPT en Modo Agent:**

```
@workspace Configura el proyecto API para que genere documentación XML automáticamente y que Swagger la muestre en la interfaz.

Necesito que:
- El proyecto genere el archivo XML de documentación al compilar
- Swagger lea y muestre los comentarios de documentación en la UI
- Se manejen apropiadamente las advertencias de documentación faltante
```

---

### Paso 4.6: Ejecutar pruebas

**🤖 PROMPT en Modo Agent:**

```
Ejecuta todas las pruebas del proyecto INS.SegurosVehiculos.Pruebas y muéstrame los resultados
```

**📝 Alternativa manual:**

```powershell
cd src/INS.SegurosVehiculos.Pruebas
dotnet test --verbosity normal
```

**✅ Verificar antes de continuar:**
- [ ] Todas las pruebas pasan (verde)
- [ ] Swagger muestra la documentación XML
- [ ] Los comentarios aparecen en cada endpoint

---

### 🛠️ Troubleshooting Lab 4

| Problema | Solución |
|----------|----------|
| FluentAssertions no encontrado | Ejecuta `dotnet restore` en el proyecto de pruebas |
| WebApplicationFactory falla | Asegúrate de tener el paquete `Microsoft.AspNetCore.Mvc.Testing` |
| Pruebas fallan por datos | Cada prueba debe usar su propia instancia de BD en memoria |
| Documentación XML no aparece | Verifica `GenerateDocumentationFile` en el .csproj |
| Warnings CS1591 | Agrega `<NoWarn>CS1591</NoWarn>` al .csproj si deseas suprimirlos |

---

## 🔬 LABORATORIO 5: Características Avanzadas (15 min)

> **⚠️ PRERREQUISITO:** Este laboratorio requiere haber completado los **Laboratorios 2 y 3**. Necesitas:
> - La estructura completa del proyecto API
> - El archivo `.github/copilot-instructions.md` configurado
> - Familiaridad con los modos de Copilot (Ask, Agent, Plan)

### Objetivos
- ✅ Traducir código legacy a C# moderno
- ✅ Integrar bibliotecas de terceros
- ✅ Crear agente de revisión de código

---

### Paso 5.1: Traducción de código legacy

> **💡 ESCENARIO:** Tienes código PHP antiguo de un sitio web del INS que muestra un contador de visitas. Necesitas migrarlo a C# moderno con Minimal API.

**📝 Primero crea la carpeta y el archivo de ejemplo:**

```powershell
mkdir legacy
```

**Luego crea el archivo:** `legacy/contador_visitas.php`

```php
<?php
// Código PHP legacy de ejemplo - Sitio web anterior del INS
// Contador de visitas de la página web

$archivo_contador = "contador.txt";

// Lee el número actual de visitas
function obtenerVisitas() {
    global $archivo_contador;
    if (file_exists($archivo_contador)) {
        $visitas = file_get_contents($archivo_contador);
        return intval($visitas);
    }
    return 0;
}

// Incrementa el contador y lo guarda
// NOTA: Este código tiene problemas de concurrencia (race condition)
function registrarVisita() {
    global $archivo_contador;
    $visitas = obtenerVisitas();
    $visitas++;
    file_put_contents($archivo_contador, $visitas);
    return $visitas;
}

// Obtiene visitas por página específica
// NOTA: Este código tiene vulnerabilidad de Path Traversal
function obtenerVisitasPorPagina($pagina) {
    $archivo = "contadores/" . $pagina . ".txt";
    if (file_exists($archivo)) {
        return intval(file_get_contents($archivo));
    }
    return 0;
}

// Registra visita para una página específica
// NOTA: Sin validación de entrada - vulnerable a inyección
function registrarVisitaPagina($pagina) {
    $archivo = "contadores/" . $pagina . ".txt";
    $visitas = obtenerVisitasPorPagina($pagina);
    $visitas++;
    file_put_contents($archivo, $visitas);
    return $visitas;
}

// Página principal
$total_visitas = registrarVisita();
$pagina_actual = isset($_GET['pagina']) ? $_GET['pagina'] : 'inicio';
$visitas_pagina = registrarVisitaPagina($pagina_actual);
?>

<html>
<head><title>INS - Contador de Visitas</title></head>
<body>
    <h1>Grupo INS</h1>
    <p>Total de visitas al sitio: <?php echo $total_visitas; ?></p>
    <p>Visitas a esta página (<?php echo $pagina_actual; ?>): <?php echo $visitas_pagina; ?></p>
    <p>Fecha: <?php echo date("d/m/Y H:i:s"); ?></p>
</body>
</html>
```

**🤖 PROMPT para traducir:**

```
Traduce este código PHP legacy a C# moderno con Minimal API siguiendo los estándares del proyecto INS:

Requisitos de la traducción:

1. **Arquitectura**: Crear endpoints Minimal API
   - Crear VisitaEndpoints.cs en Funcionalidades/Visitas/
   - Crear entidad Visita.cs con: Id, Pagina, FechaVisita, DireccionIp

2. **Modernización**:
   - Reemplazar archivos .txt por Entity Framework Core InMemory
   - Convertir a async/await
   - Usar DbContext en lugar de file_get_contents/file_put_contents

3. **Seguridad** (CRÍTICO):
   - Corregir la vulnerabilidad de Path Traversal en obtenerVisitasPorPagina
   - Validar el parámetro "pagina" (solo alfanuméricos y guiones)
   - Sanitizar todas las entradas del usuario

4. **Endpoints**:
   - POST /api/v1/visitas/registrar?pagina=inicio (registra visita)
   - GET /api/v1/visitas/total (total de visitas del sitio)
   - GET /api/v1/visitas/{pagina} (visitas por página)
   - GET /api/v1/visitas/resumen (resumen con visitas por página)

5. **Mejoras**:
   - Resolver el problema de concurrencia (race condition)
   - Agregar nullable reference types
   - Agregar CancellationToken a métodos async

6. **Documentación**:
   - XML comments en español

Crea los archivos en src/INS.SegurosVehiculos.API/Funcionalidades/Visitas/
```

---

### Paso 5.2: Integrar biblioteca externa

**🤖 PROMPT en Modo Plan:**

```
@workspace Quiero agregar funcionalidad para exportar reportes de pólizas a Excel.

Implementa lo siguiente:

1. **Paquete NuGet**: Agregar ClosedXML al proyecto API

2. **Servicio de Exportación**: 
   Crear ExportacionServicio.cs en src/INS.SegurosVehiculos.API/Funcionalidades/Exportacion/
   
   - Método: Task<byte[]> ExportarPolizaAExcelAsync(Guid polizaId)
   - Generar Excel con una hoja "Pólizas" con encabezados y datos
   - Formato básico: encabezados en azul (#003B71) con texto blanco

3. **Endpoint Minimal API**:
   GET /api/v1/polizas/{id}/exportar
   - Retorna archivo Excel para descarga

Muéstrame el plan primero
```

---

### Paso 5.3: Crear agente de revisión de código

**🤖 PROMPT en Modo Agent:**

```
Crea .github/agents/revisor-codigo.md con un agente especializado en revisión de código:

# Agente: Revisor de Código INS (@revisor-codigo)

## Rol
Eres un revisor de código senior especializado en .NET y los estándares de desarrollo del Grupo INS. Tu trabajo es revisar código y proporcionar retroalimentación constructiva.

## Idioma
Toda la retroalimentación debe estar en **español**.

## Checklist de Revisión

### Estándares del Proyecto
- [ ] Código en español (variables, métodos, comentarios)
- [ ] Estructura de carpetas por funcionalidad respetada
- [ ] Minimal API implementado correctamente
- [ ] Nombres siguen convenciones (PascalCase público, _camelCase privado)

### Calidad de Código
- [ ] Async/await usado correctamente
- [ ] Nullable reference types manejados
- [ ] No hay código duplicado
- [ ] Métodos con responsabilidad única
- [ ] Complejidad ciclomática aceptable

### Seguridad
- [ ] Sin datos sensibles en logs
- [ ] Validación de entradas presente
- [ ] Sin SQL Injection posible
- [ ] Sin secretos hardcodeados

### Rendimiento
- [ ] Consultas optimizadas (no N+1)
- [ ] Uso apropiado de AsNoTracking
- [ ] Paginación implementada en listas

### Documentación
- [ ] XML comments en APIs públicas
- [ ] Comentarios útiles (no obvios)

### Pruebas
- [ ] Cobertura de casos principales
- [ ] Nombres descriptivos
- [ ] Arrange-Act-Assert

## Formato de Respuesta

Al revisar código, responde con este formato:

---

## 📋 Revisión de Código: [Nombre del archivo]

### ✅ Aspectos Positivos
- Punto positivo 1
- Punto positivo 2

### ⚠️ Sugerencias de Mejora (Opcionales)
| Línea | Sugerencia | Razón |
|-------|------------|-------|
| 15 | Cambiar X por Y | Mejora legibilidad |

### ❌ Problemas a Corregir (Obligatorios)
| Línea | Problema | Solución |
|-------|----------|----------|
| 23 | SQL Injection | Usar parámetros |

### 📝 Código Sugerido

(código corregido aquí)

### 📊 Resumen
- Calidad general: ⭐⭐⭐⭐☆ (4/5)
- Seguridad: ✅ Aprobado / ⚠️ Revisar / ❌ Rechazado
- Listo para merge: Sí / No / Con cambios menores

---

## Severidad de Problemas

- 🔴 **Crítico**: Bloquea merge (seguridad, errores graves)
- 🟠 **Mayor**: Debe corregirse antes de merge
- 🟡 **Menor**: Sugerencia de mejora
- 🟢 **Info**: Comentario informativo
```

---

### Paso 5.4: Usar el agente revisor

**🤖 PROMPT con Agente:**

```
@revisor-codigo Revisa el archivo src/INS.SegurosVehiculos.API/Funcionalidades/Polizas/PolizaEndpoints.cs

Evalúa:
1. Cumplimiento de estándares del proyecto INS
2. Calidad y legibilidad del código
3. Posibles problemas de seguridad
4. Rendimiento de las consultas
5. Completitud de la documentación
6. Cobertura de casos de error

Proporciona retroalimentación detallada con sugerencias de mejora específicas.
```

**✅ Verificar al finalizar el workshop:**
- [ ] Código legacy traducido compila sin errores
- [ ] El endpoint de exportación genera archivo Excel válido
- [ ] El agente @revisor-codigo proporciona feedback útil

---

### 🛠️ Troubleshooting Lab 5

| Problema | Solución |
|----------|----------|
| ClosedXML no instala | Verifica conexión a internet y ejecuta `dotnet restore` |
| Error al generar Excel | Asegúrate de que el servicio esté registrado en DI |
| Agente @revisor-codigo no funciona | Verifica la ruta `.github/agents/revisor-codigo.md` |
| Traducción de PHP incompleta | Proporciona más contexto en el prompt sobre los estándares |

---

## 📖 Referencia Rápida

### Comandos de Copilot Chat

| Comando | Descripción | Ejemplo |
|---------|-------------|---------|
| `@workspace` | Contexto del proyecto completo | `@workspace ¿cómo se implementan los repos?` |
| `/tests` | Generar pruebas unitarias | Selecciona código → `/tests` |
| `/doc` | Generar documentación XML | Selecciona clase → `/doc` |
| `/fix` | Proponer corrección de errores | Selecciona error → `/fix` |
| `/explain` | Explicar código seleccionado | Selecciona código → `/explain` |
| `/new` | Crear nuevo archivo | `/new crear servicio de exportación` |
| `@frontend-ins` | Agente de frontend | `@frontend-ins crea componente` |
| `@revisor-codigo` | Agente de revisión | `@revisor-codigo revisa este archivo` |

### Atajos de Teclado

| Atajo | Acción |
|-------|--------|
| `Ctrl+I` | Abrir Copilot inline en el editor |
| `Ctrl+Shift+I` | Abrir panel de Copilot Chat |
| `Tab` | Aceptar sugerencia de Copilot |
| `Esc` | Rechazar sugerencia |
| `Alt+]` | Ver siguiente sugerencia |
| `Alt+[` | Ver sugerencia anterior |
| `Ctrl+Enter` | Abrir Copilot Completions Panel |

### Modos de Copilot

| Modo | Cuándo Usar |
|------|-------------|
| **Ask** 💬 | Explorar, entender, planificar (no modifica archivos) |
| **Agent** 🤖 | Implementar, crear archivos, hacer cambios |
| **Plan** 📋 | Tareas complejas multi-archivo (con aprobación) |

---

## ✅ Checklist Final del Workshop

Al terminar el workshop, deberías tener:

### Documentación
- [ ] `docs/especificaciones/especificacion-sistema.md`
- [ ] `docs/especificaciones/modelo-dominio.md`
- [ ] `docs/especificaciones/contratos-api.md`

### Backend (API)
- [ ] Solución .NET con Minimal API
- [ ] `Funcionalidades/Polizas/` completo (entidad, DTOs, endpoints)
- [ ] `Funcionalidades/Vehiculos/` implementado
- [ ] `Datos/SegurosDbContext.cs` configurado
- [ ] Swagger funcionando en `/swagger`

### Frontend
- [ ] Proyecto Blazor WebAssembly
- [ ] Archivo CSS con estilos institucionales INS
- [ ] `Components/Layout/MainLayout.razor`
- [ ] `Components/Pages/Inicio.razor`
- [ ] `Components/Pages/Polizas.razor`
- [ ] Componentes compartidos (TarjetaPoliza, etc.)

### Pruebas
- [ ] Pruebas unitarias para entidad Poliza
- [ ] Pruebas de integración para endpoints de Pólizas

### Configuración de Copilot
- [ ] `.github/copilot-instructions.md`
- [ ] `.github/agents/frontend-ins.md`
- [ ] `.github/agents/revisor-codigo.md`

### Extras
- [ ] Código legacy traducido a C# moderno
- [ ] Servicio de exportación a Excel

---

## 📚 Recursos Adicionales

### Documentación Oficial
- [GitHub Copilot Docs](https://docs.github.com/en/copilot)
- [VS Code + Copilot](https://code.visualstudio.com/docs/copilot/overview)
- [.NET 8 Documentation](https://learn.microsoft.com/en-us/dotnet/core/whats-new/dotnet-8)
- [Blazor Documentation](https://learn.microsoft.com/en-us/aspnet/core/blazor/)

### Patrones y Arquitectura
- [Minimal API (.NET 8)](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis)
- [EF Core InMemory](https://learn.microsoft.com/en-us/ef/core/providers/in-memory/)

### Grupo INS
- [Portal Grupo INS](https://www.grupoins.com/)
- [Seguros de Vehículos INS](https://www.grupoins.com/seguros/)

---

## 🙋 Preguntas Frecuentes

### ¿Por qué Copilot no sigue mis instrucciones del archivo copilot-instructions.md?
Asegúrate de que:
1. El archivo esté en `.github/copilot-instructions.md`
2. Hayas recargado VS Code después de crearlo
3. Estés usando `@workspace` para que tome contexto

### ¿Cómo hago que Copilot genere código en español?
1. Configúralo en `.github/copilot-instructions.md` (Lab 2.1) — esto aplica para todo el proyecto
2. Proporciona ejemplos en español en tu código existente
3. Si aún no tienes `copilot-instructions.md`, agrega "Responde en español" al final del prompt como medida temporal

### ¿El Modo Plan no me muestra el plan, ¿qué hago?
- Verifica que tengas la última versión de la extensión
- Intenta con tareas más complejas (el plan es más útil para múltiples archivos)
- Usa Modo Agent si solo necesitas crear un archivo

### ¿Los agentes personalizados no funcionan?
- Verifica la ruta: `.github/agents/nombre-agente.md`
- El nombre del archivo (sin .md) es el nombre del agente
- Recarga VS Code después de crear el archivo

### ¿Por qué usamos base de datos en memoria?

Este taller usa `Microsoft.EntityFrameworkCore.InMemory` por las siguientes razones:

| Ventaja | Descripción |
|---------|-------------|
| **Sin instalación** | No requiere SQL Server, SQLite ni ningún motor de BD |
| **Rápido** | Operaciones instantáneas, ideal para desarrollo |
| **Portable** | Funciona igual en cualquier máquina |
| **Aislado** | Cada ejecución inicia limpia con datos semilla |

**Limitaciones a considerar:**
- Los datos se pierden al detener la aplicación
- No soporta algunas características avanzadas de SQL
- Para producción, cambiar a SQL Server o PostgreSQL

**¿Cómo cambiar a SQL Server en producción?**
1. Cambiar paquete: `Microsoft.EntityFrameworkCore.SqlServer`
2. Actualizar Program.cs: `UseInMemoryDatabase` → `UseSqlServer(connectionString)`
3. Agregar connection string en appsettings.json

---

## 👥 Créditos

**Workshop desarrollado para:** Grupo INS (Instituto Nacional de Seguros de Costa Rica)

**Tecnologías:** GitHub Copilot, .NET 8, Blazor WebAssembly, C#

**Duración:** 3 horas

---

*¿Preguntas o comentarios? Contacta al equipo de capacitación.*
