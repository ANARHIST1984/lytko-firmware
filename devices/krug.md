# krug — круглый дисплей

## Описание

Прошивка для круглого дисплея GC9A01 на базе ESP32-C3.  
UI на LVGL, связь с термостатом через UART (DWIN-протокол).

## Характеристики

| Параметр | Значение |
|----------|----------|
| Чип | ESP32-C3 |
| IDF | 5.3.2 |
| Flash | 4 MB |
| Дисплей | GC9A01 240×240 |
| UI | LVGL |
| Связь | UART (DWIN-протокол) с L100w-SCN |

## Адреса прошивки

| Файл | Адрес |
|------|-------|
| bootloader.bin | 0x0 |
| partition-table.bin | 0x8000 |
| ota_data_initial.bin | 0xC000 |
| krug-x.x.x+N.bin | 0x380000 |

## Полная прошивка (первый раз)

```bash
esptool.py --chip esp32c3 -p PORT -b 460800 \
  --before default_reset --after hard_reset --no-stub \
  write_flash --flash_mode dio --flash_size 4MB --flash_freq 80m \
  0x0      bootloader.bin \
  0x8000   partition-table.bin \
  0xc000   ota_data_initial.bin \
  0x380000 krug-x.x.x+N.bin
```

## Обновление (только приложение)

```bash
esptool.py --chip esp32c3 -p PORT -b 460800 --no-stub \
  write_flash 0x380000 krug-x.x.x+N.bin
```
