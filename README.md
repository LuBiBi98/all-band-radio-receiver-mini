# all-band-radio-receiver-mini

Introduction: 
This is an ESP32S3 full band radio project suitable for beginners to reproduce. Using the ESP32S3-N16R8 module as the main control MCU, SI4735 as the radio control module, and TC8002D for audio output.
- Open source protocol: CERN Open Hardware License
![image](https://github.com/LuBiBi98/all-band-radio-receiver-mini/assets/116412764/c26a4dfe-0417-4baa-99a1-67770dedd85b)



Project Description
- This project is aimed at Arduino developers, radio experimenters, hobbyists and anyone interested in building an all-band (including AM, FM, SSB)radio receiver based on the SI4735. The frequency range of AM and SSB modes is 150kHz to 30MHz, while FM mode is 64 to 108MHz.
- This project consists of two PCBs, a main board and an extension board. The main board supports all basic functions, including all-band radio signal reception, processing, and playback, as well as function key operation. The extension board needs to be established based on the main board. After connecting to the main board, the extension board can achieve time display and synchronization, temperature and humidity display, and connect to the battery module for power supply. 

Core/special Components

- TC8002D, audio amplifier chip
- The LCD screen uses a 1.47 inch 12 pin soldering type
- WS2812B-B 5050 Colorful LED for decoration
- Crystal oscillator uses 32768 active crystal oscillator
- The headphone jack is a PJ-320B patch socket
- The antenna socket is an SMA socket, which corresponds to an antenna with an SMA interface
- Magnetic coil that supports receiving AM signals
- SSOP-24 encapsulated SI4735-D60-GU
- ESP32-S3-WROOM-1U-N16R8
- The real time clock chip RX8025T-UC to support date and time display.
- The temperature and humidity sensor SHT30, if not desired, can be removed with no temperature and humidity number displayed on LCD. The software program firmware can work normally without it.
- The charging management chip is IP5306. The function can be turned on by short pressing on the power button on the back panel, turned off by double pressing on the same button.
 

Project Related Functions

1、 Main interface functions
1. Volume adjustment function: Short press the volume control button and rotate the encoder to adjust the audio size of the radio;
2. Modulation mode selection: Short press the modulation mode selection button, rotate the encoder, and you can choose to receive radio signals under the four modulation modes including: AM FM USB LSB. Press the encoder down to confirm the current selection;
3. Manual channel adjustment function: Short press the manual channel adjustment button, rotate the encoder, and manually adjust the received radio signal frequency by 0.1Mhz units;
4. Quick target band locking function: Due to the large range of radio signal bands covered by the full band radio, it is necessary to quickly lock a certain band function to help reduce manual channel adjustment workload; Short press the Quick Select Band button and rotate the encoder to quickly locate the received band in bands such as 20M 40M 80M. Press the encoder down to confirm the current selection;

2、 Expansion board function
1. Expansion module: including power management, real time clock module for date&time display, temperature and humidity module;
2. Long press the button in the bottom left corner of the front panel to show extended dashboard:
3. Timing synchronization: Short press the function key in the bottom left corner to switch the timing object (hour, minute, second, year, day), and rotate the encoder to synchronize.

Introduction to main board design and functional description: https://youtu.be/LVF68FzS0V0
Introduction to extension board design and functional description:  https://youtu.be/IU4aah9qmFE


Software Program Firmware

Based on the Arduino IDE framework, the core program logic is as follows:
- [Initialization]: Initialize the device and its functions, including - I2C/display/SI4735/buttons/encoder/power amplifier; 
- [Main loop] : 1. identify the encoder and buttons; 2. Read the status of SI4735; 3. Set SI4735 parameters(frequency, volume, etc.); 4. Draw and display;



Housing Design

The housing mainly consists of four parts: front panel, front shell, back shell, and back panel.
The front panel is made of PET, with adhesive on the back for easy adhesion, and the back panel is made of fully transparent acrylic. The front and back shells are 3D printed with resin  and the front shell is painted with Pantone color code 1795C.
![image](https://github.com/LuBiBi98/all-band-radio-receiver-mini/assets/116412764/5b76afe9-5a66-4cdd-be26-e636877fdf8b)

Introduction to housing installation: https://youtu.be/IU4aah9qmFE



The front panel is made of PET, with adhesive on the back for easy adhesion, and the back panel is made of fully transparent acrylic. The front and back shells are 3D printed with resin  and the front shell is painted with Pantone color code 1795C.



20230528 Update
Air band PCB - Gerber_EB_PCB_V2_2023-05-28.gerber
Schematic Diagram - SCH_EB_SCH_V2_2023-05-28.pdf

202301006 Update
Upload our new Software Firmware for this radio - FW_ESP32S3_Radio_v231004.bin
You might need a flash download tool published by 乐鑫科技(Espressif Systems) -- the manufactor of the radio's MCU chip, to install the fireware. The tool is all uploaded. - flash_download_tool_3.9.2_0.rar
