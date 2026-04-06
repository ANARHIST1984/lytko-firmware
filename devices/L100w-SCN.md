# L100w-SCN — WiFi термостат

## Описание

Прошивка для термостата на базе ESP32-C6.  
Управление нагревом, WiFi, облачные протоколы.

## Характеристики

| Параметр | Значение |
|----------|----------|
| Чип | ESP32-C6 |
| IDF | 5.5.3 |
| Flash | 4 MB |
| Протоколы | MQTT, Apple HomeKit, Яндекс Алиса |
| Диапазон уставки | 15–40 °C |
| Связь с экраном | UART (DWIN-протокол) |

## Адреса прошивки

| Файл | Адрес |
|------|-------|
| bootloader.bin | 0x0 |
| partition-table.bin | 0x8000 |
| ota_data_initial.bin | 0xC000 |
| L100w-SCN-x.x.x+N.bin | 0x80000 |

## Полная прошивка (первый раз)

```bash
esptool.py --chip esp32c6 -p PORT -b 460800 \
  --before default_reset --after hard_reset \
  write_flash --flash_mode dio --flash_size 4MB --flash_freq 80m \
  0x0      bootloader.bin \
  0x8000   partition-table.bin \
  0xc000   ota_data_initial.bin \
  0x80000  L100w-SCN-x.x.x+N.bin
```

## Обновление (только приложение)

```bash
esptool.py --chip esp32c6 -p PORT -b 460800 \
  write_flash 0x80000 L100w-SCN-x.x.x+N.bin
```
