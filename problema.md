# 🏢 Caso de Estudio: Red Corporativa "TechCorp"

[🏠 Inicio](README.md) | [📋 Instrucciones Generales](instrucciones.md) | [🏢 Problema: "TechCorp"](problema.md) | [✨ Ejemplo de Entrega](ejemplo-entrega.md) | [📊 Criterios de Evaluación](criterios-evaluacion.md) | [✅ Lista de Cotejo](lista-cotejo.md)

---

## Escenario
La empresa *TechCorp* requiere interconectar las oficinas de su nuevo edificio .

### Requerimientos de VLANs (Etapa 1)
- **VLAN 10 (Administración):** `192.168.10.0/24` — Piso 1
- **VLAN 20 (Ventas):** `192.168.20.0/24` — Piso 2
- **VLAN 30 (TI):** `192.168.30.0/24` — Piso 3
- **VLAN 99 (Gestión):** `192.168.99.0/24` — SVI de Switches
- **VLAN 999 (Blackhole):** Puertos inactivos


🏢 Caso de Estudio: Modernización e Interconexión de la Red LAN Corporativa
Contexto del Problema
La empresa TechCorp ha iniciado un proceso de reestructuración en su infraestructura de red local para responder al crecimiento de sus operaciones internas y mejorar la seguridad de la información. Actualmente, la organización requiere un esquema de red segmentado lógicamente para separar el tráfico entre sus distintas áreas operativas: Administración (VLAN 10), Laboratorios de Capacitación (VLAN 20), Dirección General (VLAN 30) y una red exclusiva para la Gestión e Infraestructura (VLAN 99).

Para cumplir con este objetivo, el departamento de TI ha diseñado una topología física en estrella extendida. El núcleo de la red estará centralizado en un switch distribuido (SW-Core), el cual se conecta directamente con un router principal (R1-Core) a través de la interfaz física GigabitEthernet 0/0/0 para llevar a cabo el enrutamiento inter-VLAN mediante subinterfaces (esquema Router-on-a-Stick).

A su vez, el SW-Core dará acceso directo a los equipos locales del edificio administrativo y distribuirá la conectividad hacia dos switches secundarios (SW-Lab1 y SW-Lab2), encargados de conectar los equipos de los laboratorios de cómputo.

Descripción del Escenario Topológico
Enrutamiento Central (R1-Core): Recibe la interfaz troncal proveniente del SW-Core y aloja las subinterfaces asociadas a cada VLAN (.10, .20, .30 y .99), actuando como la puerta de enlace predeterminada (Default Gateway) para toda la infraestructura.

Distribución Principal (SW-Core): Conecta directamente con el router central y atiende a los hosts locales de las oficinas principales:

1 PC de Gestión asignada a la VLAN 99 (Puerto Fa0/9).

6 PCs de Administración pertenecientes a la VLAN 10 (Puertos Fa0/1 al Fa0/6).

2 PCs de Dirección General integradas en la VLAN 30 (Puertos Fa0/7 y Fa0/8).

Acceso Remoto (SW-Lab1 y SW-Lab2): Interconectados mediante enlaces troncales hacia el SW-Core. Cada uno da servicio a 3 PCs de Alumnos pertenecientes a la VLAN 20 (Puertos Fa0/1 al Fa0/3 en ambos switches).

Desafío y Requerimientos de Configuración
Como especialista en redes, se te encomienda implementar, configurar y validar esta topología dentro del entorno de simulación Cisco Packet Tracer.

Tus tareas principales consisten en:

Cálculo de Direccionamiento IP: Aplicar los parámetros de direccionamiento IPv4 con máscara de subred /24 (255.255.255.0) según los segmentos asignados:

VLAN 10 (Administración): 192.168.10.0/24

VLAN 20 (Laboratorios): 192.168.20.0/24

VLAN 30 (Dirección): 192.168.30.0/24

VLAN 99 (Gestión): 192.168.99.0/24

Configuración de Interfaces e Interlocking:

Calcular y asignar la última dirección IP utilizable de cada segmento de red a la subinterfaz correspondiente en R1-Core (la cual servirá de Default Gateway para los hosts de esa VLAN).

Configurar las Interfaces Virtuales de Switch (SVI) en la VLAN 99 para la administración remota de cada switch, asignando secuencialmente la 1ª IP utilizable para SW-Core, la 2ª IP utilizable para SW-Lab1 y la 3ª IP utilizable para SW-Lab2.

Asignación de Hosts: Configurar las direcciones IP estáticas en formato CIDR en los dispositivos finales y establecer el enlace hacia su respectiva puerta de enlace.

Entregables del Proyecto
Plan de Direccionamiento: Completar la matriz de direccionamiento (Tabla A para infraestructura interlineal y Tabla B para hosts) resolviendo las direcciones faltantes y puertas de enlace correspondientes.

Archivo de Simulación (.pkt): Subir al repositorio del proyecto el archivo de Cisco Packet Tracer completamente interconectado, configurado y validado mediante pruebas de conectividad (ping inter-VLAN).
