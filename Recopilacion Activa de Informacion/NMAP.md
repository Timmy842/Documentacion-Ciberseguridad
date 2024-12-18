# Documentacion NMAP

## Descubrimiento de Hosts con Nmap

El descubrimiento de hosts es una de las primeras etapas en un análisis de red. Con Nmap, podemos identificar qué dispositivos están activos en una red, lo que nos permite tener una vista inicial del entorno a auditar. Esta guía detalla los comandos y opciones más comunes para realizar descubrimiento de hosts.

---

## Opciones Básicas de Descubrimiento de Hosts

### Escaneo Ping (`-sn`)
El escaneo ping permite determinar qué hosts están activos sin realizar un escaneo de puertos. Por defecto, Nmap utiliza ICMP, TCP SYN y ARP para comprobar si un host está activo.

**Comando:**
```bash
nmap -sn <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn 192.168.1.0/24
```

---

### Escaneo ARP

En redes locales (Ethernet), el escaneo ARP es más efectivo para identificar hosts activos.

**Comando:**
```bash
nmap -sn -PR <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -PR 192.168.1.0/24
```

---

### Escaneo ICMP

El escaneo ICMP utiliza solicitudes Echo Request para identificar dispositivos que respondan al protocolo ICMP.

**Comando:**
```bash
nmap -sn -PE <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -PE 192.168.1.0/24
```

---

### Escaneo TCP SYN

Envía paquetes TCP SYN al puerto 443 (por defecto) para comprobar si un host está activo.

**Comando:**
```bash
nmap -sn -PS <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -PS 192.168.1.0/24
```

**Nota:** Puedes especificar puertos personalizados añadiendo `-PS<puerto>`.

---

### Escaneo TCP ACK

Envía paquetes TCP ACK al puerto 80 (por defecto).

**Comando:**
```bash
nmap -sn -PA <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -PA 192.168.1.0/24
```

---

## Opciones Avanzadas

### Personalizar Rangos de IP
Puedes especificar rangos de IP con formatos personalizados:

- Rango completo: `192.168.1.0/24`
- Rango específico: `192.168.1.1-192.168.1.10`
- IPs separadas por comas: `192.168.1.1,192.168.1.5,192.168.1.10`

---

### Evitar Resolución de DNS (`-n`)
Para acelerar el escaneo y evitar la resolución inversa de DNS:

**Comando:**
```bash
nmap -sn -n <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -n 192.168.1.0/24
```

---

### Incrementar el Nivel de Verbo (`-v`)
Para obtener más detalles sobre el progreso del escaneo:

**Comando:**
```bash
nmap -sn -v <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -v 192.168.1.0/24
```

---

## Guardar Resultados

Puedes guardar los resultados del escaneo en diferentes formatos:

### Guardar en un Archivo de Texto
**Comando:**
```bash
nmap -sn -oN <archivo_salida> <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -oN resultados.txt 192.168.1.0/24
```

### Guardar en Formato XML
**Comando:**
```bash
nmap -sn -oX <archivo_salida> <rango_de_ips>
```
**Ejemplo:**
```bash
nmap -sn -oX resultados.xml 192.168.1.0/24
```

---

## Descubrimiento de Puertos con Nmap

El descubrimiento de puertos es una etapa fundamental en el análisis de redes y sistemas. Con **Nmap**, podemos identificar puertos abiertos y servicios activos en un host o red. Esto nos proporciona información clave para evaluar el estado de seguridad de un sistema.

---

## Escaneos Comunes de Puertos

### Escaneo TCP SYN (`-sS`)
Es el escaneo más rápido y común. Envia un paquete TCP SYN para determinar el estado de un puerto (abierto, cerrado o filtrado).

**Comando:**
```bash
nmap -sS <objetivo>
```
**Ejemplo:**
```bash
nmap -sS 192.168.1.1
```

---

