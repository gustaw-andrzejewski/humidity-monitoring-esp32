# Humidity Monitoring with ESP32 and DHT11

## About
This small project uses an **ESP32** and a **DHT11 sensor** to monitor temperature and humidity. The data is served via an HTTP endpoint.  
It's inspired by [this great tutorial](https://www.youtube.com/watch?v=_dRrarmQiAM) for Wi-Fi communication and extended to display sensor data using the [DHT ESP-IDF component](https://esp-idf-lib.readthedocs.io/en/latest/groups/dht.html).


---

## Wiring Instructions
To connect the DHT11 sensor with the ESP32:
- **VCC (DHT11)** -> **3.3V (ESP32)**  
- **GND (DHT11)** -> **GND (ESP32)**  
- **DATA (DHT11)** -> **GPIO16 (ESP32)**  
  *(You can change the GPIO pin in the code by modifying `DHT_GPIO_PIN`)*.

Optional: Connect the ESP32 to a power bank for portability.

---

## How to Run
1. **Set up ESP-IDF**:  
   Make sure you have ESP-IDF installed and configured. Refer to the [ESP-IDF Getting Started Guide](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html).

2. Clone the repository:
   ```bash
   git clone https://github.com/gustaw-andrzejewski/humidity-monitoring-esp32.git
   cd humidity-monitoring-esp32
   ```
3. Edit the WIFI configuration in the **main/humidity-check.c** file by changing the wifi details:
    ```c
    wifi_config_t wifi_config = {
            .sta = {
                .ssid = "YOUR_SSID",
                .password = "YOUR_PASSWORD",
    ```
4. Build and flash the project:
   ```bash
   idf.py build
   idf.py flash
   ```
5. Monitor the logs to find the ESP32's IP address:
   ```bash
   idf.py monitor
   ```
6. Open your browser and go to:
   ```
   http://<ESP32_IP>/humidity
   ```

For detailed setup instructions, see the [ESP-IDF Documentation](https://idf.espressif.com/).
