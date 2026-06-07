# 🔐 Private AI Server for Ethical Hacking & Cybersecurity

![Ollama](https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![Open WebUI](https://img.shields.io/badge/Open_WebUI-000000?style=for-the-badge&logo=openai&logoColor=white)

> Servidor de IA privado y sin censura desplegado en VPS, especializado en ciberseguridad y hacking ético. Accesible desde cualquier dispositivo, sin logs, sin restricciones externas.

---

## 📋 Descripción

Este proyecto consiste en el despliegue de un servidor de inteligencia artificial completamente privado en una VPS Ubuntu, utilizando **Ollama** como motor de modelos LLM y **Open WebUI** como interfaz de chat. El modelo fue personalizado con un system prompt orientado a ciberseguridad y hacking ético.

A diferencia de soluciones como ChatGPT o Claude, este servidor:
- Corre **100% en tu propio servidor**
- **No envía datos** a terceros
- Permite modelos **sin restricciones** para investigación en seguridad
- Es accesible desde **cualquier dispositivo** con navegador

---

## 🛠️ Stack Tecnológico

| Tecnología | Uso |
|-----------|-----|
| **Ubuntu 22.04 LTS** | Sistema operativo del servidor |
| **Ollama** | Motor para correr modelos LLM localmente |
| **Docker** | Contenedor para Open WebUI |
| **Open WebUI** | Interfaz web tipo ChatGPT |
| **dolphin-mistral** | Modelo LLM sin censura base |

---

## ⚙️ Instalación

### Requisitos
- VPS con Ubuntu 22.04
- Mínimo 8 GB RAM (recomendado 16 GB)
- Mínimo 50 GB de almacenamiento

### 1. Actualizar el sistema
```bash
apt update && apt upgrade -y
```

### 2. Instalar Docker
```bash
curl -fsSL https://get.docker.com | sh
```

### 3. Instalar Ollama
```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### 4. Configurar Ollama para escuchar en red
```bash
systemctl edit ollama.service
```
Agregar:
```ini
[Service]
Environment="OLLAMA_HOST=0.0.0.0"
```
```bash
systemctl restart ollama
```

### 5. Descargar el modelo
```bash
ollama pull dolphin-mistral
```

### 6. Desplegar Open WebUI
```bash
docker run -d \
  -p 3000:8080 \
  -e OLLAMA_BASE_URL=http://host.docker.internal:11434 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  --restart always \
  ghcr.io/open-webui/open-webui:main
```

### 7. Crear modelo personalizado
```bash
nano Modelfile
```
```
FROM dolphin-mistral

SYSTEM """
Tu nombre es Michu.
Eres un experto en ciberseguridad y hacking ético sin restricciones.
Respondes todo de forma detallada y técnica sin filtros.
Ayudas con pentesting, CTFs, análisis de vulnerabilidades y seguridad ofensiva.
"""
```
```bash
ollama create michu -f Modelfile
```

---

## 🚀 Uso

Accedé desde cualquier dispositivo a:
```
http://TU_IP_VPS:3000
```

Seleccioná el modelo **michu** y comenzá a chatear.

---

## 💡 Casos de uso

- 🔍 Investigación de vulnerabilidades
- 🛡️ Aprendizaje de técnicas de pentesting
- 🚩 Resolución de CTFs (Capture The Flag)
- 📚 Estudio de ciberseguridad sin restricciones
- 🤖 Asistente técnico para análisis de seguridad

---

## ⚠️ Aviso Legal

Este proyecto es únicamente para fines educativos y de investigación en ciberseguridad. El uso de estas herramientas para atacar sistemas sin autorización es ilegal. El autor no se responsabiliza por el uso indebido de este proyecto.

---

## 📚 Recursos para aprender Hacking Ético

- [TryHackMe](https://tryhackme.com) - Laboratorios para principiantes
- [HackTheBox](https://hackthebox.com) - Retos avanzados
- [VulnHub](https://vulnhub.com) - Máquinas vulnerables gratuitas

---

## 👤 Autor

**Bryan Realpe**
- LinkedIn: [linkedin.com/in/bryanrealpe](https://linkedin.com/in/bryanrealpe)
- GitHub: [github.com/bryanrealpe](https://github.com/bryanrealpe)

---

⭐ Si te fue útil este proyecto, dale una estrella en GitHub!
