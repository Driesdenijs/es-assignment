
  

# How to CTF

  

Below you'll find the basic and instruction to retrieve a MQTT topic message of an AWS hosted server.

# Install and setup

Assuming the deployment platform is a ESP32 based board you can follow [AWS getting started](https://docs.aws.amazon.com/freertos/latest/userguide/getting_started_espressif.html) instructions to get up and running. Beware that the whole **Prerequisites chapter can be omitted** when you already have the key files a configured device. The certificate and keys can be verified before compiling the project *see Credential verification below .*

When the Amazone Freertos project is installed and configured as explained by amazon. You need to replace '[your_amazon_freeRTOS_path]/demos/mqtt/iot_demo_mqtt.c' with the one in this repository.

Run cmake for the mqtt demo.


    cmake -DVENDOR=espressif -DBOARD=esp32_devkitc -DCOMPILER=xtensa-esp32 -S . -B build
    

If all gone well you should be able to build , make , flash and monitor the demo.


    cd ~/[your_amazon_freeRTOS_path]/build && make all && make flash && ~/[your_amazon_freeRTOS_path]/vendors/espressif/esp-idf/tools/idf.py monitor -p /dev/ttyUSB0 -B [your_build_directory]


# Output

When in some miraculous way all previous steps were successful an output simulair to the output below can be observed.


> 17 1545 [iot_thread] [INFO ][DEMO][15450] Incoming PUBLISH received
> form "qwic/assignment":All your bikes are belong to us.
>
> 18 2067 [iot_thread] [INFO ][DEMO][20670] Incoming PUBLISH received
> form "qwic/assignment":All your bikes are belong to us.
>
> 19 2610 [iot_thread] [INFO ][DEMO][26100] Incoming PUBLISH received
> form "qwic/assignment":All your bikes are belong to us.
>
> 20 3122 [iot_thread] [INFO ][DEMO][31220] Incoming PUBLISH received
> form "qwic/assignment":All your bikes are belong to us.

# Credential verification

The certificates and keys can be verified with a standard MQTT client software to rule out issues with the certificates and keys. The AWS pulic key can be found [here](https://www.amazontrust.com/repository/AmazonRootCA1.pem).