### Escaneo TCP Connect (`-sT`)
Realiza una conexión completa al puerto objetivo. Es más lento y detectable que el escaneo SYN.

**Comando:**
```bash
nmap -sT <objetivo>
```
**Ejemplo:**
```bash
nmap -sT 192.168.1.1
```

---

### Escaneo UDP (`-sU`)
Explora puertos UDP en busca de servicios activos. Este tipo de escaneo puede ser más lento debido a la naturaleza del protocolo UDP.

**Comando:**
```bash
nmap -sU <objetivo>
```
**Ejemplo:**
```bash
nmap -sU 192.168.1.1
```

---

### Escaneo de Puertos Específicos
Puedes especificar qué puertos escanear con la opción `-p`.

**Comando:**
```bash
nmap -p <puertos> <objetivo>
```
**Ejemplo:**
```bash
nmap -p 22,80,443 192.168.1.1
```
Para escanear todos los puertos (1-65535):
```bash
nmap -p- <objetivo>
```

---

### Escaneo de Puertos Comúnmente Usados
El escaneo por defecto en Nmap cubre los 1,000 puertos más comunes. Puedes forzar este comportamiento con:

**Comando:**
```bash
nmap --top-ports 1000 <objetivo>
```
**Ejemplo:**
```bash
nmap --top-ports 1000 192.168.1.1
```

---

## Opciones Avanzadas

### Detectar Servicios y Versiones (`-sV`)
Identifica servicios y versiones en los puertos abiertos.

**Comando:**
```bash
nmap -sV <objetivo>
```
**Ejemplo:**
```bash
nmap -sV 192.168.1.1
```

---

### Escaneo Silencioso (`-T0` o `-T1`)
Para minimizar la detección en sistemas con medidas de seguridad, usa configuraciones lentas.

**Comando:**
```bash
nmap -T1 <objetivo>
```
**Ejemplo:**
```bash
nmap -T1 192.168.1.1
```

---

### Evitar Resolución DNS (`-n`)
Para evitar la resolución inversa de nombres de dominio, utiliza la opción `-n`.

**Comando:**
```bash
nmap -n <objetivo>
```
**Ejemplo:**
```bash
nmap -n 192.168.1.1
```

---

### Detección de Sistemas Operativos (`-O`)
Este escaneo intenta identificar el sistema operativo del objetivo.

**Comando:**
```bash
nmap -O <objetivo>
```
**Ejemplo:**
```bash
nmap -O 192.168.1.1
```

---

## Guardar Resultados

### Guardar en Archivo de Texto
**Comando:**
```bash
nmap -oN <archivo_salida> <objetivo>
```
**Ejemplo:**
```bash
nmap -oN resultados.txt 192.168.1.1
```

### Guardar en Formato XML
**Comando:**
```bash
nmap -oX <archivo_salida> <objetivo>
```
**Ejemplo:**
```bash
nmap -oX resultados.xml 192.168.1.1
```

---

## Estados de los Puertos con Nmap

Cuando realizamos un escaneo con Nmap, los puertos de los objetivos analizados pueden reportarse en diferentes estados. Estos estados son clave para entender el comportamiento de los servicios y la configuración del sistema objetivo.

Esta guía describe los posibles estados de los puertos que Nmap puede identificar y su significado.

---

## Estados de los Puertos

### 1. **Abierto (Open)**

Un puerto se considera **abierto** si está aceptando conexiones activas. Esto indica que hay un servicio en escucha en ese puerto.

- **Significado:**
  - Hay un servicio o aplicación que puede interactuar con los clientes.
  - Este es el estado más relevante para el análisis de servicios y vulnerabilidades.

- **Ejemplo de salida en Nmap:**
  ```bash
  PORT    STATE SERVICE
  80/tcp  open  http
  ```

---

### 2. **Cerrado (Closed)**

Un puerto está **cerrado** si no hay ningún servicio en escucha en él, pero el puerto es accesible y responde a los paquetes enviados.

