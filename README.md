

# Security sytem for cash transit

![LOGO](https://imgtr.ee/images/2023/03/24/9lVSQ.jpg)

Our project aims to design a secure device that enables the transportation of cash from the institution to the bank, while integrating GPS technology to track the movement of cash in real-time. We also aim to develop a system for remote monitoring and control of cash transportation to improve security and reduce the risk of theft. Additionally, we will introduce a hard box for secure and easy transport of money.

Project Objectives

1. To design a secure device that enables the transportation of cash from the
institution to the bank, ensuring the safety of the money throughout the
journey.

2. To integrate GPS technology with the device to track the movement of the
cash in real-time and provide a live feed to the institution's observers.

3. To develop a system that enables the institution to monitor and control the
transportation of cash remotely through the internet.
4. To Improve the security of cash transactions and work to reduce the risk
of theft.

5. To Introduce a hard box that can provide security for money and is easy to
transport.



## Installation

### To install XAMPP on your computer

```bash
Go to the official XAMPP website (https://www.apachefriends.org/index.html) and download the version that is compatible with your operating system.

Once the download is complete, open the installer file and follow the instructions provided by the installer.

Select the components you want to install. For example, you can choose to install Apache, MySQL, PHP, and phpMyAdmin.

Choose the installation folder for XAMPP. The default folder is usually "C:\xampp" for Windows and "/Applications/XAMPP" for macOS.

During the installation process, you may be asked to set up a password for the MySQL root user. Make sure to choose a strong password and keep it safe.

Once the installation is complete, you can launch XAMPP by clicking on the XAMPP icon in your Start menu or Applications folder.

In XAMPP, you can start and stop the Apache and MySQL servers, and manage your databases using phpMyAdmin.

```
### To install Arduino IDE and install ESP32

```bash
Go to the official Arduino website (https://www.arduino.cc/en/software) and download the latest version of the Arduino IDE that is compatible with your operating system.

Once the download is complete, open the installer file and follow the instructions provided by the installer.

Launch the Arduino IDE and click on the "File" menu, then select "Preferences".

In the "Additional Boards Manager URLs" field, paste the following URL: https://dl.espressif.com/dl/package_esp32_index.json

Click "OK" to close the Preferences window.

Next, go to the "Tools" menu, then select "Board" > "Boards Manager".

In the "Boards Manager" window, search for "esp32" and select the "ESP32 by Espressif Systems" package.

Click on "Install" to install the ESP32 package.

Once the installation is complete, you can select the ESP32 board from the "Tools" menu > "Board" > "ESP32 Dev Module".

You're now ready to program your ESP32 board using the Arduino IDE.

```
### Arduino Libraries
```bash

#include <Arduino_JSON.h>
https://github.com/arduino-libraries/Arduino_JSON.git
#include <SPI.h>
https://github.com/PaulStoffregen/SPI.git
#include <MFRC522.h>
https://github.com/miguelbalboa/rfid.git
#include <AsyncTCP.h>
https://github.com/me-no-dev/AsyncTCP.git
#include <ESPAsyncWebServer.h>
https://github.com/me-no-dev/ESPAsyncWebServer.git
#include <WebSerial.h>
https://github.com/ayushsharma82/WebSerial.git
#include <WiFi.h>
https://github.com/espressif/arduino-esp32/blob/master/libraries/WiFi/src/WiFi.h
#include <HTTPClient.h>
https://github.com/espressif/arduino-esp32/blob/master/libraries/HTTPClient/src/HTTPClient.h


```
### Create google maps API key

``` bash
Go to the Google Cloud Console at https://console.cloud.google.com/ and sign in with your Google account.

If you don't already have a project, create one by clicking on the "Select a project" dropdown at the top of the page and then clicking on the "New Project" button.

Give your project a name and click "Create".

Once your project is created, go to the "APIs & Services" dashboard by clicking on the hamburger menu in the top-left corner and then clicking on "APIs & Services".

Click on the "Credentials" tab in the left-hand menu.

Click on the "Create credentials" button and select "API key".

Your API key will be displayed on the screen. You can restrict the usage of your API key by clicking on the "Restrict key" button and specifying the IP addresses or HTTP referrers that are allowed to use it.

Once you have created your API key, copy it and use it in your Google Maps application.
```

### Deskop installation

```bash
Go to the GitHub website and search for the repository that contains the PHP web app and Arduino IDE program code.

Once you find the repository, click on the "Code" button and select "Download ZIP" to download the files.

Extract the downloaded ZIP file to a folder on your computer.

Copy the main project folder, which should be named "smartcashcarrier" in this case.

Open the XAMPP installation folder, go to the "htdocs" subfolder, and paste the "smartcashcarrier" folder there.

Next, open a web browser and go to the URL "http://localhost/phpmyadmin/" to access the phpMyAdmin dashboard.

Click on the "Database" tab and create a new database named "smartcashcarrier".

In the "Import" tab, click on "Choose File" and select the "database.sql" file located inside the "smartcashcarrier" folder.

Click on the "Go" button to import the database schema and data.

Open a web browser and go to the URL "http://localhost/smartcashcarrier/" to access the web app.

Enter the default admin credentials provided (email: admin@gmail.com, password: 123) to log in to the system.

```
### To use localhost for database connection
```bash
Open your PHP code editor or IDE, and locate the PHP file where you want to connect to your database.

Copy the following code to your PHP file to connect to the database:
/* Database connection settings */
	$servername = "localhost";
    $username = "root";		//put your phpmyadmin username.(default is "root")
    $password = "";			//if your phpmyadmin has a password put it here.(default is "root")
    $dbname = "database";
    
```
### Firmware Changes
``` bash
//WIFI Credintial and RFID Device token
const char* ssid = "WIFI SSID";
const char* password = "Password";
const char* device_token  = "You can get it from web page";
//************************************************************************

// Send Data and Get data information can include computer IP or the server domain.
String IRURL = "http://YourIPAddress/smartcashcarrier/updateDHT11data_and_recordtable.php";
String UIDURL = "http://YourIPAddress/smartcashcarrier/getdata.php";
String LEDURL = "http://YourIPAddress/smartcashcarrier/getdatamain.php";
const char* SERVER_NAME = "http://YourIPAddress/smartcashcarrier/gpsdata.php";
String ESP32_API_KEY = "Ad5F10jkBM0";

```

## Requirements  

Required components:

```bash

+--------------------+---------------------------+-------------------+
|  Component name    |         Data Pins         | Power consumption |
+--------------------+---------------------------+-------------------+
| 15V and 2A Relay   | 2 GPIO Pins               | 5V and 60mA       |
| GPS Module         | 2 GPIO Pins (UART)        | 3.3V and 20mA     |
| RFID Module        | 5 GPIO Pins (SPI)         | 3.3V and 40mA     |
| Buzzer             | 1 GPIO Pin (Digital)      | 3.3V and >20mA    |
| Two LEDs           | 2 GPIO Pin (Digital)      | 1.8V and >20mA    |
| IR Sensor          | 1 GPIO Pin (Digital)      | 1.8V and 20mA     |
| GSM Module         | 2 GPIO Pins (UART)        | 3.3V and 20mA     |
| Solenoid lock      |                           |                   |
| Relay Module Pins  | 12V and 600mA(continuous) |                   |
+--------------------+---------------------------+-------------------+

```
Then I selected ESP32 development board for this requirement fulfill.

``` bash

+-----+------------------------+-------------------+---------------------+
| Pin | Communication Protocol | Power Consumption |      Function       |
+-----+------------------------+-------------------+---------------------+
|   0 | UART (TX)              | Low Power         | GPIO36              |
|   1 | UART (RX)              | Low Power         | GPIO37              |
|   2 | RST                    | Low Power         | GPIO05              |
|   3 | LED01                  | Low Power         | GPIO39              |
|   4 | LED02                  | Low Power         | GPIO34              |
|   5 | SPI (SCK)              | Low Power         | GPIO14              |
|   6 | SPI (MISO)             | Low Power         | GPIO12              |
|   7 | SPI (MOSI)             | Low Power         | GPIO13              |
|   8 | BUZZER                 | Low Power         | GPIO35              |
|   9 | IR SENSOR              | Low Power         | GPIO32              |
|  10 | SPI (SS)               | Low Power         | GPIO15              |
|  11 | I2C (SDA)              | Low Power         | GPIO21              |
|  12 | I2C (SCL)              | Low Power         | GPIO22              |
|  28 | RELAY 01               | Low Power         | GPIO04              |
|  25 | RELAY 02               | Low Power         | GPIO5               |
|  13 | -                      | Low Power         | GPIO33 – GPIO6      |
|  29 | -                      | Low Power         | GPIO0 / BOOT button |
|  30 | Extra pin for LED      | Low Power         | GPIO2               |
+-----+------------------------+-------------------+---------------------+

```
## Deployment
### Communicate with RFID, NEO-6M GPS with ESP-32

#### Connect the following pins of the ESP32 with the RFID RC522 module:


```bash
  
+--------------+-----------------+
| EPS- 32 PINs | RFID RC522 PINs |
+--------------+-----------------+
| 3.3V         | VCC             |
| GND          | GND             |
| GPIO5        | RST             |
| GPIO18       | MISO            |
| GPIO23       | MOSI            |
| GPIO19       | SCK             |
| GPIO22       | SDA             |
+--------------+-----------------+

```
### Install the "RFID RC522" library:
To use the RFID RC522 module with the ESP32, you need to install the RFID library. You can install it using the Arduino IDE Library Manager or by downloading the library and manually installing it.
1.	Install the MFRC522 library in the Arduino IDE to program the ESP32 board.

2.	In the setup function, initialize the SPI communication and the MFRC522 library.

3.	In the loop function, use the MFRC522 library to detect RFID tags and read their data.

4.	Now we can use the read data to grab Log in Log Out details.

Link - https://github.com/miguelbalboa/rfid.git

#### Connect the following pins of the ESP32 with the NEO-6M module:

``` bash

+--------+-------+
| ESP32  | NEO6M |
+--------+-------+
| GPIO16 | TX    |
| GPIO17 | RX    |
| 3.3V   | VCC   |
| GND    | GND   |
+--------+-------+

```
### Install the “TinyGPSPlus” library:
1.	First, the necessary libraries are included. “SoftwareSerial” is used to communicate with the NEO6M GPS module using the ESP32's digital pins, and “TinyGPSPlus” is used to parse the GPS data. Because GPS module only generate NMEA data. We have converted NMEA data to Longitude and Latitude.

2.	The RX and TX pins for the “SoftwareSerial” communication are defined. In this case, the RX pin is set to 17 and the TX pin is set to 16.

3.	Install the TinyGPS++ library in the Platform IO. 

Link - https://github.com/mikalhart/TinyGPS.git

#### Connect the relay module to the ESP32 as follows:

``` bash
+------------------+-----------+
| Relay Module Pin | ESP32 Pin |
+------------------+-----------+
| VCC              | 5V        |
| GND              | GND       |
| IN1              | GPIO 26   |
+------------------+-----------+

```
Connect the solenoid lock to the relay module as follows:
1.	Connect one end of the solenoid lock to the NO (Normally Open) pin of the relay module.

2.	Connect the other end of the solenoid lock to the GND pin of the ESP32.

#### Block diagram of the ESP-32 and other modules

![App Screenshot](https://imgtr.ee/images/2023/03/24/9aBwV.jpg)

#### Block diagram of the connected servers

![App Screenshot](https://imgtr.ee/images/2023/03/24/9aicF.jpg)

#### Circuit diagram

![App Screenshot](https://imgtr.ee/images/2023/03/24/9azIB.jpg)

#### Process of the cash transit

![App Screenshot](https://imgtr.ee/images/2023/03/24/9lRrA.jpg)

You can get a better understanding of our project and how it works from the flowchart below. Each step is explained in the flowchart below and the complete logic will be explained here.

#### Flowchart of the overall process

![App Screenshot](https://imgtr.ee/images/2023/03/24/9lkeJ.jpg)

### Explaination of the web pages

Below is explained about the webpage and I have used a previously created (opensource) webpage and it has been adjusted as per my requirement. The webpages I masked and the sections I changed are clearly listed below.

#### Login page:
The login page provides an authentication system for the admin to access the system. The admin can log in using their email and password, and once they are authenticated, they will be redirected to the dashboard page. Additionally, there is a "Forgot Password" feature, which allows the admin to reset their password if they forget it. The "Edit and Update admin profile" feature enables the admin to modify their personal details such as name, email, and password.

#### Manage Users Page:
The "View users" feature allows the admin to see a list of all the registered users in the system. The admin can also add new users to the system using the "Add New User" feature. The "Edit and update the existing users" feature allows the admin to modify the user's personal details such as name, email, and department. Finally, the "Remove Users" feature allows the admin to delete a user from the system.

#### Manage Device Page:
The "Add new device" feature allows the admin to add a new RFID device to the system. The admin can update an existing device using the "Update existing device" feature. Additionally, the "Delete device" feature enables the admin to remove a device from the system. The "Update New token to the device" feature allows the admin to update the device token in case of a replacement. Finally, the "Change the device mode" feature enables the admin to switch between two modes of the RFID device- Enrollment Mode and Attendance Mode.

#### View Users Log Page:
The "View Users Log" page displays all the attendance records of the registered users. The admin can view the arrival and leaving time of a user and filter the logs based on different parameters such as user, date, arrival time, leaving time, and department. The filter functionality makes it easier for the admin to sort through the attendance data and generate reports.

#### Location Page: 
The ESP32 code creates a web server and runs a function to load the map and plot an initial marker. This function also contains a setInterval() method that triggers the getPosition() function every second. The getPosition() function sends a GET request to the ESP32 IP address to retrieve the GPS coordinates. The latitude and longitude values are then extracted and the marker is repositioned using the changeMarkerPosition() function.

The web page files are uploaded to an external server, and the ESP32 code is modified to send GPS data via HTTP POST to the external server. The PHP file on the external server captures the POST data and saves it to a text file. The getPosition() function is updated to read from the text file using a JQuery GET method. (This page developed by me)

#### Emergency Page:
Here the solenoid lock can be locked and unlocked manually and considering the security in this project, we thought about putting an ink degradation system for this bag. So, for further development, a button was added to this device that can turn the ink degradation system on and off. Another important thing here is that we have developed a method to know whether this bag is sealed or not. It receives data through an IR sensor.

### Headings and data types of the database tables

### Table: admin
``` bash
+-------------+-----------+-------------+
|   Column    | Data Type | Constraints |
+-------------+-----------+-------------+
| id          | integer   | primary key |
| admin_name  | varchar   | not null    |
| admin_email | varchar   | not null    |
| admin_pwd   | longtext  | not null    |
+-------------+-----------+-------------+
```
### Table: devices
``` bash

+-------------+-----------+-----------------------+
|   Column    | Data Type |      Constraints      |
+-------------+-----------+-----------------------+
| id          | integer   | primary key           |
| device_name | varchar   | not null              |
| device_dep  | varchar   | not null              |
| device_uid  | text      | not null              |
| device_date | date      | not null              |
| device_mode | tinyint   | not null, default = 0 |
+-------------+-----------+-----------------------+

```
### Table: users
```bash

+--------------+-----------+----------------------------+
|    Column    | Data Type |        Constraints         |
+--------------+-----------+----------------------------+
| id           | integer   | primary key                |
| username     | varchar   | not null, default = 'None' |
| serialnumber | double    | not null, default = 0      |
| gender       | varchar   | not null, default = 'None' |
| email        | varchar   | not null, default = 'None' |
| card_uid     | varchar   | not null                   |
| card_select  | tinyint   | not null, default = 0      |
| user_date    | date      | not null                   |
| device_uid   | varchar   | not null, default = '0'    |
| device_dep   | varchar   | not null, default = '0'    |
| add_card     | tinyint   | not null, default = 0      |
+--------------+-----------+----------------------------+

```
### Table: users_logs

``` bash

+--------------+-----------+-----------------------+
|    Column    | Data Type |      Constraints      |
+--------------+-----------+-----------------------+
| id           | integer   | primary key           |
| username     | varchar   | not null              |
| serialnumber | double    | not null              |
| card_uid     | varchar   | not null              |
| device_uid   | varchar   | not null              |
| device_dep   | varchar   | not null              |
| checkindate  | date      | not null              |
| timein       | time      | not null              |
| timeout      | time      | not null              |
| card_out     | tinyint   | not null, default = 0 |
+--------------+-----------+-----------------------+

```



## Documentation

[Documentation](https://securein.com/intelligent-products/ibox-rds-cash-collection/)

[Documentation](https://www.security.co.za/companies/628/products)

[Documentation](https://mactwincashsecurity.com/our-vision-on-cash-security/irreversible-cash-degradation/)

[Documentation](https://www.researchgate.net/publication/266412980_Real_Time_Vehicle_Tracking_System_using_GSM_and_GPS_Technology-An_Anti-theft_Tracking_System)

[Documentation](https://media.neliti.com/media/publications/422070-real-time-vehicle-tracking-system-using-9c0ccb27.pdf)

[Documentation](https://www.academia.edu/35735760/Vehicle_Tracking_and_Locking_System_Based_on_GSM_and_GPS)

[Documentation](https://lastminuteengineers.com/esp32-ntp-server-date-time-tutorial/)

[Documentation](https://circuitdigest.com/microcontroller-projects/msp430-vehicle-tracking-and-accident-detection-using-vibration-sensor)






## Appendix

### Additional information 

![App Screenshot](https://imgtr.ee/images/2023/03/24/9l6UF.jpg)

![App Screenshot](https://imgtr.ee/images/2023/03/24/9lLTm.jpg)

![App Screenshot](https://imgtr.ee/images/2023/03/24/9lNsU.png)

