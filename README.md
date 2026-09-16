# Goatted Controller

Aplicación nativa para macOS que permite controlar la cámara **DJI Osmo Pocket 3** en segundo plano mediante un control de **Xbox** o mando USB mediante protocolo UVC.

Desarrollado por **Goatted Labs**.

---

## 📸 Vista Previa
<img width="800" height="300" alt="GOATTED-SNAP" src="https://github.com/user-attachments/assets/e10cfcd1-c366-468d-b12d-cdd78bfdc66a" />

---

## 🚀 Descarga e Instalación

1. Ve a la sección de **[Releases]([https://www.google.com/search?q=../../releases](https://github.com/diegomndza/GOATTED-CONTROLLER/releases))** en la barra lateral derecha de este repositorio.
2. Descarga la versión más reciente (`Goatted-Controller-vX.0.x.zip`).
3. Descomprime el archivo y arrastra **Goatted Controller** a tu carpeta de **Aplicaciones**.

---

## ⚙️ Permisos Obligatorios (Monitoreo de Entrada)

Para que el control de Xbox funcione mientras, transmites o usas la aplicación minimizada, macOS exige otorgar permisos de acceso en segundo plano:

1. Abre **Ajustes del Sistema** en tu Mac.
2. Navega a **Privacidad y seguridad** > **Monitoreo de entrada**.
3. Haz clic en el botón **`+`** y selecciona **Goatted Controller**.
4. Activa el interruptor para confirmar.

---

## 🎮 Guía de Uso

* **Conexión de Cámara:** Conecta tu DJI Osmo Pocket 3 a la Mac por USB y confígurala en modo Webcam / UVC.
* **Conexión de Control:** Vincula tu control de Xbox por Bluetooth o cable USB.
* **Control PTZ:** Usa los sticks analógicos para realizar movimientos suaves de **Pan** (Giro horizontal), **Tilt** (Inclinación vertical) y **Zoom** continuo en tiempo real.
* **Soporte Segundo Plano:** Puedes minimizar la ventana o cambiar a otra app; los comandos del control seguirán respondiendo en todo momento.

---

### 1. Captura de Entradas y Mapeo Analógico

* La aplicación inicializa un bucle de eventos mediante `pygame.joystick` para leer los ejes del mando de Xbox a 60 Hz.
* Los valores analógicos del stick (rango `-1.0` a `1.0`) son procesados mediante una zona muerta (*deadzone*) para evitar derivas no deseadas (*stick drift*).

### 2. Control de Cámara UVC sin Bloqueo

* Para enviar comandos de movimiento a la DJI Osmo Pocket 3, la app ejecuta llamadas asíncronas hacia el ejecutable embebido `uvc-util`.
* Los comandos PTZ (Pan-Tilt-Zoom) se envían directamente a los endpoints de control del dispositivo UVC sin bloquear la interfaz.

### 3. Persistencia en Segundo Plano

* Integración con la librería `appnope` para solicitar al kernel de macOS la desactivación de la suspensión de energía por *App Nap*, permitiendo escuchar el control de Xbox en segundo plano.

---

## 🔮 Próximas Funciones (Roadmap)

* [ ] **Presets de Posición Guardados:** Guardar posiciones de cámara favoritas (ej. Presets A, B y C) y recuperarlas al presionar los botones del D-Pad.
* [ ] **Ajuste de Sensibilidad:** Interfaz para personalizar la zona muerta (*deadzone*) y la curva de respuesta analógica de los joysticks.
* [ ] **Soporte Multi-Cámara:** Selección y alternancia rápida entre múltiples dispositivos UVC conectados por USB.
* [ ] **Asignación Libre de Botones:** Mapeo personalizado para asignar funciones específicas a los botones del mando.
* [ ] **Barra de Menú (Menu Bar App):** Opción para ejecutar la aplicación en segundo plano exclusivamente desde la barra superior de macOS.

---

## 🛠️ Créditos y Proyectos de Terceros

Agradecimiento especial a los desarrolladores y comunidades de código abierto que hacen posible este proyecto:

* **[uvc-util](https://www.google.com/search?q=https://github.com/juju/uvc-util)** ([@juju](https://www.google.com/search?q=https://github.com/juju)) — Control de bajo nivel UVC/PTZ en macOS.
* **[appnope](https://github.com/minrk/appnope)** ([@minrk](https://www.google.com/search?q=https://github.com/minrk)) — Gestión de procesos en segundo plano y bypass de App Nap.
* **[Pygame](https://www.google.com/search?q=https://github.com/pygame/pygame)** ([@pygame](https://www.google.com/search?q=https://github.com/pygame)) — Lectura de eventos de entrada y compatibilidad con Gamepads.
* **[PyInstaller](https://www.google.com/search?q=https://github.com/pyinstaller/pyinstaller)** ([@pyinstaller](https://www.google.com/search?q=https://github.com/pyinstaller)) — Compilación y empaquetado del bundle ejecutable `.app`.
* **[Pillow](https://www.google.com/search?q=https://github.com/python-pillow/Pillow)** ([@python-pillow](https://www.google.com/search?q=https://github.com/python-pillow)) — Procesamiento y gestión de recursos de imagen.

---

## 📄 Licencia

Copyright © 2026 **Goatted Labs & Goatted Media**. Todos los derechos reservados.