- **Significado:**
  - Aunque no hay servicios activos, el puerto puede convertirse en un objetivo si un servicio se habilita posteriormente.
  - Es útil para evaluar políticas de firewall y medidas de seguridad.

- **Ejemplo de salida en Nmap:**
  ```bash
  PORT    STATE SERVICE
  22/tcp  closed ssh
  ```

---

### 3. **Filtrado (Filtered)**

Un puerto se clasifica como **filtrado** cuando los paquetes enviados no pueden determinar si el puerto está abierto o cerrado, generalmente debido a un firewall que bloquea los paquetes.

- **Significado:**
  - La comunicación directa con el puerto está restringida.
  - Puede indicar la presencia de un firewall o dispositivo de seguridad en la red.

- **Ejemplo de salida en Nmap:**
  ```bash
  PORT    STATE SERVICE
  25/tcp  filtered smtp
  ```

---

### 4. **No Filtrado (Unfiltered)**

Un puerto está **no filtrado** si Nmap puede acceder a él, pero no puede determinar si está abierto o cerrado.

- **Significado:**
  - Es menos común y generalmente requiere escaneos adicionales para obtener más información.

- **Ejemplo de salida en Nmap:**
  ```bash
  PORT    STATE SERVICE
  53/tcp  unfiltered domain
  ```

---

### 5. **Indeterminado (Open|Filtered)**

Un puerto aparece como **Open|Filtered** cuando Nmap no puede determinar si el puerto está abierto o filtrado.

- **Significado:**
  - Ocurre típicamente en escaneos UDP o en sistemas protegidos por firewalls.
  - Puede requerir técnicas adicionales para clarificar el estado real.

- **Ejemplo de salida en Nmap:**
  ```bash
  PORT    STATE SERVICE
  123/udp open|filtered ntp
  ```

---

### 6. **Cerrado|Filtrado (Closed|Filtered)**

Este estado indica que Nmap no puede determinar si un puerto está cerrado o filtrado.

- **Significado:**
  - Es menos común y generalmente ocurre en redes con políticas de seguridad avanzadas.

---

## Relevancia de los Estados de Puertos

- **Abierto:** Identifica posibles puntos de entrada y servicios activos.
- **Cerrado:** Indica accesibilidad, aunque sin servicios activos.
- **Filtrado:** Destaca posibles barreras de seguridad como firewalls.
- **Open|Filtered:** Sugiere necesidad de técnicas avanzadas para clarificación.

---

## Consejos para Analizar Estados de Puertos

1. **Escaneo de Versiones (`-sV`):** Ayuda a identificar servicios específicos en puertos abiertos.
   ```bash
   nmap -sV <objetivo>
   ```

2. **Escaneo UDP (`-sU`):** Para verificar estados de puertos UDP, donde Open|Filtered es común.
   ```bash
   nmap -sU <objetivo>
   ```

3. **Escaneo Intensivo (`-T4`):** Aumenta la velocidad del escaneo para obtener resultados más rápidos.
   ```bash
   nmap -T4 <objetivo>
   ```

---

## Consideraciones Finales

- Los estados de puertos ayudan a entender la arquitectura y seguridad de una red.
- Usa herramientas adicionales como firewalls o IDS para confirmar resultados obtenidos por Nmap.
- Realiza siempre escaneos con autorización.

---

## Opciones Principales para Descubrimiento de Servicios

El descubrimiento de servicios es una etapa crucial para identificar qué aplicaciones o procesos están escuchando en puertos específicos de un sistema objetivo. Con **Nmap**, podemos obtener información detallada sobre los servicios que se ejecutan en los puertos abiertos y, en muchos casos, identificar su versión.

---

### 1. **Detección de Servicios y Versiones (`-sV`):**

Esta opción permite identificar servicios y sus versiones en puertos abiertos. Nmap envía una serie de peticiones específicas para analizar las respuestas y deducir el servicio.

