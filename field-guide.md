# Field Guide

In diesem Dokument finden sich hilfreiche Tipps für den Umgang mit Problemen im Live-Betrieb.

## WiFi Zugriff am Gerät

Das Leezenflow Gerät verbindet sich zu einem vordefinierten Wartungs-Netzwerk. Dieses kann man z.B. per Handy Hotspot oder geteilter Verbindung vom Laptop erstellen.
Nutzt man die richtigen Zugangsdaten (SSID und Passwort) sollte sich das Leezenflow Gerät nach einer kurzen Zeit automatisch verbinden.
Es ist der bCyber SSH "Wartungskey" hinterlegt. Man kann also z.B. mit
`ssh -i .ssh/bcyber pi@LEEZENFLOWIP` eine Verbindung herstellen.
Ansprechpartner für Zugangsdaten ist [bCyber](https://www.bcyber.de).

## Leezenflow Service

Der Python Code läuft als system.d Service und kann mit den folgenden Befehlen gesteuert werden:

Leezenflow stoppen: `sudo service leezenflow stop`  
Leezenflow starten: `sudo service leezenflow start`  
Leezenflow neustarten: `sudo service leezenflow restart`  
Leezenflow Status: `sudo service leezenflow status`  

Außerdem kann die Ausgabe vom Log mit: `journalctl -u leezenflow` angezeigt werden. Mit `journalctl -u leezenflow -f` bleibt die Ausgabe offen und streamt alle neuen Logs.  

## Netzwerk Zugriff im Steuergerät-Kasten

Das Netzwerk im Steuergerät hat eine direkte Verbindung in das städtische Netzwerk. Man könnte somit z.B. aus Versehen auf andere Geräte zugreifen. Eine einfache Möglichkeit das zu verhindern ist es, den Laptop nicht in den vorhanden Switch einzustecken, sondern das vorhandene Kabel zwischen Switch und PoE-Injector abzustecken und mit einem RJ45 zu RJ45 Adapter zu arbeiten. So, dass man physikalisch nur eine Verbindung zum PoE-Injector und der Sender-RSU hat.
