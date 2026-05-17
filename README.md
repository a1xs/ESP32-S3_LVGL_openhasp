# ESP32-S3_LVGL_openhasp
Touch panel ESP32-S3 for HomeAssistant

1. Прошить образ esp32-s3-4848S040_full_16MB_v0.7.0-rc9.bin утилитой flash_download_tool
   Для этого подключаемся по usb к компьютеру и запускаем программу flash_download_tool. В ней Выбираем так как показано на скрине и собственно загружаем прошивку:
   
   <img width="427" height="672" alt="изображение" src="https://github.com/user-attachments/assets/09792c06-0755-4f9e-b41e-6a1e10a0406f" />

3. Настроить WIFI подключившись к панели (найти в dhcp)
   <img width="623" height="414" alt="изображение" src="https://github.com/user-attachments/assets/386c7583-fe8a-4036-9d67-517c97a16422" />

4. В Configuration -> GPIO Settings Настроить выходы реле (Add New Pin Output) Где первое реле = 40 pin, Второе = 2 pin, Третье = 1 pin
   <img width="696" height="414" alt="изображение" src="https://github.com/user-attachments/assets/924f994e-4a28-4973-8c7a-bee61649d360" />

5. Настроить MQTT Settings (Настройки- Приложения - Mosquitto broker)
   <img width="844" height="243" alt="изображение" src="https://github.com/user-attachments/assets/9b924821-23c8-4c21-8625-1a53bdfa7678" />
   
6. в меню File editor загрузить картинки и файлы команд с папки "Upload to FILE EDITOR" (upload)
   <img width="659" height="378" alt="изображение" src="https://github.com/user-attachments/assets/7e2c76e1-0a3c-40b4-95ec-ecc6144d1050" />

7. Открыть в File Editor {}pages.jsonl и заменить весь код на содержимое файла "pages_480x480.jsonl"
8. Установить в интеграции HACS -> openHASP-custom-component. При установке включите "отображать бэта версии" и установите пакет с номером большим 0.7.9. 
9. Загрузить в Home Assistant файл openhasp_homekit.yaml в ту же папку где находиться configuration.yaml или как у меня в packages. В openhasp_homekit.yaml заменить все plate04 на свое название из MQTT settings -> Hostname
10. В configuration.yaml добавить:
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