**Comando:**
```bash
nmap -sV <objetivo>
```

**Ejemplo:**
```bash
nmap -sV 192.168.1.1
```

**Salida típica:**
```bash
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 8.2
80/tcp  open  http    Apache httpd 2.4.41
```

---

### 2. **Detección Intensa de Servicios (`--version-intensity`):**

Controla el nivel de intensidad del escaneo de servicios. Por defecto, se usa un nivel de 7 (máximo). Puedes reducirlo para acelerar el proceso.

**Comando:**
```bash
nmap -sV --version-intensity <nivel> <objetivo>
```

**Ejemplo:**
```bash
nmap -sV --version-intensity 5 192.168.1.1
```

---

### 3. **Forzar Protocolos Específicos (`--version-light` y `--version-all`):**

- **`--version-light`**: Realiza una detección más rápida y ligera.
- **`--version-all`**: Intenta identificar servicios en todos los puertos detectados, sin restricciones.

**Comandos:**
```bash
nmap -sV --version-light <objetivo>
```
```bash
nmap -sV --version-all <objetivo>
```

---

### 4. **Detección de Scripts (`-sC` o `--script`):**

Utiliza scripts NSE (Nmap Scripting Engine) para obtener información adicional sobre los servicios descubiertos.

**Comando:**
```bash
nmap -sC <objetivo>
```

**Ejemplo:**
```bash
nmap -sV -sC 192.168.1.1
```

**Salida típica:**
```bash
PORT    STATE SERVICE VERSION
80/tcp  open  http    Apache httpd 2.4.41
| http-title: Welcome to Apache!
| http-methods: GET POST OPTIONS
```

---

### 5. **Especificar Puertos para el Escaneo (`-p`):**

Si quieres enfocar el descubrimiento de servicios en puertos específicos, usa la opción `-p`.

**Comando:**
```bash
nmap -sV -p <puertos> <objetivo>
```

**Ejemplo:**
```bash
nmap -sV -p 22,80,443 192.168.1.1
```

---

## Combinación con Otras Opciones

### Combinar con Detección de Sistemas Operativos (`-O`):
Puedes combinar la detección de servicios con la identificación del sistema operativo para obtener un perfil más completo del objetivo.

**Comando:**
```bash
nmap -sV -O <objetivo>
```

**Ejemplo:**
```bash
nmap -sV -O 192.168.1.1
```

### Escaneo en Modo Verboso (`-v`):
Para obtener más detalles durante el proceso de escaneo.

**Comando:**
```bash
nmap -sV -v <objetivo>
```

**Ejemplo:**
```bash
nmap -sV -v 192.168.1.1
```

---

## Interpretación de Resultados

- **SERVICE:** Indica el servicio en ejecución (e.g., HTTP, SSH).
- **VERSION:** Proporciona la versión detectada del servicio.
- **SCRIPTS:** Salida adicional proporcionada por los scripts NSE.

---

# Identificación del Sistema Operativo con Nmap

## Introducción

La identificación del sistema operativo (OS detection) es una funcionalidad clave de **Nmap** que permite determinar el sistema operativo que está ejecutando un host objetivo. Esto es particularmente útil para obtener un perfil más completo de la infraestructura y detectar posibles vulnerabilidades específicas de un sistema operativo.

Nmap utiliza técnicas avanzadas para analizar las características de los paquetes enviados y las respuestas del objetivo, comparándolos con una base de datos de firmas conocida.

---

## Opciones Principales para la Identificación de Sistemas Operativos

### 1. **Habilitar la Detección de Sistemas Operativos (`-O`)**

Esta opción activa la identificación del sistema operativo del objetivo.

**Comando:**
```bash
nmap -O <objetivo>
```

**Ejemplo:**
```bash
nmap -O 192.168.1.1
```

**Salida típica:**
```bash
OS details: Linux 5.4 - 5.8 (Ubuntu)
```

