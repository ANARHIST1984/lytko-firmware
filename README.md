# Lytko Firmware Releases

Публичные релизы прошивок устройств Lytko.  
Исходный код закрыт. Только готовые бинарники для прошивки.

---

## Устройства

| Устройство | Чип | Описание |
|------------|-----|----------|
| [L100w-SCN](devices/L100w-SCN.md) | ESP32-C6 | WiFi термостат (MQTT, HomeKit, Алиса) |
| [krug](devices/krug.md) | ESP32-C3 | Круглый дисплей GC9A01 240×240 |

---

## Как прошить

### Через esptool (универсально)

```bash
pip install esptool

# L100w-SCN (ESP32-C6)
esptool.py --chip esp32c6 -p /dev/ttyUSB0 -b 460800 \
  write_flash 0x80000 L100w-SCN-2.1.0+3.bin

# krug (ESP32-C3)
esptool.py --chip esp32c3 -p /dev/ttyUSB0 -b 460800 \
  write_flash 0x380000 krug-1.0.1+1.bin
```

### Через ESP Flash Tool (Windows GUI)
Скачать: https://www.espressif.com/en/support/download/other-tools

---

## Скачать

Все версии: [Releases](../../releases)
