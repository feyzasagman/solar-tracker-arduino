# solar-tracker-arduino
Solar Tracker (Arduino) ☀️📡

Bu proje, 4 adet LDR (ışık sensörü) kullanarak ışığın geldiği yönü tespit eder ve 2 adet servo motor ile sistemi (yatay + dikey eksen) otomatik olarak ışığa doğru döndürür. Temel amaç, güneş takip (solar tracker) mantığını Arduino üzerinde uygulamaktır.

Özellikler

4 LDR ile üst-alt ve sol-sağ ışık farkı hesaplanır

2 servo ile yatay (pan) ve dikey (tilt) hareket yapılır

Tolerans değeriyle gereksiz servo titreşimleri azaltılır

Seri monitör üzerinden sensör ortalamaları ve tolerans takibi yapılabilir

Kullanılan Malzemeler

Arduino Uno

2x Servo motor (ör: SG90/MG90S)

4x LDR

4x 10kΩ direnç (LDR ile gerilim bölücü için)

Breadboard ve jumper kablolar

(Öneri) Servolar için harici 5V güç kaynağı

Bağlantılar
Servo Motorlar

Yatay Servo (horizontal) Sinyal → D9

Dikey Servo (vertical) Sinyal → D10

Servo VCC → 5V (harici besleme önerilir)

Servo GND → GND (Arduino GND ile ortak olmalı)

LDR Sensörler (Analog giriş)

Kod analogRead() kullandığı için LDR’ler A0–A3 analog pinlere bağlanmalıdır.

Önerilen eşleştirme:

Sol Üst (LT) → A2

Sağ Üst (RT) → A3

Sol Alt (LD) → A0

Sağ Alt (RD) → A1

Not: Her LDR, 10kΩ direnç ile gerilim bölücü şeklinde bağlanmalıdır.

Çalışma Mantığı

4 LDR’den analog değerler okunur.

Üst ortalama (avt), alt ortalama (avd), sol ortalama (avl), sağ ortalama (avr) hesaplanır.

Üst-alt farkı dikey, sol-sağ farkı yatay servo hareketini belirler.

Fark, tolerans değerinden büyükse servo açıları 1’er derece güncellenir.

Servo açıları belirlenen limitler içinde tutulur.

Seri Monitör

Baud rate: 9600

Ekranda avt avd avl avr dtime tol değerleri yazdırılır.

Önemli Notlar

Servolar USB’den yeterli akım alamazsa titreme/çalışmama olabilir. Harici 5V besleme önerilir.

Harici besleme kullanıldığında GND mutlaka ortak olmalıdır.

Kod içinde analogRead(2) gibi kullanım A2 anlamına gelir (D2 değil).

Dosyalar

solar_tracker.ino → Arduino kodu

README.md → Proje açıklaması