---

### 2. **Combinar con Escaneo de Versiones (`-sV`)**

La combinación de detección de sistemas operativos y servicios permite obtener un perfil más detallado del objetivo.

**Comando:**
```bash
nmap -O -sV <objetivo>
```

**Ejemplo:**
```bash
nmap -O -sV 192.168.1.1
```

---

### 3. **Técnicas de Huella Digital Activa (`--osscan-guess`)**

Si Nmap no puede identificar el sistema operativo con precisión, esta opción permite realizar suposiciones informadas basadas en características similares.

**Comando:**
```bash
nmap -O --osscan-guess <objetivo>
```

**Ejemplo:**
```bash
nmap -O --osscan-guess 192.168.1.1
```

**Salida típica:**
```bash
Aggressive OS guesses: Linux 5.4 (80%)
```

---

### 4. **Modo Verboso (`-v`)**

Para obtener más detalles sobre el proceso de identificación de sistemas operativos.

**Comando:**
```bash
nmap -O -v <objetivo>
```

**Ejemplo:**
```bash
nmap -O -v 192.168.1.1
```

---

## Interpretación de Resultados

- **`OS details`**: Muestra el sistema operativo identificado y su versión aproximada.
- **`Aggressive OS guesses`**: Cuando no hay coincidencias exactas, Nmap intenta hacer suposiciones basadas en patrones similares.

---

## Consejos para Mejorar la Detección

1. **Usar Privilegios de Superusuario:** Algunos escaneos requieren acceso root para enviar ciertos tipos de paquetes.
   ```bash
   sudo nmap -O <objetivo>
   ```

2. **Combinar con Escaneo de Red Completo:** Incluye técnicas de descubrimiento de hosts y puertos.
   ```bash
   nmap -O -sS -T4 <objetivo>
   ```

3. **Reducir el Nivel de Velocidad (`-T1`):** Puede ayudar en redes protegidas por firewalls.
   ```bash
   nmap -O -T1 <objetivo>
   ```

---

## Limitaciones

- **Firewalls y Sistemas de Detección de Intrusos:** Pueden bloquear o alterar las respuestas, dificultando la identificación.
- **Redes Seguras:** Algunas configuraciones avanzadas pueden impedir que Nmap identifique correctamente el sistema operativo.

---

## Consideraciones Legales

Asegúrate de tener autorización antes de realizar un escaneo de sistemas operativos en cualquier red que no te pertenezca.

---

# Enumeración de SMB con Nmap

## Introducción

La enumeración de SMB (Server Message Block) permite recopilar información sobre recursos compartidos, usuarios y configuraciones en sistemas que utilizan este protocolo. Con **Nmap** y su potente motor de scripts (NSE), podemos identificar y analizar servicios SMB en sistemas objetivos de manera eficiente.

---

## Scripts de Nmap para SMB

### 1. **Detección de Servicios SMB (`smb-protocols`)**
Este script identifica las versiones de SMB soportadas por el sistema objetivo (SMBv1, SMBv2, SMBv3).

**Comando:**
```bash
nmap --script smb-protocols -p 445 <objetivo>
```

**Ejemplo:**
```bash
nmap --script smb-protocols -p 445 192.168.1.1
```

**Salida típica:**
```bash
445/tcp open  microsoft-ds
| smb-protocols: 
|   dialects: 
|     2.02 
|     2.10 
|     3.00 
|_    3.11
```

---

### 2. **Enumeración de Recursos Compartidos (`smb-enum-shares`)**
Este script lista los recursos compartidos en el servidor SMB, como carpetas públicas o protegidas.

**Comando:**
```bash
nmap --script smb-enum-shares -p 445 <objetivo>
```

**Ejemplo:**
```bash
nmap --script smb-enum-shares -p 445 192.168.1.1
```

