# Arduino RFID Authenticator (R4 WiFi + RC522)

This project is a simple RFID authentication system built using an **Arduino R4 WiFi**, an **RC522 RFID module**, and basic components the built-in LED matrix and a buzzer. It reads RFID card data and provides authentication feedback using a check-mark and success tones (if authorized) or an 'X' and error tones (if unauthorized).

## Hardware Used

- **Arduino R4 WiFi**
- **RC522 RFID Module**
- **Buzzer**
- **Jumper Wires & Breadboard**

## How It Works

When an RFID card is brought near the RC522 reader:

1. The card's UID (Unique Identifier) is read via the SPI protocol.
2. The UID is compared to a predefined `authorizedUID`.
3. Depending on the result:
   - ✅ If the UID matches:
     - LED Matrix will draw a check-mark
     - Buzzer plays two high-pitched success tones
   - ❌ If the UID doesn't match:
     - LED Matrix will draw an 'X'
     - Buzzer plays low-pitched error tones

## Pin Configuration

| Component  | Arduino Pin |
| ---------- | ----------- |
| RC522 SDA  | 10 (SS)     |
| RC522 RST  | 9           |
| RC522 MOSI | 11 (SPI)    |
| RC522 MISO | 12 (SPI)    |
| RC522 SCK  | 13 (SPI)    |
| Buzzer     | 5           |

## Code Summary

- **Authorized UID:**

  ```cpp
  byte authorizedUID[][4] = {
  {0xAA, 0x98, 0x85, 0xB1},
  {0xAA, 0xAA, 0xAA, 0xAA},
  {0xAA, 0xAA, 0xAA, 0xAA}
   };
  ```

  Change this array to match your desired RFID card's UID.

- **Authentication Functions:**
  - `checkUID()` — compares scanned UID with the authorized one.
  - `successAuth()` — lights LED matrix and beeps twice.
  - `failAuth()` — blinks LED matrix and beeps 3 times.

## Demo

### Sorry in advance, the wiring makes it difficult to see who's connected to what :/ 

### **New Version using built-in LED Matrix** 
![Image](IMG_Matrix.jpeg)

[▶️ Watch Demo Video](videoRFID_Matrix.mp4)

### **Old Version using Red and Green LEDs** 
![Image](IMG_5285.jpeg)

[▶️ Watch Demo Video](videoRFID.mp4)
