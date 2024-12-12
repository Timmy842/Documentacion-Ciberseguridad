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

## Consideraciones Finales

- **Permisos:** Algunos escaneos requieren permisos de superusuario para ejecutarse correctamente.
- **Legalidad:** Asegúrate de tener autorización antes de realizar escaneos en redes que no te pertenezcan.
- **Firewall:** Los firewalls pueden bloquear ciertos tipos de escaneo, lo que podría requerir técnicas adicionales para eludir restricciones.

---

## Referencias

- [Nmap Manual](https://nmap.org/book/man.html)
- [Opciones de Escaneo de Hosts](https://nmap.org/book/man-host-discovery.html)
