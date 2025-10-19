
# QR Code Generator | Kawdhitha Nirmal

<div align="center">

![QR Code Generator](http://kawwa.pages.dev/Tgs/qrcodelogo.png)

**Advanced QR Code Generator with Custom Logos, Shapes, and Styles**

[![Live Demo](https://img.shields.io/badge/Live_Demo-Visit_Now-00C853?style=flat&logo=vercel)](https://qr.kawwa.site)
[![API Documentation](https://img.shields.io/badge/API-Documentation-2962FF?style=flat&logo=readme)](#api-documentation)
[![Features](https://img.shields.io/badge/View-Features-FF6F00?style=flat&logo=featureflow)](#features)
[![Installation](https://img.shields.io/badge/Setup-Installation-9C27B0?style=flat&logo=npm)](#installation)


</div>

---

## Overview

QR Code Generator is a modern, feature-rich web application built with Next.js that allows you to create customized QR codes with advanced styling options, custom logos, and multiple error correction levels. Perfect for marketing campaigns, product packaging, and digital content sharing.

**Built by:** [Kawdhitha Nirmal](https://whatsapp.com/channel/0029VatTpZU7oQhkw1WbZS0B) | CodeXDeveloper

---

## Features

### Core Features
- ✨ **Real-time QR Code Generation** - Instant preview as you customize
- 🎨 **Custom Styling** - Choose from multiple dot shapes and corner styles
- 🖼️ **Logo Support** - Add custom logos to the center of QR codes
- 🎯 **Error Correction Levels** - Easy, Medium, and Hard (default: Easy)
- 📱 **Responsive Design** - Works seamlessly on desktop and mobile
- 🌐 **Glassmorphism UI** - Modern, elegant interface with liquid glass effects

### QR Customization
- **Dot Shapes**: Square, Circle, Rounded, Diamond
- **Corner Styles**: Square, Rounded, Circle
- **Color Control**: Custom QR code and background colors
- **Size Options**: Adjustable QR code dimensions
- **Logo Sizing**: Control logo proportion in QR code

### API Features
- 🚀 **RESTful API** - Generate QR codes programmatically
- 📊 **Multiple Formats** - Support for URLs, emails, phone numbers, WiFi
- 🔗 **Shareable Links** - Generate and share QR code configurations
- 📥 **Logo Upload** - Add logos via URL parameter
- 💾 **Direct Image Output** - Returns PNG images directly

---


## Usage

### Web Interface

1. **Enter Content**: Type or paste your URL, email, phone number, or text
2. **Customize**: Select dot shapes, corner styles, colors, and error level
3. **Add Logo** (Optional): Upload a logo to display in the center
4. **Generate**: Click "Generate QR Code"
5. **Download**: Save the QR code as PNG
6. **Share**: Copy the shareable link to recreate the same QR code

### API Usage

#### Basic QR Code Generation

# Simple text QR code
```
curl "https://qr.kawwa.site/api/generate-qr?data=Hello%20World"
```

# URL QR code
```
curl "https://qr.kawwa.site/api/generate-qr?data=https://example.com"
```

#### With Custom Logo


# QR code with logo
```
curl "https://qr.kawwa.site/api/generate-qr?data=https://example.com&logo=https://example.com/logo.png"

```


#### With Error Correction Level


# Easy error correction (default)
```
curl "https://qr.kawwa.site/api/generate-qr?data=text&errorLevel=easy"
```

# Medium error correction
```
curl "https://qr.kawwa.site/api/generate-qr?data=text&errorLevel=medium"
```

# Hard error correction
```
curl "https://qr.kawwa.site/api/generate-qr?data=text&errorLevel=hard"
```


#### With Dot and Corner Shapes

# Custom shapes
```
curl "https://qr.kawwa.site/api/generate-qr?data=text&dotShape=circle&cornerShape=rounded"
```

#### Complete Example
```
curl "https://qr.kawwa.site/api/generate-qr?data=https://example.com&logo=https://example.com/logo.png&errorLevel=medium&dotShape=circle&cornerShape=rounded"
```

---

## API Documentation

### Endpoint

```
GET /api/generate-qr
POST /api/generate-qr
```

### Query Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `data` | string | required | Content to encode (URL, email, phone, text) |
| `logo` | string | optional | URL to logo image to overlay on QR code |
| `errorLevel` | string | `easy` | Error correction level: `easy`, `medium`, `hard` |
| `dotShape` | string | `square` | QR dot shape: `square`, `circle`, `rounded`, `diamond` |
| `cornerShape` | string | `square` | Corner marker shape: `square`, `rounded`, `circle` |
| `size` | number | `300` | QR code size in pixels (100-1000) |
| `margin` | number | `10` | Margin around QR code in pixels |
| `darkColor` | string | `#000000` | QR code color (hex format) |
| `lightColor` | string | `#ffffff` | Background color (hex format) |

### Response

- **Content-Type**: `image/png`
- **Body**: PNG image of the generated QR code

### Error Correction Levels

| Level | Recovery | Use Case |
|-------|----------|----------|
| **Easy** | ~7% | General use, clean environments |
| **Medium** | ~15% | Standard use, some potential damage |
| **Hard** | ~30% | Harsh environments, high durability needed |

### JavaScript Example

#javascript
// Generate QR code
```
const qrUrl = 'https://qr.kawwa.site/api/generate-qr?data=https://example.com&errorLevel=medium';
```

// Display in image tag
const img = document.createElement('img');
img.src = qrUrl;
document.body.appendChild(img);

// Download QR code
const link = document.createElement('a');
link.href = qrUrl;
link.download = 'qrcode.png';
link.click();
\`\`\`

### cURL Example


# Generate and save QR code
```
curl "https://qr.kawwa.site/api/generate-qr?data=https://example.com" -o qrcode.png
```

# With logo
```
curl "https://qr.kawwa.site/api/generate-qr?data=https://example.com&logo=https://example.com/logo.png" -o qrcode-with-logo.png
```

### Python Example
```
python
import requests
from PIL import Image
from io import BytesIO

# Generate QR code
url = 'https://qr.kawwa.site/api/generate-qr'
params = {
    'data': 'https://example.com',
    'errorLevel': 'medium',
    'dotShape': 'circle'
}

response = requests.get(url, params=params)
img = Image.open(BytesIO(response.content))
img.save('qrcode.png')
```

---

## Shareable Links

After generating a QR code, you can share the configuration using the shareable link format:

```
https://qr.kawwa.site?data=https://example.com&errorLevel=medium&dotShape=circle
```

This link will recreate the exact same QR code when opened in the application.

---

## Technology Stack

- **Frontend**: Next.js 15, React 19, TypeScript
- **Styling**: Tailwind CSS v4, Glassmorphism effects
- **QR Generation**: qrcode library
- **Image Processing**: Sharp
- **UI Components**: Radix UI, shadcn/ui
- **Deployment**: Vercel

---

## Project Structure

```
qr-code-generator/
├── app/
│   ├── api/
│   │   └── generate-qr/
│   │       └── route.ts          # QR generation API endpoint
│   ├── docs/
│   │   └── page.tsx              # API documentation page
│   ├── layout.tsx                # Root layout with meta tags
│   ├── page.tsx                  # Home page
│   └── globals.css               # Global styles
├── components/
│   ├── qr-generator.tsx          # Main QR generator component
│   └── ui/                       # shadcn/ui components
├── public/
│   ├── favicon.ico               # Favicon
│   └── qr-dot-shapes/            # QR dot shape examples
├── lib/
│   └── utils.ts                  # Utility functions
├── package.json
├── tsconfig.json
└── README.md
```

---

## Features in Detail

### QR Dot Shapes

Choose from 4 different dot shape styles:

- **Square**: Classic QR code appearance
- **Circle**: Modern, rounded dots
- **Rounded**: Slightly rounded square dots
- **Diamond**: Diamond-shaped dots for unique look

### Corner Styles

Customize the position markers (corners) of your QR code:

- **Square**: Traditional square corners
- **Rounded**: Rounded square corners
- **Circle**: Circular corner markers

### Error Correction

QR codes can recover from damage:

- **Easy (7%)**: Suitable for clean, protected environments
- **Medium (15%)**: Standard choice for most applications
- **Hard (30%)**: For outdoor or high-wear environments

---

## License

This project is open source and available under the MIT License.

---

## Support

For support, questions, or feedback:

- **WhatsApp Channel**: [Join our community](https://whatsapp.com/channel/0029VatTpZU7oQhkw1WbZS0B)
- **GitHub Issues**: [Report bugs or request features](https://github.com/kawdhitha/qr-code-generator/issues)
- **Email**: [codexsldev@gmail.com](mail-too:codexsldev.@gmail.com)

---

## Author

**Kawdhitha Nirmal** | CodeXDeveloper

<a href="https://dev.sapelaweddo.site" target="_blank"><img src="https://img.icons8.com/fluency/48/web.png" alt="Website"/></a>
<a href="mailto:codexsldev@gmail.com" target="_blank"><img src="https://img.icons8.com/fluency/48/000000/mail.png" alt="Email"/></a>
<a href="https://t.me/Codex_dev" target="_blank"><img src="https://img.icons8.com/fluency/48/000000/telegram-app.png" alt="Telegram"/></a>
<a href="https://github.com/KAWDHITHA-NIRMAL" target="_blank"><img src="https://img.icons8.com/fluency/48/000000/github.png" alt="GitHub"/></a>

---

<div align="center">
QR Code Studio • Build with ❤️ by Kawdhitha Nirmal
</div>

<div align="center">
<div style="display: flex; flex-wrap: wrap; justify-content: center; gap: 10px;">
  <a href="https://whatsapp.com/channel/0029VatTpZU7oQhkw1WbZS0B" target="_blank"><img src="https://social-card.kawwa.site/api?channellink=https%3A%2F%2Fwhatsapp.com%2Fchannel%2F0029VatTpZU7oQhkw1WbZS0B&theme=dark&overrideVerified=true&overrideVerifiedIcon=https%3A%2F%2Fstatic.whatsapp.net%2Frsrc.php%2Fv4%2FyM%2Fr%2FSGDtYg_EYce.png" alt="CodeX Developers" style="width: 300px; max-width: 100%; height: auto;" /></a>
  <a href="https://t.me/codex_developer" target="_blank"><img src="https://social-card.kawwa.site/api/telegram?username=codex_developer&theme=dark&overrideVerified=true&overrideVerifiedIcon=https%3A%2F%2Fstatic.whatsapp.net%2Frsrc.php%2Fv4%2FyM%2Fr%2FSGDtYg_EYce.png" alt="CodeX Developers tg" style="width: 300px; max-width: 100%; height: auto;" /></a>
</div>
</div>
