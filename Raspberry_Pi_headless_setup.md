
### 1. Betriebssystem installieren

1. [Raspberry Pi Imager](https://www.raspberrypi.com/software/) installieren und öffnen
2. SD-Karte an Computer anschließen
3. Betriebssystem auswählen und Pi Version wählen
	- **grafische Nutzeroberfläche** oder minimalistisch?
	- 32 oder **64bit**?
4. OS Anpassungen
	1. Allgemein:
		- Hostname: *raketenphysik01*
		- Benutzername: *rakete*
		- Passwort: *physik*
		- Wifi SSID: WLAN-HOEB-Gast
		- Wifi Passwort: hoeb202344
		- Wifi Land: DE
		- Zeitzone: Europe/Berlin
		- Tastaturlayout: de
	2. Dienste:
		- Secure Shell Protocol (SSH) aktivieren
		- Passwort zur Authentifizierung
5. Einstellungen speichern und Betriebssystem installieren
6. Verfizierung abwarten
7. SD-Karte auswerfen und in Raspberry Pi einsetzen

### 2. Verbindung mit Raspberry Pi herstellen

1. Raspberry Pi an Stromversorgung anschließen, grüne LED blinkt
2. Raspberry Pi Boot abwarten, etwa eine Minute
3. Raspberry Pi pingen, um Wifi Verbindung zu überprüfen:
	- Windows 10 CMD: ``ping *hostname*.local``
	- MacOs Terminal: `ping *hostname*.local`
	- Linux Terminal: `ping -c 3 *hostname*.local`
4. Secure Shell Protocol (SSH) Verbindung herstellen:
	- Windows 10 CMD: `ssh *benutzername*@*hostname*.local` -> yes -> *passwort*
	- MacOs Terminal: `ssh *benutzername*@*hostname*.local` -> yes -> *passwort*
	- Linux Terminal: `ssh *benutzername*@*hostname*.local` -> yes -> *passwort*
5. `*benutzername*@*hostname*:~ $` ?
	- erfolgreich mit Raspberry Pi verbunden!
	- Raspberry Pi Kommandozeile nutzen
6. **Raspberry Pi abschalten:**
	- `sudo poweroff`
	- warten bis grüne LED vollständig erlischt
	- Stromversorgung kann sicher getrennt werden
7. SSH Verbindung trennen:
	- `exit`

### 3. Kamera testen

1. Kamera anschließen:
	- Rasperry Pi Zero:
	 ![[Pi_Zero_Camera_Cable.jpg]]
	- Camera Module:
	![[Pi_Zero_Connection_Camera_Module.jpg]]
2. update advanced packaging tool (APT): 
	- `sudo apt update`
	- `sudo apt upgrade -y`
3. Kamera testen:
	- Foto aufnehmen: `rpicam-jpeg --output test.jpg`
	- Foto per secure copy (SCP) von lokalem Computer anfragen (nicht SSH!):
		- Windows 10 CMD: `scp *benutzername*@*hostname*.local`:test.jpg *local_destination_path*` oder `scp *benutzername*@*ip-adress*:test.jpg *local_destination_path*` 
		- analog auf Mac OS und Linux
4. Video Stream testen:
	- Raspberry Pi IP Adresse notieren: `ifconfig`
	- Raspberry Pi (host) bash: `rpicam-vid -t 0 --inline -o - | cvlc stream:///dev/stdin --sout '#rtp{sdp=rtsp://:8554/stream1}' :demux=h264rpicam-vid -t 0 --inline -o - | cvlc stream:///dev/stdin --sout '#rtp{sdp=rtsp://:8554/stream1}' :demux=h264`
	- VLC (client) Netzwerkstream öffnen: `rtsp://*pi-ip-adress*:8554/stream1`
	- Qualität mittelmäßig bis schlecht?

### 4. Virtual Network Computing (VNC) Setup

1. VNC (Server) auf Raspberry Pi anschalten: 
	- `sudo raspi-config`
	- Interfacing Options -> VNC -> enable
	- Konfiguration verlassen: Esc
2. VNC Viewer auf lokalem Computer installieren: https://www.realvnc.com/de/connect/download/viewer/windows/
3. VNC Viewer verbinden:
	- öffnen, ohne anmelden verwenden
	- RVNC connect: `Raspberry Pi IP Adresse` eingeben
	- Remote Desktop:
	![[Raspberry_Pi_VNC.png]]


### 5. VS Code via SSH

https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh

Python Extension does not work on Raspberry Pi Zero!
https://forums.raspberrypi.com/viewtopic.php?t=354898



