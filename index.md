# Pruebas Automatizadas 🤖

Guía rápida y sencilla de Ejecución de Pruebas de Chattigo 😉


1. [Ejecutar pruebas desde GitHub Actions](#id1)
2. [Ejecutar pruebas desde Discord](#id2)
3. [Ver reporte de pruebas](#id3)
4. [Ejecutar subsuite de pruebas (marcas)](#id4)


---


<div id='id1' />
## Ejecutar pruebas desde GitHub Actions 🚀

Dentro de cada Repositorio (agente, canales, etc.) ir a la sección **Actions** → **Workflows** → **Ejecutor de pruebas** → **Run Workflow**

Se nos desplegará un pequeño formulario con los siguientes campos:

- **Ambiente**: El ambiente dónde queremos correr las pruebas → _leones, tigres, panteras, lobos_. OBLIGATORIO❗
- **Marcas**: Las marcas que deseamos ejecutar. Si no se especifica ninguna se ejecutará el 100% de las pruebas de ese repositorio
- **Enviar ejecución a Jira?**: Si deseamos que se guarde la ejecución en JIRA Zephyr o no. → _true, false_

Hacer click en **run workflow** y LISTO!✅


---


<div id='id2' />
## Ejecutar pruebas desde Discord 👾

Abrir Discord → Ir al servidor de Automation → Ir al canal #general → Escribir el comando

### Comandos
```markdown
  Comando con parámetros mínimos y obligatorios
  /run --env="<ambiente>" --repo="<repositorio>" 

  Comando para ejecutar una subsuite de pruebas
  /run --env="<ambiente>" --repo="<repositorio>" -m="<marcas>"
  
  Comando para enviar la ejecución a Jira Zephyr
  /run --env="<ambiente>" --repo="<repositorio>" -jira

  Comando para pedir ayuda y ejemplos
  /help
```

### Ejemplos
```markdown

  Ejecutar todas las pruebas del agente en el ambiente de leones
  /run --env="leones" --repo="agente"
  
  Ejecutar únicamente las pruebas críticas del agente en el ambiente de tigres
  /run --env="tigres" --repo="agente" -m="critical"
  
  Dejar el ciclo de ejecución en Jira
  /run --env="panteras" --repo="supervisor" -jira
  
  Ejecutar un conjunto de marcas. Todas las pruebas de Messenger a nivel de Backend
  /run --env="leones" --repo="canales" -m="messenger and back"
  
 ```


---


<div id='id3' />
## Ver reporte de pruebas 📈
- **Opción 1**: Entrar a la ejecución del workflow → Ir al step llamado _Link Reporte_📌 → Click en el Link mostrado (estar conectado a la VPN)
- **Opción 2**: Entrar a Discord → Ir al canal llamado #automation_tests → Buscar la ejecución y hacer click en _acá_
- **Opción 3**: (Únicamente si dejamos la ejecución en JIRA) Ir a Zepyhr Scale → Ejecuciones → Pruebas Automatizadas → Funcionalidad → Ejecución (_fecha y hora_) → Ir a la descripción de la ejecución y obtener el Link.


---


<div id='id4' />
## Ejecutar subsuite de pruebas (marcas) 🔖

En ocasiones no queremos correr el 100% de las pruebas. Ya sea porque quiero correr solamente pruebas que afectan a una funcionalidad específica, porque quiero hacer un smoke test de la aplicación, ¿O por qué no? correr sólo las pruebas de backend.

### Marcas Generales 🔖

- **critical**: Pruebas críticas que NO pueden fallar en producción. 
- **smoke**: Pruebas básicas que deben funcionar si o sí para empezar a probar un determinado flujo.
- **back**: Pruebas a nivel de API y WebSockets, son las pruebas mas rápidas que se pueden ejecutar.
- **web**: Pruebas a nivel del Frontend de la Aplicación, son pruebas desde el punto de vista del usuario de la plataforma.

### Marcas para pruebas del Agente 🔖
[Repositorio](https://github.com/chattigodev/automation-agente)
- **login**: Pruebas relacionadas con el login en la plataforma.
- **states**: Pruebas relacionadas con los estados del agente (online, descanso, etc.)
- **chat**: Pruebas correpondientes a las funcionalidades que interactuan con un chat.

### Marcas para pruebas de los Canales 🔖
[Repositorio](https://github.com/chattigodev/automation-canales)
- **webchat**: Pruebas del webchat.
- **whatsapp**: Pruebas de WhatsApp.
- **messenger**: Pruebas de Messenger.
- **facebook**: Pruebas de Facebook Muro.

### Marcas para pruebas del Supervisor 🔖
[Repositorio](https://github.com/chattigodev/automation-supervisor)
- **login**: Pruebas relacionadas con el login en la plataforma.
- **kpi**: Pruebas del Dashboard de KPI's (Chats cerrados, chat activos por agente, etc.)
- **monitor**: Pruebas relacionadas al monitoreo del agente (chats asignados, etc.) 
