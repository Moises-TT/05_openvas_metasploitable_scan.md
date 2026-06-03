# 🔒 Escaneo de Vulnerabilidades: OpenVAS + Metasploitable3

> Análisis de vulnerabilidades de una máquina Metasploitable3 usando OpenVAS/Greenbone en entorno KVM.

---

## 📋 Descripción

Laboratorio de gestión de vulnerabilidades donde se configuró **OpenVAS (Greenbone)** en un servidor Ubuntu Server vía Docker para escanear una máquina virtual **Metasploitable3** (máquina intencionalmente vulnerable).  
Se creó el target, se configuró la tarea de escaneo y se generó el reporte de vulnerabilidades detectadas.

---

## 🛠️ Stack y Herramientas

| Tecnología | Uso |
|-----------|-----|
| Ubuntu Server | Servidor OpenVAS |
| Docker + Docker Compose | Despliegue de OpenVAS |
| Greenbone Community Edition | Plataforma de análisis de vulnerabilidades |
| Metasploitable3 | Máquina objetivo (intencionalmente vulnerable) |
| KVM / QEMU | Virtualización de ambas máquinas |
| Fedora 43 | Sistema anfitrión |

---

## 🔬 Proceso del Laboratorio

### 1. Preparación del entorno
- Ubuntu Server actualizado y con Docker instalado
- Motor Docker habilitado con `systemctl enable docker`
- Archivo `docker-compose.yml` de Greenbone configurado y ejecutado

### 2. Levantar Metasploitable3 en KVM
La guía oficial de Metasploitable3 fue adaptada para KVM/QEMU en Fedora Linux.  
Se realizó conexión SSH a la máquina víctima desde la terminal de Fedora.

### 3. Crear Target en OpenVAS

```
Menú: Configuración → Targets → Nuevo Target
Nombre: Metasploitable3
IP: <IP de la VM Metasploitable>
```

### 4. Crear y ejecutar tarea de escaneo

```
Menú: Escaneos → Tareas → Nueva Tarea
Target: Metasploitable3 (configurado en paso anterior)
Acción: Ejecutar → esperar completar al 100%
```

### 5. Análisis del reporte
- Escaneo ejecutado con proceso de +3 horas
- Progreso alcanzado: 82%+ con reporte generado exitosamente
- El reporte muestra vulnerabilidades clasificadas por severidad (Critical, High, Medium, Low)

---

## 📊 Resultados del Escaneo

El reporte de OpenVAS identificó múltiples vectores de ataque en Metasploitable3:

- Servicios con versiones desactualizadas y CVEs conocidos
- Puertos abiertos innecesarios
- Configuraciones inseguras por defecto
- Credenciales débiles en servicios de red

---

## 🧠 Aprendizajes

- Configuración y uso de OpenVAS para análisis de vulnerabilidades
- Creación de targets y tareas de escaneo en Greenbone
- Interpretación de reportes de vulnerabilidades (CVSS score)
- Diferencia entre escaneo activo y análisis pasivo
- Importancia del hardening de servicios expuestos

---

## ⚠️ Aviso Legal

Laboratorio realizado en red aislada con máquinas **intencionalmente vulnerables**.  
No aplicar en infraestructuras reales sin autorización escrita.
