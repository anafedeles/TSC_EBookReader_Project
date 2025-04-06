# TSC_EBookReader_Project

## 
EBookReader este un dispozitiv avansat construit în jurul microcontrolerului ESP32-C6, cu diverși senzori și interfețe.

## Diagramă bloc cu toate componentele proiectului

## Listă de materiale (BOM)

#Funcționalitatea Hardware 
ESP32-C6 este nucleul EBookReader-ului, oferind conectivitate Wi-Fi 6 și Bluetooth 5.0 LE. Acesta include:

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
