# ✨ Ejemplo de Entrega (Modelo para el Alumno)

[🏠 Inicio](README.md) | [📋 Instrucciones Generales](instrucciones.md) | [🏢 Problema: "TechCorp"](problema.md) | [✨ Ejemplo de Entrega](ejemplo-entrega.md) | [📊 Criterios de Evaluación](criterios-evaluacion.md) | [✅ Lista de Cotejo](lista-cotejo.md)

---
### 📋 Sigue un plan de Configuración de Red en orden por ejemplo:
- [x] Configurar el nombre del Host (`R1-Core-ELO`)
- [ ] Configurar la subinterfaz `GigabitEthernet0/0/0.10`
- [ ] Asignar direccionamiento IP y encapsulamiento Dot1Q
- [x] Verificar conectividad con Ping

![ejemplo de entrega](./imgs/1-topologia.png)

*(Agrega las imagenes puedes guiarte con esta estructura para armar su README)*
**recomiendo crear una imagen en una carpeta** `imgs` y colocar ahi las imagenes
```bash
![imagen de topologia](./imgs/1-topologia.png)
```

## 📥 Archivo de Packet Tracer
- [Descargar mi topología Etapa 1 (.pkt)](etapa1_red.pkt)

#Escribe los comandos que estas ejecuntando para la configuración en tu archivo `readme.md` de la siguiente manera para que se muestren como acontinuación
````markdown
```bash
R1-Core-ELO(config)#interface GigabitEthernet0/0/0.10
```
````




## 📸 Evidencias CLI
```bash
SW-Piso1# show vlan brief
10   Administracion                   active    Fa0/1, Fa0/2
20   Ventas                           active    Fa0/3, Fa0/4
```

A continuación se presenta la configuración de la interfaz en R1-Core:

```cisco
interface GigabitEthernet0/0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.254 255.255.255.0
```
