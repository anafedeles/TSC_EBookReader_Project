# TSC_EBookReader_Project

## 
OpenBook este un dispozitiv avansat construit în jurul microcontrolerului ESP32-C6, cu diverși senzori și interfețe.

## Diagramă bloc cu toate componentele proiectului

## Listă de materiale (BOM)

| Componentă             | Link pentru achizitionare                                                                                             | Link Datasheet                                                                                                      |
|------------------------|----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| 112A-TAAR-R03 ATTEND   | https://store.comet.srl.ro/Catalogue/Product/43497/                                                            | https://www.snapeda.com/parts/112A-TAAR-R03/Attend/datasheet/                                                     |
| BD5229G-TR             | [https://www.digikey.com/en/products/detail/rohm-semiconductor/BD5229G-TR/3663792  ](https://eu.mouser.com/ProductDetail/ROHM-Semiconductor/BD5229G-TR?qs=4kLU8WoGk0vvnhrrYwdszw%3D%3D)                            | https://fscdn.rohm.com/en/products/databook/datasheet/ic/power/voltage_detector/bd52xxg-e.pdf                      |
| ESP32 WROVER BME680 Sensor                 | [https://ro.mouser.com/ProductDetail/Bosch-Sensortec/BME688?qs=IS%252B4QmGtzzqQoVDscqwx3A%3D%3D  ](https://store.comet.srl.ro/Catalogue/Product/50164/)              | (https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme680-ds001.pdf)                                                  |
| LED CHG_LED                | https://ro.mouser.com/ProductDetail/Kingbright/KP-1608SURCK?qs=2JU0tDl2GZ3FuyEWfBV1%2Fg==                     | https://www.snapeda.com/parts/KP-1608SURCK/Kingbright/datasheet/                                                  |
| Condensator C0402      | https://ro.mouser.com/c/passive-components/capacitors/ceramic-capacitors/?q=CC0402                           | https://componentsearchengine.com/Datasheets/2/CC0402MRX5R5BB106.pdf                                               |
| Condensator Tant  | https://ro.mouser.com/ProductDetail/KYOCERA-AVX/TAJW107M010RNJ?qs=Wtp%252Bf%2FAeVqIH8v1VxV%252B1Rg%3D%3D        | https://ro.mouser.com/datasheet/2/40/TAJ-3165264.pdf                                                               |
|Q1 DMG2305UX-7            | https://www.digikey.com/en/products/detail/diodes-incorporated/DMG2305UX-7/4340666                           | https://www.diodes.com/assets/Datasheets/DMG2305UX.pdf                                                             |
| RTC MODULE DS3231SN#              | (https://www.snapeda.com/parts/DS3231SN%23/Analog+Devices/view-part/?ref=eda) | (https://www.snapeda.com/parts/DS3231SN%23/Analog%20Devices/datasheet/)                                                           |
| ESP32 C6 WROOM-1-N8    | https://ro.mouser.com/ProductDetail/Espressif-Systems/ESP32-C6-WROOM-1-N8?qs=8Wlm6%252BaMh8ST02Gmwp74cw%3D%3D | (https://www.snapeda.com/parts/ESP32-C6-WROOM-1-N8/Espressif%20Systems/datasheet/)              |
| FH34SRJ-24S-0.5SH(99)  | [https://ro.mouser.com/ProductDetail/Hirose-Connector/FH34SRJ-24S-0.5SH99?qs=vcbW%252B4%252BSTIpKBl5ap9J8Fw%3D%3D](https://ro.mouser.com/ProductDetail/Hirose-Connector/FH34SRJ-24S-0.5SH99?qs=vcbW%252B4%252BSTIpKBl5ap9J8Fw%3D%3D)) | (https://www.snapeda.com/parts/FH34SRJ-24S-0.5SH(99)/Hirose%20Connector/datasheet/)           |
| MAX 17048G+T10          | (https://www.snapeda.com/parts/MAX17048G+T10/Analog+Devices/view-part/?ref=eda)  | (https://www.snapeda.com/parts/MAX17048G+T10/Analog%20Devices/datasheet/)                                          |
| MBR0530 Schottky Diode              | (https://www.snapeda.com/parts/MBR0530/Onsemi/view-part/?ref=snap)              | ](https://www.snapeda.com/parts/MBR0530/ON%20Semiconductor/datasheet/)                                                    |
| ESP32 WROVER MCP73831 Power Management              | ](https://www.snapeda.com/parts/BME680/Bosch/view-part/?welcome=home) | (https://www.snapeda.com/parts/MCP73831T-2ACI/OT/Microchip/datasheet/)                      |
| PFMF.050.1             | https://ro.mouser.com/ProductDetail/EPCOS-TDK/B72520T0350K062?qs=dEfas%2FXlABIszF52uu7vrg%3D%3D               | https://www.tdk-electronics.tdk.com/inf/75/db/CTVS_14/Surge_protection_series.pdf                                  |
| PGB1010603MR           | ](https://www.snapeda.com/parts/PGB1010603MR/Littelfuse/view-part/?ref=eda)                              | (https://www.snapeda.com/parts/PGB1010603MR/Littelfuse%20Inc./datasheet/) |
| QWIIC_RIGHT_ANGLE CONNECTOR     | https://ro.mouser.com/ProductDetail/SparkFun/PRT-14417?qs=wd5RIQLrsJhgdz%2FpmZ%2F3GQ==                        | https://ro.mouser.com/datasheet/2/813/Qwiic_Connector_Datasheet-1223982.pdf                                        |
| Rezistență R0402       | https://grabcad.com/library/resistor-0402-1)  | https://www.yageo.com/upload/media/product/products/datasheet/rchip/PYu-RC_Group_51_RoHS_L_12.pdf                 |
| SD0805S020S1R0         | https://ro.mouser.com/ProductDetail/KYOCERA-AVX/SD0805S020S1R0?qs=jCA%252BPfw4LHbpkAoSnwrdjw%3D%3D            | https://ro.mouser.com/datasheet/2/40/schottky-3165252.pdf                                                          |
| Si1308EDL-T1-GE3 MOSFET      | ](https://www.snapeda.com/parts/SI1308EDL-T1-GE3/Vishay+Siliconix/view-part/?welcome=home&ref=eda)                                  | https://www.snapeda.com/parts/SI1308EDL-T1-GE3/Vishay%20Siliconix/datasheet/)                                                                     |
| USB4110-GF-A           | https://ro.mouser.com/ProductDetail/GCT/USB4110-GF-A?qs=KUoIvG%2F9IlYiZvIXQjyJeA%3D%3D                        | https://ro.mouser.com/datasheet/2/837/GCT_USB4110_Product_Drawing___20k_cycles-3455479.pdf                         |
| USBLC6-2SC6Y           | https://ro.mouser.com/ProductDetail/STMicroelectronics/USBLC6-2SC6Y?qs=gNDSiZmRJS%2FOgDexvXkdow%3D%3D         | https://ro.mouser.com/datasheet/2/389/usblc6_2sc6y-1852505.pdf                                                     |
| W25Q512JVEIQ           | ]https://www.snapeda.com/parts/W25Q512JVEIQ/Winbond+Electronics/view-part/?ref=eda)                     | (https://www.winbond.com/resource-files/W25Q512JV%20SPI%20RevB%2006252019%20KMS.pdf)                                      |
| XC6220A331MR-G         | (https://componentsearchengine.com/part-view/XC6220A331MR-G/Torex)          | (https://product.torexsemi.com/system/files/series/xc6220.pdf)                                                          |
| 744043680   BOBINA  | https://ro.mouser.com/ProductDetail/Wurth-Elektronik/744043680?qs=PGXP4M47uW6VkZq%252BkzjrHA%3D%3D             | https://www.we-online.com/components/products/datasheet/744043680.pdf                                              |
 

## Funcționalitatea Hardware 
ESP32-C6 este nucleul EOpenBook-ului, oferind conectivitate Wi-Fi 6 și Bluetooth 5.0 LE. Acesta include:

### Procesor RISC-V single-core de 160MHz
512KB de SRAM
8MB de memorie flash externă
Conectivitate wireless integrată
Multiple pini GPIO pentru interfațarea cu componente periferice

### Afișaj E-Paper

Afișajul e-paper oferă o interfață vizuală cu consum redus pentru EBook
Conectat prin interfața SPI la ESP32-C6
Utilizează driver-ul BD5229G-TR pentru a gestiona diversele tensiuni necesare afișajului
Alimentarea afișajului este controlată de MOSFET-uri pentru a asigura oprirea completă când nu este utilizat
Conectorul afișajului (FH34SRJ-24S-0.5SH) oferă o conexiune fiabilă la modulul flexibil de afișare

### Senzor de Mediu

Senzorul BME688 oferă măsurători pentru:

Temperatură (precizie ±0.5°C)
Umiditate (precizie ±3% RH)
Presiune (precizie ±0.12 hPa)
Calitatea aerului (detectare VOC)
Conectat prin interfața I²C (SCL/SDA)
Funcționează la 3.3V cu un consum tipic de curent de 3.7mA în timpul măsurătorilor

### Gestionarea Energiei

Conector USB-C (112A-TAAR-R03) pentru alimentare și comunicare de date
USBLC6-2SC6Y oferă protecție ESD pentru liniile USB
MCP73831 controller pentru încărcarea bateriei Li-Ion/Li-Polymer cu o singură celulă:

Curent de încărcare programabil până la 500mA
Terminare automată a încărcării
Indicare status prin LED


MAX17048G+T10 monitorizează starea bateriei:

Oferă o estimare precisă a stării de încărcare (SoC)
Comunică prin I²C
Consum redus de energie (23μA)


XC6220A331MR-G LDO oferă o ieșire stabilă de 3.3V:

Interval de tensiune de intrare: 2.0V până la 6.0V
Curent de ieșire până la 700mA
Tensiune de dropout scăzută (90mV tipic la 100mA)



### Ceas în Timp Real

DS3231SN RTC de înaltă precizie:

Oscilator cu cristal compensat în temperatură (TCXO)
Precizie ±2ppm (±1 minut pe an)
Baterie de backup folosind un supercondensator
Interfață I²C pentru comunicare
Funcții de alarmă cu capacitate de întrerupere



### Stocare Externă

W25Q512JVEIQ 512Mb (64MB) Flash NOR Serial:

Interfață SPI la până la 133MHz
100.000 de cicluri de programare/ștergere
Retenție date: 20 de ani
Folosit pentru stocarea datelor aplicației, configurare și actualizări firmware


Interfață card SD pentru stocare extensibilă:

Conectată prin interfață SPI
Suportă formate standard de card SD



### Protecție ESD

Diodele PGB1010603MR protejează liniile SPI sensibile
USBLC6-2SC6Y protejează liniile de date USB
Layout-ul atent al PCB-ului cu planuri de masă și rutare corespunzătoare îmbunătățește performanța EMI/EMC

### Analiza Consumului de Energie

Mod de repaus: <50μA (ESP32-C6 în deep sleep, RTC activ)
Mod inactiv: ~25mA (ESP32-C6 treaz, periferice în standby)
Mod activ: ~150mA (toate sistemele active, fără a include reîmprospătarea afișajului)
Reîmprospătare afișaj: ~20mA vârf în timpul reîmprospătării, 0mA când este static
Estimare durată de viață a bateriei:

Cu o baterie tipică LiPo de 2000mAh
~80 de ore de funcționare continuă în mod inactiv
~2-3 săptămâni cu modele tipice de utilizare (treziri periodice și actualizări ale afișajului)

## Alocarea Pinilor ESP32-C6

| Componentă                  | Pini ESP32                                                  | Interfață         | Note                                                                                                                               |
|-----------------------------|-------------------------------------------------------------|-------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Afișaj E-Paper              | IO12 (EPD_CS), IO11 (EPD_DC), IO5 (EPD_RST), IO4 (EPD_BUSY) | SPI (MOSI, SCK)   | Pin CS selectat pentru suport hardware SPI                                                                                          |
| Senzor de Mediu (BME688)    | IO8, IO10                                                   | I²C (SDA, SCL)    | Se folosesc pull-up-uri interne                                                                                                     |
| Memorie Flash Externă       | IO0 (FLASH_CS)                                              | SPI (MOSI, MISO, SCK) | Partajează busul SPI cu afișajul, dar cu CS dedicat                                                                                |
| Card SD                     | IO7 (SS_SD)                                                 | SPI (MOSI, MISO, SCK) | Partajează busul SPI cu alte componente                                                                                             |
| Ceas în Timp Real (DS3231SN) | IO8, IO10                                                   | I²C (SDA, SCL)    | Partajează busul I²C cu BME688, întrerupere pe IO13 (INT_RTC)                                                                      |
| Indicator Baterie           | IO8, IO10                                                   | I²C (SDA, SCL)    | Partajează busul I²C cu alte dispozitive I²C                                                                                       |
| Serial USB                  | IO16 (TX), IO17 (RX)                                        | UART              | Pini UART impliciți pentru programare și debug                                                                                       |
| Interfață Utilizator        | IO9 (IO/BOOT), IO19 (IO/CHANGE)                             | GPIO              | Pini de intrare cu pull-up-uri pentru butoanele utilizatorului                                                                     |

Bus SPI: Bus-ul SPI este partajat între mai multe dispozitive (afișaj, flash, card SD) pentru a minimiza utilizarea pinilor. Fiecare dispozitiv are un pin dedicat de selectare a chip-ului pentru a asigura o comunicare corectă.
Bus I²C: Un singur bus I²C conectează toate dispozitivele I²C (BME688, RTC, indicator baterie) pentru a minimiza utilizarea pinilor, oferind în același timp o comunicare fiabilă la viteze standard (100kHz-400kHz).
Pini GPIO: Pinii cu capacitate de întrerupere (IO13, IO19) au fost selectați pentru funcții care necesită funcționalitate de trezire.
UART: Pinii standard UART (IO16/IO17) sunt utilizați pentru programare și depanare pentru a asigura compatibilitatea cu instrumentele standard de dezvoltare.
Gestionarea Energiei: Pinii de control pentru domeniile de alimentare sunt configurați pentru a permite controlul individual al perifericelor pentru o gestionare optimă a energiei.

##Detalii Suplimentare de Proiectare

### Asezarea TP-urilor: 
TP-urile au fost amplasate strategic în apropierea marginilor plăcii de circuit imprimat și în vecinătatea componentelor cheie. Această alegere facilitează accesul pentru operațiunile de depanare și testare.
## Diode (Montare pe Suprafață ):
Designul inițial al amprentei pentru diode prezenta orificii de contact (pad holes) cu un diametru insuficient, ceea ce ar fi putut genera dificultăți semnificative în procesul de lipire. Pentru a asigura o fabricație fără probleme și o conexiune electrică solidă, dimensiunea acestor orificii a fost revizuită.
## Rutare și Plan de Masă: 
Rutarea traseelor a fost realizată atât pe stratul superior, cât și pe stratul inferior al PCB-ului. Această strategie a necesitat utilizarea unui total de 1105 vias pentru a interconecta diferitele straturi și a permite o rutare complexă a semnalelor. Deși un număr mare de vias poate influența costul și complexitatea fabricației, utilizarea ambelor straturi oferă o flexibilitate sporită în distribuția semnalelor și a alimentării. Planul de masă (GND) a fost implementat după finalizarea rutării, fiind aplicat pe ambele straturi ale plăcii (superior și inferior). 
