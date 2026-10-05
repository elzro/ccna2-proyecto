# 🌐 Proyecto Integrador: Red Corporativa CCNA 2 (SRWE v7)

> **Materia:** Manejo de Tecnologias de conmutación y enrutamiento / CCNA 2 v7  
> **Nivel:** 5 Semestre Conalep 039  
> **Profesor:** elzro  

---

# 📋 Instrucciones Generales del Proyecto

[🏠 Inicio](README.md) | [📋 Instrucciones Generales](instrucciones.md) | [🏢 Problema: "TechCorp"](problema.md) | [✨ Ejemplo de Entrega](ejemplo-entrega.md) | [📊 Criterios de Evaluación](criterios-evaluacion.md) | [✅ Lista de Cotejo](lista-cotejo.md)

---

## 1. Creación del Portafolio Personal
Cada estudiante creará un repositorio público en su cuenta de GitHub llamado `portfolio-ccna2` y activará **GitHub Pages**.

## 2. Entregables por Etapa
En cada etapa deberás incluir en tu repositorio:
1. Tu archivo de Cisco Packet Tracer (`.pkt`).
2. La documentación CLI e imágenes en tu `README.md`.
3. Las respuestas al diario de aprendizaje (metacognición).


# ccna2-proyecto-integrador
Instrucciones, requerimientos técnicos y política de evaluación para el Proyecto Integrador de la asignatura de Redes (CCNA 2 - SRWE v7).


# 🏢 Proyecto Integrador: Red Corporativa "TechCorp"
**Asignatura:** Conectividad de Redes (CCNA 2 - SRWE v7)  
**Profesor:** [ Tu Nombre Completo]  
**Institución:** [Nombre del Bachillerato]

Bienvenido al repositorio oficial del proyecto integrador. Este espacio contiene el escenario, los requerimientos técnicos y las reglas de evaluación obligatorias para construir la infraestructura de red de la empresa *TechCorp*.

---

## 🛑 Política Anti-IA y Sistema de Evaluación Cronológica (¡Importante!)
Para garantizar un aprendizaje real y profesional, **este proyecto no se califica únicamente por el resultado final, sino por la evidencia de tu proceso de construcción en el tiempo.**

1. **La Regla de los Commits:** Está estrictamente prohibido subir todo el proyecto terminado en un solo día o de último momento. Cada etapa requiere un **mínimo de 3 "commits" (guardados)** en días y horas diferentes dentro de tu historial de GitHub. 
2. **Penalización por "Entrega Mágica":** Si tu archivo `.pkt` funciona a la perfección pero tu historial de GitHub muestra un solo commit el último día, **perderás automáticamente el 30% de la calificación** de esa etapa.
3. **Firma de Identidad CLI:** Todos los switches y routers deben configurarse con un Hostname que incluya tus iniciales (ej. `S1-Lab1-JPA`). Las capturas de pantalla de la consola deben incluir obligatoriamente el comando `show version` para verificar el tiempo de encendido real del simulador.

---

## 📅 Cronograma del Proyecto (3 Etapas Calificables)

### 📍 Etapa 1: Infraestructura Base y Segmentación (Módulos 1-4)
*Configuración inicial de seguridad, diseño de VLANs y Enrutamiento Inter-VLAN.*

*   **Hito 1 (Obligatorio en GitHub):** Topología física armada en Packet Tracer, dispositivos nombrados con tus iniciales y contraseñas base configuradas.
*   **Hito 2 (Obligatorio en GitHub):** Creación de las VLANs de departamentos y asignación de puertos de acceso y troncales.
*   **Entrega Final Etapa 1:** Configuración de *Router-on-a-Stick*, pruebas de ping exitosas entre VLANs, llenado de la tabla de direccionamiento en tu `README.md` y bitácora de errores.

#### Requerimientos Técnicos (Etapa 1):
*   **VLAN 10 (Administración):** Red `192.168.10.0/24`
*   **VLAN 20 (Ventas):** Red `192.168.20.0/24`
*   **VLAN 30 (Invitados):** Red `192.168.30.0/24`
*   **VLAN 99 (Nativa y Administración):** Red `192.168.99.0/24`
*   Seguridad básica: `enable secret`, cifrado de contraseñas de texto plano y mensaje de advertencia (`banner motd`).

---
<!--
### 📍 Etapa 2: Redundancia y Servicios de Red (Módulos 5-9)
*Optimización de enlaces, prevención de bucles y automatización de direccionamiento.*

*   **Hito 1 (Obligatorio en GitHub):** Duplicación de enlaces físicos entre switches centrales y configuración de EtherChannel (LACP).
*   **Hito 2 (Obligatorio en GitHub):** Ajuste de prioridades en STP para asegurar qué switch es el Root Bridge principal y secundario.
*   **Entrega Final Etapa 2:** Configuración de servidores DHCPv4 y DHCPv6 en el Router core. Las PCs deben recibir IP de manera automática.

---

### 📍 Etapa 3: Red Inalámbrica, Seguridad y Conexión Externa (Módulos 10-16)
*Protección de puertos contra intrusos, despliegue de red Wi-Fi corporativa y salida a Internet.*

*   **Hito 1 (Obligatorio en GitHub):** Configuración de Port Security en switches de acceso (máximo 2 MACs por puerto y acción de violación *shutdown*).
*   **Hito 2 (Obligatorio en GitHub):** Configuración de un Access Point o WLC inalámbrico con seguridad WPA2 para los empleados de la empresa.
*   **Entrega Final Etapa 3:** Enrutamiento estático hacia un Router externo que simula "Internet" y pruebas de conectividad de extremo a extremo.

---
-->

## 📋 Criterios de Evaluación (Rúbrica General por Etapa)

*   **Funcionamiento Técnico (40%):** La topología en Packet Tracer opera correctamente, los comandos CLI son los adecuados y los pings/servicios son exitosos.
*   **Historial de Avance Cronológico - Anti-IA (30%):** Presencia de commits constantes en el historial de GitHub que demuestren que el proyecto se construyó paso a paso durante las semanas de clase.
*   **Documentación de Ingeniería (20%):** Tablas de direccionamiento completas, formato Markdown limpio y capturas de pantalla con la firma de identidad correspondiente.
*   **Bitácora de Troubleshooting (10%):** Documentación real y honesta de al menos dos errores encontrados durante las configuraciones y cómo se resolvieron.

---

## 🛠️ Instrucciones para que inicies tu Portafolio

1. Crea tu cuenta gratuita en [GitHub](https://github.com).
2. Crea un repositorio público llamado `portafolio-ccna2` e inicialízalo con un archivo `README.md`.
3. Ve a **Settings** -> **Pages**, selecciona la rama **`main`** y guarda para activar tu sitio web público.
4. Copia la estructura del portafolio que el profesor te proporcionará en clase, pégala en tu `README.md` y comienza a trabajar en tus commits técnicos desde la primera sesión práctica.
