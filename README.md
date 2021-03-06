# ATSAMR34_ECC608A_TTI
> “Wireless Made Easy!" - Develop with the SAM R34 LoRa SiP and Microchip LoRaWAN stack on TTI join server

<p>
<a href="https://www.microchip.com/design-centers/security-ics/trust-platform/trust-go/trust-go-lora-secure-authentication-with-join-servers" target="_blank">
<img border="0" alt="Microchip_logo" src="Doc/Microchip_logo.png" width="150">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp

<a href="https://www.thethingsindustries.com" target="_blank">
<img border="0" alt="TTI_logo" src="Doc/TTI_logo.png" width="150">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp

<a href="https://youtu.be/eXXl485fbBE" target="_blank">
<img src="https://img.youtube.com/vi/eXXl485fbBE/0.jpg" 
alt="Secure Authentication for LoRa with the ATECC608A and The Things Industries (TTI) Join Server" width="240"></a>

</p>
</a>



**This guide will direct you through the process of getting started with developing a secure LoRa end device product using Microchip Technology's Pre-provisioned ATECC608A secure element along with TTI Join server.**
</br>
The Things Industries created a product and a service that delivers secure join, secure communication and secure key provisioning.

1. [Material required](#step1)
2. [Software](#step2)
3. [Hardware setup](#step3)
4. [Sample Application Code](#step4)
5. [TTI Activation](#step5)
6. [Running the demo](#step6)

## Material required <a name="step1"></a>

Purchase samples of the <a href="https://www.microchipdirect.com/product/search/all/ATECC08A-TNGLORA" target="_blank">ATECC608A-TNGLORA</a>
secure element 
and the <a href="https://www.microchipdirect.com/product/search/all/AT88CKSCKTUDFN-XPRO" target="_blank">CryptoAuthentication UDFN Socket Kit</a>
</br>
![](Doc/CryptoAuthenticationUDFN.png)
</br>

Purchase the <a href="https://www.microchip.com/Developmenttools/ProductDetails/DM320111" target="_blank">SAM R34 Xplained Pro Evaluation Kit</a>
</br>
![](Doc/ATSAMR34Xpro.png)
</br>

Purchase a LoRa(r) Gateway from <a href="https://www.thethingsindustries.com/technology/hardware#gateway" target="_blank">The Things Industries</a>
</br>
![](Doc/TTI_Hardware.png)
</br>


## Software <a name="step2"></a>

- Download and install Atmel Studio 7.0 IDE. </br>
https://www.microchip.com/mplab/avr-support/atmel-studio-7

- Open Atmel Studio 7.0 IDE. </br>
- Then, you need Advanced Software Framework (ASFv3) v3.47.0 release or upper release. </br>
Install ASFv3 as an extension to Atmel Studio from the menu: Tools -> Extensions and Updates …
- Once the installation is complete, you must restart Atmel Studio. </br>
- Download and install a serial terminal program like Tera Term. </br>
https://osdn.net/projects/ttssh2/releases/

Note: ASFv3 is an MCU software library providing a large collection of embedded software for AVR® and SAM flash MCUs and Wireless devices. ASFv3 is configured by the ASF Wizard in Atmel Studio 7.0 (installed as an extension to Studio). ASFv3 is also available as a standalone (.zip) with the same content as Studio extension (https://www.microchip.com/mplab/avr-support/advanced-software-framework).

Important:
Until the next Atmel Studio IDE release, you have to manually install the Device Part Pack for developing with SAMR34/R35 on Atmel Studio 7.0 IDE.
(all products released in between IDE releases of Atmel Studio should be manually added by user to develop applications).
- Go to Tools -> Device Pack Manager </br>
- Check for Updates </br>
- Search for SAMR34 and click install </br>
- Repeat the same for SAMR35 </br>
- Restart Atmel Studio 7.0 IDE </br>


## Hardware setup <a name="step3"></a>

Configure the DIP switch of the CryptoAuthenticationUDFN Socket kit for I2C communication with the host microcontroller.
**1, 3 and 7 must be placed to ON position**
</br>
![](Doc/DIP_Switch.png)
</br>

Open the socket board
</br>
![](Doc/OpenSocketBoard.png)
</br>

Make sure the ATECC608A device is ready to be inserted in the right direction.
Make sure the pin 1 of the component (represented by a point) is located at the bottom left.
</br>
![](Doc/SecureElement.png)
</br>

Place the Secure Element in the UDFN socket
</br>
![](Doc/SecureElementPlacement.png)
</br>

Make sure the Secure Element is properly seated and the pin 1 is located at the bottom left.
</br>
![](Doc/SecureElementPlaced.png)
</br>
Close the clam shell lid.
</br>

Attach the CryptoAuthenticationUDFN Socket kit to the SAM R34 Xplained Pro board on the **EXT3 header.**
</br>
Plug the antenna.
Attach a USB cable to SAM R34 Xplained Pro board's EDBG micro-B port on the right.</br>
The USB ports powers the board and enables the user to communicate with the kits.
</br>
![](Doc/FullSetup.png)


- Wait for USB driver installation and COM ports mounting. </br>
- Launch Tera Term program and configure the serial ports mounted with: **115200 bps, 8/N/1**

## Sample Application Code <a name="step4"></a>

Open the "APPS_ENDDEVICE_DEMO" project with Atmel Studio 7 IDE</br>
From the top menu, go to Project -> APPS_ENDDEVICE_DEMO Properties</br>
From Tool settings, select your board as EDBG debugger with SWD interface
</br>
![](Doc/EDBG.png)
</br>
Build and download the project by clicking the empty green "Run without debugging" triangle
</br>
![](Doc/AtmelStudio.png)
</br>
Open the Tera Term UART console previously configured at 115200 bps, 8-data bits/No parity/1-stop bit
</br>
Press the "Reset" button on the SAM R34 Xplained Pro board to see output printed to the console
</br>
Observe the following identifiers coming from the ATECC608A Secure Element
</br>
![](Doc/UART_Console1.png)
</br>


In order to pre-commission a device using ATECC608A secure element in TTI Activation, the following idenfiers are required:

- DevEUI: LoRaWAN device 64-bit unique identifier assigned by the Device manufacturer (or using Secure Element default value)
- JoinEUI: LoRaWAN JS 64-bit unique identifier of the Join Server on which AppKey of the device is stored


## TTI Join Server Activation <a name="step5"></a>

Activating the device within TTI is the next step.</br>

Go here: <a href="https://www.thethingsindustries.com/technology/security-solution" target="_blank">https://www.thethingsindustries.com/technology/security-solution</a>

And follow the steps to get started with claiming your devices.


## Running the demo <a name="step6"></a>

Go back to the Tera Term UART console
</br>
![](Doc/UART_Console2.png)
</br>
Press "1" to start the Demo Application
</br>
Select the band where your device is operating
</br>
![](Doc/UART_Console3.png)
</br>
Then, the end device application transmits a Join Request message. If a Join Accept message was received and validated, the SAM R34 Xplained Pro board will be joined to the Join Server.
</br>
![](Doc/UART_Console4.png)
</br>
Press "2" to send a packet consisting of a temperature sensor reading
</br>
![](Doc/UART_Console5.png)
</br>

