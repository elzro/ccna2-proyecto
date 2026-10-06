# 🌐 Proyecto Integrador: Red Corporativa CCNA 2 (SRWE v7)

> **Materia:** Manejo de Tecnologias de conmutación y enrutamiento / CCNA 2 v7  
> **Nivel:** 5 Semestre Conalep 039  
> **Profesor:** elzro  

---

## 🏢 Caso de Estudio: Red Corporativa "TechCorp"

[🏠 Inicio](README.md) | [📋 Instrucciones Generales](instrucciones.md) | [🏢 Problema: "TechCorp"](problema.md) | [✨ Ejemplo de Entrega](ejemplo-entrega.md) | [📊 Criterios de Evaluación](criterios-evaluacion.md) | [✅ Lista de Cotejo](lista-cotejo.md)

---
# 📍 Etapa 1: Infraestructura Base y Segmentación (Módulos 1-4)
*Configuración inicial de seguridad, diseño de VLANs y Enrutamiento Inter-VLAN.*

#### 📚 Objetivos Didácticos

Al finalizar este ejercicio práctico, el estudiante será capaz de:

- **Diseñar e implementar** una topología LAN jerárquica en estrella extendida utilizando switches de capa de acceso y distribución interconectados con un router central.
    
- **Segmentar el tráfico de red** mediante la creación y asignación de VLANs (Administración, Laboratorios, Dirección y Gestión) para optimizar el dominio de difusión y la seguridad.
    
- **Configurar enrutamiento Inter-VLAN** bajo la técnica _Router-on-a-Stick_, implementando subinterfaces en una interfaz física con encapsulamiento IEEE 802.1Q.
    
- **Establecer la gestión de infraestructura** mediante la configuración de Interfaces Virtuales de Switch (SVI) en la VLAN de administración y la asignación de puertas de enlace predeterminadas (_Default Gateway_).
    
- **Calcular y documentar el direccionamiento IPv4**, identificando rangos utilizables, subredes `/24`, direcciones de subinterfaz y direccionamiento estático en hosts.
    

#### 🛠️ Competencias Profesionales y Técnicas (Saber Hacer)

- **Asociadas a la Certificación Cisco CCNA 2 (SRWE v7):**
    
    - **Módulo 3:** Demuestra dominio en la configuración de VLANs, puertos de acceso y puertos troncales (_Trunking_).
        
    - **Módulo 4:** Implementa exitosamente el enrutamiento Inter-VLAN mediante subinterfaces en routers Cisco IOS.
        
    - **Módulo 1:** Aplica configuraciones iniciales de seguridad y gestión en switches Catalyst (SVI, hostnames, contraseñas y puertas de enlace).
        
- **Competencias Transversales de Ingeniería y TI:**
    
    - **Pensamiento Crítico y Resolución de Problemas:** Diagnostica y resuelve fallos de conectividad entre diferentes subredes lógicas.
        
    - **Documentación Técnica de Ingeniería:** Elabora tablas de direccionamiento precisas y mantiene un portafolio digital estructurado con buenas prácticas de gestión de versiones en GitHub


## 🏢 Caso de Estudio: Modernización e Interconexión de la Red LAN Corporativa

### Contexto del Problema

La empresa **TechCorp** ha iniciado un proceso de reestructuración en su infraestructura de red local para responder al crecimiento de sus operaciones internas y mejorar la seguridad de la información. Actualmente, la organización requiere un esquema de red segmentado lógicamente para separar el tráfico entre sus distintas áreas operativas: **Administración (VLAN 10)**, **Laboratorios de Capacitación (VLAN 20)**, **Dirección General (VLAN 30)** y una red exclusiva para la **Gestión e Infraestructura (VLAN 99)**.

Para cumplir con este objetivo, el departamento de TI ha diseñado una topología física en **estrella extendida**. El núcleo de la red estará centralizado en un switch distribuido (`SW-Core`), el cual se conecta directamente con un router principal (`R1-Core`) a través de la interfaz física `GigabitEthernet 0/0/0` para llevar a cabo el enrutamiento inter-VLAN mediante subinterfaces (esquema _Router-on-a-Stick_).

A su vez, el `SW-Core` dará acceso directo a los equipos locales del edificio administrativo y distribuirá la conectividad hacia dos switches secundarios (`SW-Lab1` y `SW-Lab2`), encargados de conectar los equipos de los laboratorios de cómputo.

### Descripción del Escenario Topológico

```text
               [ R1-Core (Router) ]
                        |
                        | (Interfaz G0/0/0 - Trunk Vlan 111, Router-on-a-Stick)
                        |
                 [ SW-Core ] ------------- Local:
                  /       \                └── VLAN 99: 1 PC Gestión
                 / (Trunk) \ (Trunk) Vlan 111 nativa
                /           \
          [ SW-Lab1 ]    [ SW-Lab2 ]

      Dispositivos en SW-Lab1:       Dispositivos en SW-Lab2:
      ├── VLAN 10: 3 PCs Admin       ├── VLAN 10: 3 PCs Admin
      ├── VLAN 20: 3 PCs Alumnos     ├── VLAN 20: 3 PCs Alumnos
      └── VLAN 30: 1 PC Dirección    └── VLAN 30: 1 PC Dirección

```

