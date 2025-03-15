# ⌨️ Code Typer Simulator

_Simulador de escritura de código con efectos visuales profesionales_

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-lightgrey)](https://github.com/tuusuario/code-typer)

Un simulador de escritura de código interactivo que crea el efecto de que el código se escribe a máxima velocidad con cada pulsación de teclas. ¡Perfecto para demostraciones y screencasts profesionales!

## 🌟 Características Principales

- 🚀 **Efecto de typing ultra rápido** controlado por pulsaciones
- 💻 **Multiplataforma** (Windows/Linux/macOS)
- 🛑 **Interrupción elegante** con `Ctrl+C`
- 🎨 **Colores estilo hacker** con soporte ANSI
- 📁 **Carga código desde archivos externos** (`codigo.txt`)
- 🔒 **Manejo seguro del terminal** (modo raw profesional)
- 📦 **0 dependencias externas** (solo librerías estándar)
- ⚡ **Optimizado para rendimiento**

## 🛠️ Instalación

1. **Clona el repositorio:**
```bash
git clone https://github.com/tuusuario/code-typer.git
cd code-typer
```

2. **Instala las dependencias:**
```bash
pip install -r requirements.txt
```

## 🚀 Uso Básico

1. **Prepara tu código:**
   - Crea un archivo `codigo.txt` con el código a mostrar
   - Mantén la indentación y formato deseado

2. **Ejecuta el simulador:**
```bash
python code_typer.py
```

3. **Controla la ejecución:**
   - Presiona cualquier tecla para escribir código
   - `Ctrl+C` para salir en cualquier momento

## 🎨 Personalización

### Configuración del color
Modifica los colores editando las constantes de `colorama`:
```python
# Ejemplo: Cambiar a tema azul
sys.stdout.write(Fore.BLUE)
```

### Velocidad de typing (modo avanzado)
Ajusta el archivo `config.json`:
```json
{
  "typing_delay": 0.01,
  "color_theme": "cyber_green"
}
```

## 📂 Estructura del Proyecto
```
code-typer/
├── code_typer.py    # Script principal
├── codigo.txt       # Código de ejemplo
├── requirements.txt # Dependencias
├── LICENSE
└── README.md
```

## 🌐 Ejemplo de Uso
```bash
# 1. Clona el proyecto
# 2. Edita codigo.txt con tu código
echo "print('¡Hola Mundo! 🚀')" > codigo.txt

# 3. Ejecuta con efectos profesionales
python code_typer.py
```

## 📜 Licencia
Distribuido bajo licencia MIT. Ver [LICENSE](LICENSE) para más detalles.
