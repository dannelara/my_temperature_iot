# Tutorial for building a simple arduino based plant temperature, light and moisture sensor.

Yohalmo Daniel Martinez Lara - ym222cw

## Description

In this tutorial we will build a simple temperature communicator IOT device that will be reading the room temperature and save the data to MongoDB through our external api, which we will reach by connecting the IOT device to the wifi. The data will be presented with the help of our external API that will be saving and serving the data. In this case we will use our own created frontend with nextjs framework that will fetch and present the data saved to MongoDB.

Estimated time needed: 1-2h.

## Objective

The reason for this procject is becase we are a big family and we often use to much energy on heating our rooms. With this iot device we will be able to monitor the temperature of the main room in the house, so that we do not spend to much energy on heating it up.

The main purpose for this procject is to learn the basics of the world of IOT devices and how they can provide information from the real world. By creating this simple procject I believe that we will be able to gain some basic knowledge about the different workflows of IOT devices and the way we save / present the data by connecting the device to the internet.

When I complete the project I will be able to understand the different ways of reading live data, from IOT devices. In this case, we will read the temperature  of a room with the help of a temperature sensor. We will have created a self-sustained IOT device that will read information on a daily basis and save that data. With the way we save the data, we will be able to view the most recent data. Altought this project is simple, it gives the posibility to add extra features add further imporvements.

## Material
The required materials for the project are all included in the [Electrokit](http://www.electrokit.com) Arduino mkr1000 boundle. In this tutorial we will be using the mkr1010 wifi, but the provided mkr1000 will work aswell.

The folloing are the required materials for the project:
|Component|Store|Price| description|
|----|----|----|----|
|[Arduino boundle](https://www.electrokit.com/produkt/arduino-mkr-iot-bundle/)|Electrokit|995 SEK| Arduino boulde with all essential components.|
|Arduino mkr1000 or mkr1010|[Arduino boundle](https://www.electrokit.com/produkt/arduino-mkr-iot-bundle/)| Included | Board with wifi capabilities. Li-Po Single Cell, 3.7V, 1024mAh compatible. Programmable with c++|
|TMP36 temperature sensor|[Arduino boundle](https://www.electrokit.com/produkt/arduino-mkr-iot-bundle/)| Included | Sensor for reading temperature from the plant.|
|Breadboard|[Arduino boundle](https://www.electrokit.com/produkt/arduino-mkr-iot-bundle/)| Included | Solderless base for board and sensors.|
|USB-cable|[Arduino boundle](https://www.electrokit.com/produkt/arduino-mkr-iot-bundle/)| Included | Cable to connect board to computer or for charging.|
|[3,7 V - Li-Po battery](https://www.kjell.com/se/produkter/el-verktyg/arduino/arduino-tillbehor/luxorparts-li-po-batteri-37-v-med-kontakt-1200-mah-p87924?gclid=CjwKCAjw4ayUBhA4EiwATWyBrgnLGLbsof9aGo4WD07YLEEVemxWHd9v1mQaABOOYs8kAGj06HmD_RoCZegQAvD_BwE&gclsrc=aw.ds)|https://www.kjell.com/|99.90 SEK| Battery for the board. This is optional but recommended if the device will be outside.|

Total cost: 1095.90 (including the Li-Po battery).

mkr1010 board:
``This board is powerful enough for the project and has all necessary capabilities in order to complete the project.``

![mkr1010](https://docs.arduino.cc/static/df779d958c386826c73e149e42e28918/image.svg)


## Computer setup

Required software:

- Arduino IDE - For easier dependency management.
- C++ - Required for Arduino borad (included in the Arduino IDE)
- OS - Windows 11 or other popular OS.

<br>
<br>
The chosen IDE is Arduinos own IDE for development of arduino boards. This IDE includes all dependencies needed in order to compile C++ code and flash the Arduino board. So there won't really be any need to install other software for flashing or uploading the code.
<br>
<br>
The first step in the process is to install the IDE from Arduino. This will be used to flash the board and controll dependecies like external libraries.
<br>
<br>
Follow the following link in order to install the correct IDE: [Arduino IDE - istall guide](https://www.arduino.cc/en/software)
<br>
<br>
After successfully installing the IDE we need to install the SAMD CORE. This is done by opening the Arduino IDE and following these steps:

`Tools > Board > Board Manager > search for "samd" > install Arduino SAMD Boards (32-bits ARM Cortex-M0+) `
![mkr1010](https://docs.arduino.cc/static/ef60fa2f6bb1716e3c8f7222cbf01cee/29114/install_samd21_img03.png)
<br>
<br>
<br>
We are now ready to select the board that we will be working with.
Follow the next steps to set the board:

`Tools > Board > Arduino SAMD Boards (32-bits ARM Cortex-M0+) > Select "Arduino mkr1000`
![mkr1010](https://docs.arduino.cc/static/89b34d9b99279a53f182ea1fff0dce99/29114/install_samd21_img04.png)
<br>
<br>
<br>
Now we are ready to connect our board to the IDE! Start by connecting the USB to your computer and board.
In order for the IDE to find a board on a given port, we will need to select a board connected to a specific port.

`Tools > Port > Select the available board connected to a port.`
![mkr1010](https://docs.arduino.cc/static/0528a7a964b5c34564b6e79215b049d1/29114/install_samd21_img05.png)
<br>
<br>
<br>
We now have a board connected to the IDE and we are ready to upload our code!

`Arduino IDE provides a simple way of flashing and oploading a new sketch to the board:`
![upload_sketch](https://docs.arduino.cc/static/7eb8025389fd6baaafc5ff1537ebbe58/29114/install_samd21_img07.png)

`Note! The previous mentioned software and instructions are specific to windows 11 users, however these instructions and software should be suported by most popular OS but may look a bit different, depending on your OS. Just follow the provided links and you'll find the correct instructions for your OS.`
<br>
<br>
<br>




### Optional

If you've bought the battery, make sure to connect it to the boards JST connector. You will have to let the board stay connected to the USB as the battery needs to be charged. When you are ready for the IOT device to sustain it self on the battery, make sure to flash the board and load the new sketch (code) and remove the USB. It will then start using the battery.

The following diagram demonstrates how the Li-Po battery should be connected to the board.
![battery](https://www.arduino.cc/wiki/static/5fa079e468846a06c1717e6aaae3e828/5a190/mkr_tutorial_01_img_01_rev2.png)