1. **Enrutamiento Central (`R1-Core`):** Recibe la interfaz troncal proveniente del `SW-Core` y aloja las subinterfaces asociadas a cada VLAN (`.10`, `.20`, `.30`,`99` y `.111`), actuando como la puerta de enlace predeterminada (_Default Gateway_) para toda la infraestructura.
    
### Desglose Detallado por Switch y VLAN

1. **`R1-Core` (Router Central):**
    
    - **Interfaz G0/0/0:** Concentra las subinterfaces (`.10`, `.20`, `.30`, `.99`,`111`) y actúa como la puerta de enlace predeterminada para todas las subredes.
        
2. **`SW-Core` (Switch Núcleo):**
    
    - **VLAN 99 (Gestión):** **1 PC Gestión** (`Fa0/9`).
        
    - **Enlaces Troncales:** Puertos interconectados hacia `SW-Lab1` y `SW-Lab2` etiquetando las VLANs 10, 20, 30 y 99.
        
3. **`SW-Lab1` (Switch Acceso - Edificio A):**
    
    - **VLAN 10 (Administrativos):** **3 PCs** (`Fa0/1` al `Fa0/3`)
        
    - **VLAN 20 (Alumnos):** **3 PCs** (`Fa0/4` al `Fa0/6`)
        
    - **VLAN 30 (Dirección):** **1 PC** (`Fa0/7`)
        
4. **`SW-Lab2` (Switch Acceso - Edificio B):**
    
    - **VLAN 10 (Administrativos):** **3 PCs** (`Fa0/1` al `Fa0/3`)
        
    - **VLAN 20 (Alumnos):** **3 PCs** (`Fa0/4` al `Fa0/6`)
        
    - **VLAN 30 (Dirección):** **1 PC** (`Fa0/7`)

### Desafío y Requerimientos de Configuración

Como especialista en redes, se te encomienda implementar, configurar y validar esta topología dentro del entorno de simulación **Cisco Packet Tracer**.

Tus tareas principales consisten en:

1. **Cálculo de Direccionamiento IP:** Aplicar los parámetros de direccionamiento IPv4 con máscara de subred `/24` (`255.255.255.0`) según los segmentos asignados:
    
    - **VLAN 10 (Administración):** `192.168.10.0/24`       
    - **VLAN 20 (Laboratorios):** `192.168.20.0/24`
    - **VLAN 30 (Dirección):** `192.168.30.0/24`
    - **VLAN 99 (Gestión):** `192.168.99.0/24` — SVI de Switches
    - **VLAN 999 (Blackhole):** Puertos inactivos (apagados)
    - **VLAN 111 (Nativa):** vlan donde estan los enlaces troncales.
    - **Seguridad básica:** `enable secret`, cifrado de contraseñas de texto plano y mensaje de advertencia (`banner motd`).

        
2. **Configuración de Interfaces e Interlocking:**
    
    - Calcular y asignar la **última dirección IP utilizable** de cada segmento de red a la subinterfaz correspondiente en `R1-Core` (la cual servirá de _Default Gateway_ para los hosts de esa VLAN).
        
    - Configurar las **Interfaces Virtuales de Switch (SVI)** en la **VLAN 99** para la administración remota de cada switch, asignando secuencialmente la **1ª IP utilizable** para `SW-Core`, la **2ª IP utilizable** para `SW-Lab1` y la **3ª IP utilizable** para `SW-Lab2`.
        
3. **Asignación de Hosts:** Configurar las direcciones IP estáticas en formato CIDR en los dispositivos finales y establecer el enlace hacia su respectiva puerta de enlace.
    

# 📌 Entregables del Proyecto

- **📝 1. Plan de Direccionamiento:** Completar la matriz de direccionamiento (Tabla A para infraestructura interlineal y Tabla B para hosts) resolviendo las direcciones faltantes y puertas de enlace correspondientes.
    
- **📝 2. Archivo de Simulación (`.pkt`):** Subir al repositorio del proyecto el archivo de Cisco Packet Tracer completamente interconectado, configurado y validado mediante pruebas de conectividad (_ping_ inter-VLAN).

- **📝 3. Diario de Aprendizaje y Troubleshooting (Anti-IA)**

-**📝 4. Video explicativo de 3 min maximo sobre el funcionamiento y donde explicas la configuracion.

[](https://github.com/elzro/portafolio-alumno-prueba/blob/main/README.md#-4-diario-de-aprendizaje-y-troubleshooting-anti-ia)

- **¿Cuál fue el mayor reto técnico que enfrentaste en esta unidad?**  
    [Escribe aquí tu respuesta con tus propias palabras]
    
- **Bitácora de Errores (Documenta al menos 2 fallas que te ocurrieron y cómo las solucionaste):**
    
    1. _Error 1:_ [Ej: Olvidé poner el comando encapsulation dot1Q en la subinterfaz]  
        _Solución:_ [Ej: Entré a la subinterfaz, ejecuté encapsulation dot1q 10 y el tráfico comenzó a fluir]
    2. _Error 2:_ [Escribe aquí tu segundo error real]  
        _Solución:_ [Escribe cómo lo solucionaste]
