# Macropad

A wireless BLE keyboard the size of your hand for custom hotkeys.
<img width="2160" height="1082" alt="thumbnail (1)" src="https://github.com/user-attachments/assets/46accc81-fb6a-4021-981c-a8541892e624" />

This project was made for Hack Club as an affordable alternative to commercial Macropads. The Macropad uses the ESP32 core chip for latency-free Bluetooth transmission, taking sub 50ms. Features include key debouncing, a status LED indicator, a quick swap keybind changing tool, and an internal memory storage bank. Menu choices and key layouts can be configured easily using the desktop app.

## BOM

| Component | Description | Quantity | Approx Price (USD) |
| :--- | :--- | :--- | :--- |
| **ESP32 Dev Kit** | Microcontroller | 1 | $4.50 |
| **Tactile Buttons** | Tap input keys (any brand) | 3 | $0.30 |
| **Status LED** | Indication led for network states | 1 | $0.10 |
| **FR1 Copper Clad Sheet** | Base board for pcb | 1 | $1.00 |
| **Total Cost** | -- | -- | **~$5.90** |


---

## How it works

### 1. Keyboard Firmware
The ESP32 mimics a standard Bluetooth keyboard so your computer recognizes and trusts it. At the same time, it leaves a connection open for your Windows application to connect. This lets you rebind your gaming keys instantly without losing connection. Once sent, the new keys save directly to the onboard memory so they stick even after a reboot.

### 2. Desktop Firmware
Windows recognizes the Macropad as a standard USB device when it is plugged in. The desktop app connects directly to this active USB port and listens for the hardware footprint. Once selected, it streams your new keybind configuration data through the cable.

---

## Building & Compiling

### Arduino Firmware Setup
Ensure you have the `NimBLE-Arduino` package installed through your library manager. Compile and flash the script directly to your ESP32 board.

### Native Windows App Compilation
If you make modifications to the Python app script, re-bundle the project into an `.exe` using the system tool command:

```powershell
# Setup requirements
pip install bleak customtkinter pyinstaller

# Build into a executable
python -m PyInstaller --noconsole --onefile keybinds.py
```
Your compiled launcher will be placed cleanly inside the newly generated `/dist` directory.

# Final look
<img width="965" height="789" alt="IMG_8363" src="https://github.com/user-attachments/assets/4c676197-ef88-4cf1-b57f-2e2b32ab84c2" />