**Salida típica:**
```bash
445/tcp open  microsoft-ds
| smb-enum-shares: 
|   account_used: guest
|   \Public 
|     Type: Disk 
|     Comment: Public Folder
|_  \IPC$ 
```

---

### 3. **Enumeración de Usuarios (`smb-enum-users`)**
Este script enumera usuarios en el servidor SMB objetivo.

**Comando:**
```bash
nmap --script smb-enum-users -p 445 <objetivo>
```

**Ejemplo:**
```bash
nmap --script smb-enum-users -p 445 192.168.1.1
```

**Salida típica:**
```bash
445/tcp open  microsoft-ds
| smb-enum-users: 
|   DOMAIN\user1 
|   DOMAIN\user2 
|_  DOMAIN\admin
```

---

### 4. **Detección de Vulnerabilidades SMB**

#### **Verificación de EternalBlue (`smb-vuln-ms17-010`)**
Este script verifica si el sistema es vulnerable al exploit EternalBlue (MS17-010).

**Comando:**
```bash
nmap --script smb-vuln-ms17-010 -p 445 <objetivo>
```

**Ejemplo:**
```bash
nmap --script smb-vuln-ms17-010 -p 445 192.168.1.1
```

**Salida típica:**
```bash
445/tcp open  microsoft-ds
| smb-vuln-ms17-010: 
|   VULNERABLE: 
|   Remote Code Execution vulnerability in Microsoft SMBv1
|_  Risk Factor: Critical
```

#### **Otros Scripts de Vulnerabilidad**
- `smb-vuln-cve-2020-0796`: SMBv3 Compresión.
- `smb-vuln-ms08-067`: Ejecución remota en SMBv1.

**Comando General:**
```bash
nmap --script <nombre_del_script> -p 445 <objetivo>
```

---

## Comandos Combinados

Para ejecutar múltiples scripts en un solo comando:

**Comando:**
```bash
nmap --script "smb-*" -p 445 <objetivo>
```

**Ejemplo:**
```bash
nmap --script "smb-enum-shares,smb-enum-users,smb-vuln-ms17-010" -p 445 192.168.1.1
```

---

## Consejos para Mejorar la Enumeración

1. **Usar Escaneo Verboso (`-v`):**
   Proporciona más detalles sobre el progreso del escaneo.
   ```bash
   nmap --script smb-enum-shares -v -p 445 192.168.1.1
   ```

2. **Elevar Privilegios (sudo):** Algunos scripts requieren permisos de superusuario.
   ```bash
   sudo nmap --script smb-enum-users -p 445 192.168.1.1
   ```

3. **Combinar con Escaneos Generales:**
   Integra descubrimiento de servicios y sistemas operativos para obtener más contexto.
   ```bash
   nmap -sV -O --script smb-enum-shares -p 445 192.168.1.1
   ```

---

## Consideraciones Legales

Asegúrate de contar con la debida autorización antes de realizar escaneos SMB en redes externas o de terceros. 

---

# Enumeración de SNMP con Nmap

## Introducción

El Protocolo Simple de Gestión de Red (**SNMP**, por sus siglas en inglés) es utilizado para monitorear y administrar dispositivos de red. La enumeración de SNMP permite recopilar información importante como nombres de dispositivos, tablas ARP, configuraciones de red, e incluso contraseñas si el protocolo está mal configurado.

Con **Nmap**, puedes utilizar scripts NSE para realizar una enumeración eficaz de SNMP.

---

## Scripts de Nmap para Enumeración de SNMP

### 1. **Detección de Servicios SNMP (`snmp-info`)**

Este script recopila información general sobre el dispositivo y su configuración SNMP.

**Comando:**
```bash
nmap --script snmp-info -p 161 <objetivo>
```

**Ejemplo:**
```bash
nmap --script snmp-info -p 161 192.168.1.1
```

**Salida típica:**
```bash
161/udp open  snmp
| snmp-info: 
|   enterprise: Cisco Systems 
|   version: 2c 
|_  contact: admin@example.com
```

