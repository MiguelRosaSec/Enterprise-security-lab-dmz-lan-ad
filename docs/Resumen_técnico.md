# Resumen Técnico del Proyecto

# Resumen Técnico del Proyecto

## 1. Objetivo

Diseñar, desplegar, explotar y posteriormente fortificar una infraestructura empresarial segmentada, simulando un entorno corporativo real con malas prácticas intencionadas.

El proyecto integra:
- Administración de sistemas Linux y Windows
- Contenedores Docker
- Segmentación de red (DMZ / LAN / AD)
- Active Directory
- Pentesting ofensivo
- Hardening defensivo

---

## 2. Arquitectura Implementada

### Segmentación de Red

- **DMZ (10.10.10.0/24)**
  - WordPress vulnerable
  - DVWA
  - phpMyAdmin
  - MySQL compartido
  - Docker con configuración insegura

- **LAN (10.10.20.0/24)**
  - Aplicación PHP vulnerable a SQL Injection
  - MariaDB
  - SSH reforzado
  - Cliente Windows 10 unido al dominio

- **Active Directory**
  - Windows Server 2022
  - AD DS
  - DNS
  - IIS + WebDAV vulnerable
  - GPO mal configuradas

---

## 3. Metodología de Auditoría

Se siguió un enfoque alineado con PTES:

1. Reconocimiento
2. Enumeración
3. Explotación inicial
4. Escalada de privilegios
5. Pivoting
6. Movimiento lateral
7. Compromiso de Active Directory
8. Evaluación de impacto

---

## 4. Cadena de Ataque Resumida

- Explotación de WordPress (XML-RPC)
- Reverse shell en contenedor
- Escape de contenedor Docker
- Acceso SSH al host DMZ
- Pivoting hacia LAN
- SQL Injection Time-Based Blind
- Obtención de credenciales internas
- Explotación WebDAV en Windows Server
- Ataque DCSync
- Extracción de hashes NTLM
- Acceso SYSTEM en Windows 10

Resultado: Compromiso completo del dominio en entorno controlado.

---

## 5. Medidas de Fortificación Aplicadas

### Infraestructura Linux
- Eliminación de CGI vulnerable
- Restricción de MySQL
- Hardening básico del sistema

### Docker
- Eliminación de modo privilegiado
- Eliminación de bind mounts inseguros
- Aislamiento de red

### Active Directory
- Políticas de contraseñas robustas
- Bloqueo de cuentas
- Deshabilitación SMBv1
- Eliminación WebDAV
- Reducción de privilegios excesivos

### Cliente Windows
- Eliminación de privilegios administrativos innecesarios
- Refuerzo de firewall
- Restricción de ejecución remota

---

## 6. Impacto Empresarial

El proyecto demuestra cómo:

- La falta de segmentación facilita el movimiento lateral.
- La reutilización de credenciales amplifica el riesgo.
- Un único servicio vulnerable puede comprometer todo el dominio.
- El impacto potencial incluye pérdida de datos, sanciones RGPD y daño reputacional.

---

## 7. Conclusión

La seguridad debe abordarse como un sistema completo y no como elementos aislados.  
Este laboratorio demuestra tanto la capacidad ofensiva para comprometer una infraestructura como la capacidad defensiva para restaurarla y reforzarla.
