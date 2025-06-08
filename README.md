# esphome

first flash and compile with serial port
```
CONFIG=solarled
PORT=/dev/ttyUSB0

docker compose -f docker-compose-usb.yml  run --rm esphome run $CONFIG.yaml --device $PORT 
```

ota 
```
export CONFIG=solarled
export IP=192.168.2.60

docker compose run --rm esphome run $CONFIG.yaml --device $IP

# or
CONFIG=solarled IP=192.168.2.60 task flash:ota
```