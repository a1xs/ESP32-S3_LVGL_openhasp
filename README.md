# ESP32-S3_LVGL_openhasp
Touch panel ESP32-S3 for HomeAssistant

1. Прошить образ esp32-s3-4848S040_full_16MB_v0.7.0-rc9.bin утилитой flash_download_tool
2. Настроить WIFI подключившись к панели (по умолчанию адрес панели 192.168.4.1)
3. В Configuration -> GPIO Settings Настроить выходы реле (Add New Pin Output) Где первое реле = 40 pin, Второе = 2 pin, Третье = 1 pin
4. Настроить MQTT Settings
5. в меню File editor загрузить картинки и файлы команд с папки "Загрузить в FILE EDITOR" (upload)
6. Открыть в File Editor {}pages.jsonl и заменить весь код на содержимое файла "pages_480x480.jsonl"
7. Установить в интеграции HACS -> openHASP-custom-component. При установке включите "отображать бэта версии" и установите пакет с номером большим 0.7.0. Версии 0.6.х не совместимы с прошивкой.
8. загрузить в Home Assistant файл openhasp_homekit.yaml в ту же папку где находиться configuration.yaml. В openhasp_homekit.yaml заменить все plate04 на свое название из MQTT settings -> Hostname
9. В configuration.yaml добавить:
   homeassistant:
```
packages:
  openhasp_homekit: !include openhasp_homekit.yaml
```
в моем случае так как все ямлы хранятся в каталоге packages:
```
homeassistant:
 packages: !include_dir_named packages
```

<img width="482" height="483" alt="изображение" src="https://github.com/user-attachments/assets/8cfd7161-b599-4083-a9ff-8208c3157b9c" />
<img width="480" height="470" alt="изображение" src="https://github.com/user-attachments/assets/b48becdc-813d-458a-8e53-2629d318d942" />
<img width="479" height="475" alt="изображение" src="https://github.com/user-attachments/assets/0d29e8f0-42e4-4b26-ba2f-ced084106228" />
<img width="479" height="476" alt="изображение" src="https://github.com/user-attachments/assets/e93408d6-e73a-4469-9d6b-d12dead10010" />


