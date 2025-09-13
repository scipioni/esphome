# ESPHome Project

## Initial Flash via Serial Port

For the first-time compilation and flashing, connect the device via USB and use the serial port.

### Prerequisites
- Ensure Docker is installed and running.
- Connect the ESP device to the serial port (e.g., `/dev/ttyUSB0`).

### Steps

1. Set environment variables:
   ```bash
   export CONFIG=solarled
   export PORT=/dev/ttyUSB0  # Adjust to your serial port
   ```

2. Compile and flash:
   ```bash
   task flash

   or 

   docker compose -f docker-compose-usb.yml run --rm esphome run $CONFIG.yaml --device $PORT
   ```

## OTA Updates

Once the device is flashed and accessible on the network, use OTA for subsequent updates.

### Option 1: Using Docker Compose

1. Set environment variables:
   ```bash
   export CONFIG=solarled
   export IP=192.168.2.60  # Replace with your device's IP address
   ```

2. Update via OTA:
   ```bash
   task flash:ota

   or

   docker compose run --rm esphome run projects/$CONFIG.yaml --device $IP
   ```

### Option 2: Using Taskfile

Run the OTA flash task directly:
```bash
CONFIG=solarled IP=192.168.2.60 task flash:ota  # Replace IP with your device's IP address
```

### Notes
- The configuration file is located at `projects/solarled.yaml`.
- Ensure the device is on the same network and the IP is correct.
- For other configurations, update the `CONFIG` variable accordingly.