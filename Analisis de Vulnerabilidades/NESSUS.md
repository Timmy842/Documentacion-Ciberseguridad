# Guía Completa de Nessus

## Introducción

**Nessus** es una herramienta de escaneo de vulnerabilidades desarrollada por **Tenable**. Es una de las soluciones más populares para identificar vulnerabilidades, configuraciones incorrectas y posibles problemas de seguridad en redes, sistemas operativos y aplicaciones.

Nessus es utilizado tanto por profesionales de seguridad como por administradores de sistemas para realizar auditorías y evaluaciones de seguridad.

---

## Características Principales de Nessus

### 1. **Escaneo de Vulnerabilidades**

Nessus permite identificar vulnerabilidades en:
- Sistemas operativos (Windows, Linux, macOS).
- Aplicaciones (Apache, Nginx, etc.).
- Servicios de red (FTP, SSH, SMB).
- Bases de datos (MySQL, MSSQL, Oracle).

Nessus utiliza una amplia base de datos de plugins para realizar escaneos y detectar:
- Vulnerabilidades conocidas (CVE).
- Configuraciones incorrectas.
- Puertos abiertos y servicios activos.
- Políticas de contraseñas débiles.

---

### 2. **Plugins de Nessus**

Nessus utiliza **plugins** para realizar escaneos específicos. Cada plugin corresponde a una vulnerabilidad, configuración o chequeo de seguridad.

- **Base de Datos de Plugins:** Actualizada constantemente con nuevas vulnerabilidades y exploits.
- **Tipos de Plugins:**
  - Escaneo de puertos y servicios.
  - Detección de malware y puertas traseras.
  - Análisis de políticas de configuración.

**Ejemplo de Plugins:**
- *Plugin 19506*: Escaneo de actualización de plugins.
- *Plugin 26917*: Verificación de contraseñas débiles en FTP.

---

### 3. **Tipos de Escaneos en Nessus**

#### a) **Escaneo de Red Local**
Escanea la red interna para identificar vulnerabilidades en sistemas conectados.

#### b) **Escaneo Externo**
Permite evaluar la seguridad desde una perspectiva externa (ideal para pruebas de seguridad perimetral).

#### c) **Escaneo de Configuraciones**
Verifica configuraciones incorrectas en sistemas y aplicaciones según las mejores prácticas.

#### d) **Escaneo de Cumplimiento**
Evalúa si un sistema cumple con los estándares de seguridad y regulaciones, como:
- **PCI-DSS** (Seguridad en datos de tarjetas de crédito).
- **HIPAA** (Seguridad en el sector salud).
- **CIS Benchmarks** (Pautas de configuración segura).

#### e) **Escaneo de Malware**
Detecta software malicioso y puertas traseras conocidas en sistemas comprometidos.

---

### 4. **Análisis de Resultados y Reportes**

Nessus genera reportes detallados con la información recopilada durante el escaneo:
- **Resumen de Vulnerabilidades:** Clasificadas por severidad (Crítico, Alto, Medio, Bajo).
- **Detalles de Vulnerabilidades:**
  - Descripción del problema.
  - Referencias a CVE y bases de datos.
  - Soluciones recomendadas.
- **Gráficas y Estadísticas:** Visualización del estado general de seguridad.

---

## Funcionamiento de Nessus

### 1. **Instalación de Nessus**

Nessus puede instalarse en diferentes sistemas operativos:
- **Linux:** Ubuntu, CentOS, Debian.
- **Windows:** Windows Server, Windows 10/11.
- **macOS:** Todas las versiones compatibles.

**Comandos de Instalación en Linux (ejemplo):**
```bash
dpkg -i Nessus-10.x.x-debian6_amd64.deb
systemctl start nessusd
```

### 2. **Configuración Inicial**

1. Accede a Nessus desde el navegador en `https://localhost:8834`.
2. Crea una cuenta y registra tu código de activación (Nessus Essentials, Professional o Expert).
3. Actualiza los plugins de Nessus para obtener las últimas vulnerabilidades.

### 3. **Creación de un Escaneo**

1. Inicia sesión en la consola web de Nessus.
2. Selecciona **"New Scan"**.
3. Elige una plantilla de escaneo:
   - **Basic Network Scan** (Escaneo de red general).
   - **Advanced Scan** (Configuración personalizada).
   - **Web Application Scan** (Aplicaciones web).
4. Configura el objetivo y las credenciales si es necesario.
5. Inicia el escaneo.

### 4. **Interpretación de Resultados**

Una vez finalizado el escaneo, Nessus mostrará:
- **Resumen de vulnerabilidades por severidad.**
- **Listado detallado con soluciones y recomendaciones.**

---

## Ventajas de Nessus

1. **Base de Datos Actualizada:** Contiene miles de plugins actualizados regularmente.
2. **Escaneos Personalizables:** Permite definir configuraciones específicas.
3. **Informes Detallados:** Facilita el análisis y la toma de decisiones.
4. **Compatibilidad:** Funciona en múltiples sistemas operativos.
5. **Fácil de Usar:** Interfaz gráfica intuitiva.

---

## Versiones de Nessus

1. **Nessus Essentials:** Gratuito, límite de 16 IPs.
2. **Nessus Professional:** Diseñado para escaneos de vulnerabilidades en redes medianas y grandes.
3. **Nessus Expert:** Para análisis avanzados, incluye escaneos en entornos Cloud e IoT.

---

## Consideraciones Finales

- Nessus es una herramienta fundamental para el análisis proactivo de seguridad.
- Utilizar Nessus junto con otras herramientas (como Nmap y Burp Suite) mejora la eficacia de las auditorías.
- Asegúrate de actualizar regularmente los plugins para mantener la información de vulnerabilidades al día.

---

## Referencias

- [Sitio Oficial de Nessus](https://www.tenable.com/products/nessus)
- [Documentación de Nessus](https://docs.tenable.com/nessus)
- [Plugins de Nessus](https://www.tenable.com/plugins)