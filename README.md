[README.md](https://github.com/user-attachments/files/28615238/README.md)
# 🌿 Casa Vita BranSan
### Invitaciones Digitales & Páginas Web de Eventos

> Diseño personalizado para bodas, XV años, baby showers, graduaciones y más.
> Monterrey, N.L. · [casavitabransan.netlify.app](https://casavitabransan.netlify.app)

---

## 📁 Estructura del repositorio

```
casa-vita-bransan/
│
├── index.html                  # Landing principal
├── cotizar.html                # Formulario de cotización (3 pasos)
│
├── boda-ana-diego.html         # Ejemplo — Boda (Premium $1,100)
├── xv-anos-isabela.html        # Ejemplo — XV años (Premium $1,100)
├── baby-shower-valeria.html    # Ejemplo — Baby Shower (Web $750)
│
├── xv-foto1.png                # Fotos sesión Isabela
├── xv-foto2.png
├── xv-foto3.png
├── xv-foto4.png
├── xv-foto5.png
│
├── [cliente]-foto1.png         # Fotos de clientes reales (prefijo único por evento)
│
└── README.md                   # Este archivo
```

---

## 🌐 Páginas activas

| Archivo | URL | Descripción |
|---|---|---|
| `index.html` | `/` | Landing principal con servicios, ejemplos y precios |
| `cotizar.html` | `/cotizar` | Formulario de cotización — 3 pasos + página de gracias |
| `boda-ana-diego.html` | `/boda-ana-diego` | Ejemplo premium estilo ranch/western |
| `xv-anos-isabela.html` | `/xv-anos-isabela` | Ejemplo premium estilo rose gold |
| `baby-shower-valeria.html` | `/baby-shower-valeria` | Ejemplo web normal estilo dusty rose |

---

## 💰 Catálogo de servicios

| Servicio | Precio | Express 24 hrs |
|---|---|---|
| Invitación digital básica | $250 MXN | +$150 |
| Invitación con video o GIF | $350 MXN | +$150 |
| Página web de evento | $750 MXN | +$500 |
| Página web premium (boda / XV) | $1,100 MXN | +$500 |

**Métodos de pago:** Transferencia · Depósito · Stripe · Oxxo · Spin

---

## ⚙️ Automatización — Make.com

El formulario `cotizar.html` está conectado a un **Scenario en Make.com** que procesa cada lead automáticamente.

### Flujo del Scenario

```
Webhook (cotizar.html)
        ↓
Google Sheets — registrar lead
        ↓
UltraMsg — notificación a Sandy (todos los leads)
        ↓
Filter — ¿temperatura = "caliente 🔥"?
        ↓
UltraMsg — alerta urgente a Sandy (solo leads calientes)
```

### JSON que envía el formulario

```json
{
  "fecha":       "4/6/2025, 10:32:00 a.m.",
  "nombre":      "María García",
  "whatsapp":    "81 1234 5678",
  "tipo":        "Boda",
  "fuente":      "Facebook Ads",
  "estado":      "Nuevo",
  "temperatura": "caliente 🔥",
  "seguimiento": "Lo necesito urgente (menos de 1 mes)"
}
```

### Clasificación automática de temperatura

| Respuesta del cliente | Temperatura asignada |
|---|---|
| "Lo necesito urgente" | 🔥 caliente |
| "En el próximo mes" | ☀️ tibio |
| "Solo estoy explorando" | 🧊 frío |

### Google Sheets — mapeo de columnas

| Columna en Sheet | Variable de Make |
|---|---|
| Fecha | `{{fecha}}` |
| Nombre | `{{nombre}}` |
| WhatsApp | `{{whatsapp}}` |
| Tipo de evento | `{{tipo}}` |
| Fuente | `{{fuente}}` |
| Estado | `{{estado}}` |
| Temperatura | `{{temperatura}}` |
| Seguimiento | `{{seguimiento}}` |

### Mensaje de notificación a Sandy (todos los leads)

```
🎉 *Nuevo lead — Casa Vita BranSan*
👤 Nombre: {{nombre}}
📱 WhatsApp: {{whatsapp}}
🎊 Evento: {{tipo}}
📅 Urgencia: {{seguimiento}}
🌡 Temperatura: {{temperatura}}
📍 Fuente: {{fuente}}
🕐 Fecha: {{fecha}}
```

### Mensaje de alerta urgente (solo leads calientes 🔥)

```
🔥 *LEAD URGENTE — Atender primero*
{{nombre}} necesita su evento en menos de 1 mes.
📱 WhatsApp directo: {{whatsapp}}
```

### Credenciales necesarias en Make

| Servicio | Dato requerido | Estado |
|---|---|---|
| Google Sheets | Cuenta Google conectada | ✅ |
| UltraMsg | Instance ID + Token | ⏳ Pendiente |
| Webhook Make | URL del webhook | ✅ |

---

## 🗂 Cómo agregar un nuevo cliente

### 1. Nombrar los archivos con prefijo único

```
[nombre-evento]-foto1.png
[nombre-evento]-foto2.png
...
```

Ejemplo para un evento "Sofia XV":
```
sofia-foto1.png
sofia-foto2.png
sofia-foto3.png
sofia-foto4.png
sofia-foto5.png
sofia-xv.html
```

### 2. Subir al repositorio

```bash
# Desde GitHub Desktop o la terminal
git add sofia-xv.html sofia-foto*.png
git commit -m "Agregar página XV años Sofía"
git push
```

Netlify despliega automáticamente en menos de 1 minuto.

### 3. Compartir el link con el cliente (boceto)

```
https://casavitabransan.netlify.app/sofia-xv
```

---

## 🔧 Stack técnico

| Capa | Herramienta |
|---|---|
| Frontend | HTML · CSS · JavaScript vanilla |
| Hosting | Netlify (deploy automático desde GitHub) |
| Repositorio | GitHub |
| Automatización | Make.com |
| Mensajería automática | UltraMsg (WhatsApp) |
| Base de datos de leads | Google Sheets |
| Formulario de cotización | Webhook Make.com |

---

## 📋 Checklist antes de entregar una página

### Datos
- [ ] Nombre(s) correctos en hero, footer y todas las secciones
- [ ] Fecha correcta en countdown y secciones del evento
- [ ] Horarios correctos en detalles e itinerario
- [ ] Direcciones reales con links de Google Maps actualizados
- [ ] CLABE / N.º de mesa de regalos correcto
- [ ] Número de WhatsApp correcto en RSVP y botones

### Fotos
- [ ] Nombres de archivo en el HTML coinciden con los subidos a GitHub
- [ ] Fotos en la raíz del repo (misma carpeta que el HTML)
- [ ] Prefijo único — no coincide con fotos de otros eventos

### Funcional
- [ ] Countdown apunta a la fecha y hora exacta del evento
- [ ] Botones de WhatsApp abren conversación correcta
- [ ] Links de Google Maps llevan al lugar correcto

### Visual y entrega
- [ ] Paleta de colores correcta según lo que pidió el cliente
- [ ] Revisado en móvil — se ve bien en pantalla pequeña
- [ ] Link enviado al cliente como boceto con marca de agua

---

## 📞 Contacto

**WhatsApp:** [wa.me/528126643281](https://wa.me/528126643281)
**Sitio:** [casavitabransan.netlify.app](https://casavitabransan.netlify.app)
**Instagram:** @casavitabransan

---

*Casa Vita BranSan · Monterrey, N.L. · 2025*