---

### 2. **Enumeración de Tablas SNMP (`snmp-walk`)**

Este script realiza una consulta de tipo *walk* en el dispositivo SNMP y lista información relevante.

**Comando:**
```bash
nmap --script snmp-walk -p 161 <objetivo>
```

**Ejemplo:**
```bash
nmap --script snmp-walk -p 161 192.168.1.1
```

**Salida típica:**
```bash
161/udp open  snmp
| snmp-walk: 
|   sysName.0: Router01
|   sysUpTime.0: 15 days, 3:42:17.34
|   sysContact.0: admin@example.com
|_  sysLocation.0: Data Center A
```

---

### 3. **Enumeración de Cadenas de Comunidad (`snmp-brute`)**

Este script intenta identificar cadenas de comunidad SNMP mediante un ataque de fuerza bruta.

**Comando:**
```bash
nmap --script snmp-brute -p 161 <objetivo>
```

**Ejemplo:**
```bash
nmap --script snmp-brute -p 161 192.168.1.1
```

**Salida típica:**
```bash
161/udp open  snmp
| snmp-brute: 
|   public - read-only 
|_  private - read-write
```

---

### 4. **Consulta de Árboles OID (`snmp-oid`)**

Este script recupera información de árboles OID específicos en el dispositivo objetivo.

**Comando:**
```bash
nmap --script snmp-oid -p 161 <objetivo>
```

**Ejemplo:**
```bash
nmap --script snmp-oid -p 161 192.168.1.1
```

---

### 5. **Identificación de Configuraciones Vulnerables (`snmp-netstat`)**

Consulta la tabla de rutas y las conexiones activas del dispositivo.

**Comando:**
```bash
nmap --script snmp-netstat -p 161 <objetivo>
```

**Ejemplo:**
```bash
nmap --script snmp-netstat -p 161 192.168.1.1
```

**Salida típica:**
```bash
161/udp open  snmp
| snmp-netstat: 
|   Interface: eth0 
|     IP: 192.168.1.1/24 
|     MTU: 1500 
|_  Routes: 192.168.1.0/24 via 192.168.1.254
```

---

## Combinaciones de Scripts

Puedes combinar múltiples scripts para realizar una enumeración completa de SNMP.

**Comando:**
```bash
nmap --script "snmp-*" -p 161 <objetivo>
```

**Ejemplo:**
```bash
nmap --script "snmp-info,snmp-walk,snmp-brute" -p 161 192.168.1.1
```

---

## Consejos para Mejorar la Enumeración

1. **Especificar Comunidad SNMP:** Si conoces la cadena de comunidad, úsala con la opción `--script-args`.
   ```bash
   nmap --script snmp-info --script-args snmpcommunity=<comunidad> -p 161 <objetivo>
   ```

2. **Usar Escaneo Verboso (`-v`):** Obtén más detalles durante el escaneo.
   ```bash
   nmap --script snmp-walk -v -p 161 192.168.1.1
   ```

3. **Ejecutar con Privilegios:** Algunos scripts requieren permisos elevados (sudo).
   ```bash
   sudo nmap --script snmp-netstat -p 161 192.168.1.1
   ```

---

## Consideraciones Legales

Asegúrate de contar con la autorización necesaria antes de realizar escaneos SNMP en redes externas o de terceros. 

---

## Consideraciones Finales

- **Permisos:** Algunos escaneos requieren permisos de superusuario para ejecutarse correctamente.
- **Legalidad:** Asegúrate de tener autorización antes de realizar escaneos en redes que no te pertenezcan.
- **Firewall:** Los firewalls pueden bloquear ciertos tipos de escaneo, lo que podría requerir técnicas adicionales para eludir restricciones.

---

## Referencias

- [Nmap Manual](https://nmap.org/book/man.html)
- [Opciones de Escaneo de Hosts](https://nmap.org/book/man-host-discovery.html)
