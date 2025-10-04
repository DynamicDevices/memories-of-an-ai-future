# EL133UF1 E-Ink Display Driver - Production System

## Status: PRODUCTION READY (Deployed at 62.3.79.162)

### Project Overview
Production-ready Linux driver for 13.3" color E-Ink display with PNG/JPEG support and autonomous slideshow.

### Key Features
- **Direct PNG/JPEG Loading**: No external conversion tools needed
- **Automatic Landscape Rotation**: Portrait (1200x1600) direct, landscape (1600x1200) auto-rotated
- **Advanced Stucki Dithering**: Photographic quality on 6-color e-ink
- **Production Demo System**: Autonomous slideshow with dynamic image detection
- **libgpiod v2.x Integration**: Modern GPIO control with hardware abstraction

### Hardware Configuration
- **Target**: imx93-jaguar-eink at 62.3.79.162
- **SPI**: /dev/spidev0.0
- **GPIO Pins**: Reset=526, DC=527, CS0=529, BUSY=528, CS1=619
- **Display**: 1200x1600 pixels, dual controller (600x1600 each), 6-color palette
- **User**: fio/fio with passwordless sudo

### Quick Deploy
```bash
# Production kiosk setup
sudo ./scripts/manage_slideshow_service.sh install

# Add images
scp *.png *.jpg fio@62.3.79.162:/home/fio/el133uf1_driver/demo_images/

# Manual display
sudo LD_LIBRARY_PATH=. ./el133uf1_demo image=file.png
```

### Technical Stack
- **Dependencies**: libgpiod v2.x, libpng16, libjpeg-turbo 3.0.1, libcurl, systemd
- **Build**: ARM64 cross-compilation with stub libraries
- **Architecture**: Dual controller optimization for EL133UF1

### Color Mapping
Black(0,0,0)→0x00, White(255,255,255)→0x11, Yellow(255,255,0)→0x22, Red(255,0,0)→0x33, Blue(0,0,255)→0x55, Green(0,255,0)→0x66

### Integration
- **E-Ink Ecosystem**: Display component with MCXC143VFM power controller
- **Linux BSP**: Deployed via meta-dynamicdevices Yocto layer
- **Performance**: ~37 seconds refresh, optimized for embedded constraints

---
**Repository**: `/data_drive/esl/eink-spectra6/`  
**Deployment**: Active production slideshow at 62.3.79.162