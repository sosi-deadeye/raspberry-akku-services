# raspberry-akku-services
In diesem Projekt sind alle Konfigurationen und Programme für die Dienste des Köster WLAN-Moduls enthalten.

## systemd
Die meisten Dienste werden via systemd gestartet.

## Netzwerk
Das Netzwerk wird zur Zeit noch nicht mit systemd verwaltet.
Ein Daemon schaltet zwischen Access-Point und Client um.

# Systemdienste

- gpio26on (verhindert das Ausschalten der Platine)
- wlan-switch (Dienst um zwischen AccessPoint-Modus und Client-Modus zu wechseln)
- api (Bereitstellung der Daten via http)
- server (Akquirierung der Daten)

Die Dienste sind via systemd konfiguriert und laufen aktuell noch mit root-Rechten.
Der Quellcode befindet sich in /root/akku
Die statischen Inhalte des Webservers befinden sich in /var/www/html

Der Raspberry Pi Zero W bietet gleichzeitig auch die Möglichkeit die USB-Schnittstelle
als OTG (On The Go) zu konfigurieren. Dann verhält sich der Raspberry Pi Zero W wie ein
USB Gerät. Konfiguriert ist es als Massenspeicher, Serielle Konsole und USB-Ethernet.

Die boot partition und das rootfs sind schreibgeschützt. Lediglich die dritte
Partition ist Lesend-Schreibend eingehangen (/media/data).

## Schreibschutz lässt sich im Betrieb ändern
- rw    # Lesen und Schreiben
- ro    # Nur lesen

## Sprache
Die Dienste sind alle mit Python programmiert.
Es wird ein venv für den Interpreter verwendet (/root/venv)
### Zum aktivieren des venv

source /root/venv/bin/activate

## Folgende Systemdienste laufen im Hintergrund
- hostapd (im AP-Betrieb)
- wpa_supplicant (immer)
- dnsmasq (immer, bedient aber nur ap0 und usb0)
- nginx
- ntp
- ssh

## Netzwerk
Die Konfiguration des Netzwerkes ist in /etc/network/interfaces zu finden.


# Images
Backup-Images können hier heruntergeladen werden: https://archive.server101.icu/.k-akku/
