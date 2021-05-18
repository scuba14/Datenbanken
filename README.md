# Datenbanken Projekt
 Matrikelnummer: 4328112

## Umsetzung der Applikation
## Allgemein
* Backend: Microframework Flask in Python

* Frontend: HTML,CSS und Java Script (JQuery)(Templating Engine:JINJA 2.0)

* Datenbank: SQL-Lite mit SQLAlchemy

## Login-System
* User-Registrierung
* User-Login
* Zugriffsmanagment (Unterteilung in logged-in/rich_user<==>logged-out/poor_user)
* Chat
* Realtime-Chat mit Websocket-Protokoll
* Erstellen von Chat-Räumen mit ausgewählten Usern
* Verlassen von Chat-Räumen
* Schreiben von Nachrichten in Chat-Räumen
* Infinite Scrolling bei Chat-Nachrichten --> gesamte Nachrichten-Historie einsehbar

## Struktur
* Die HTML-Dokumente sind im Template-Folder untergebracht
* Die CSS-Dokumente sind im static/styles-Folder untergebracht
* Die Java Script Dateien sind im static/javascript-Folder untergebracht
* Die Python Dateien liegen in der LT-Home-Directory
Die Datenbank liegt ebenfals in der LT-Home-Directory
Beim Aufbau der HTML-Seiten wird ein JINJA Vererbungsbefehl verwendet:
```python
{{% extends "basic.html" %} 
{% block content %} 
....
{% endblock %}
```
--> alle HTML Seiten erben von der basic.html Seite.

Der Content zum indivdualisieren des Contents kann an die Stelle ... geschrieben werden

## Highlights der Applikation
* Implementierung Real-Time Websocketprotokoll (Alle Aktionen zwischen Usern im Chat erflogen in RealTime)
* Erstellen mehrer individueller Chat-Räume
* Speicherung aller geschriebenen Nachrichten in jedem Chat mittels einer SQLite Datenbank
* Dynamisches Nachladen der Chat-Nachrichten (Infinite Scrolling Ansatz im Chat-Window)
* Verbindung von User-Identifikation und Chat --> Nachrichten können nur von denjenigen gelesen werden die dafür bestimmt sind
* Hoher SchreibKomfort auf PC und Smartphone --> Der Chat hängt sich an den Nachrichtenfluss an. Koppelt sich jedoch ab wenn der User alte Nachrichten durchlesen will (wie bei Whats App)
* Dynamische Nav-Bar (mit CSS Grid)
* Hyperlinkerkennung in Chats
* Nachrichtenton beim Erhalt einer Nachricht (falls man nicht im Chat anwesend ist)
* Website wurde unter der Domain https://ltchatita.herokuapp.com/login?next=%2Fchat deployed
## Anmerkungen
* Die Web-Applikation funktioniert nur bedingt unter Safari 14.1
* Beim Testen des Logins und des Chats mit unterschiedlichen Accounts ist darauf zu achten zwei unterschiedliche Browser zu benutzen oder einen Incognito-Tab zu öffnen. Wenn man nur verschiedene Tabs benutzt weist der Browser den Cookie beiden Tabs zu und man loggt sich automatisch in beiden Tabs mit dem gleichen Account ein.
* Die Überlegungen und das Vorgehen wird in den Kommentaren anhand des Codes detailliert beschrieben
## Installation
 ## Vorraussetzungen
* MAC OS
* Freier Port 5000
* Funktionierende python3 version auf Mac


Zum Testen ob eine Python Version vorhanden ist: Ins Terminal `python3 --version` eintippen.
## Vorgehen
1. Diesen Ordner herunterladen oder `git clone` in gewünschtes Directory
2. Gehe, Sie in den Ordner 4328112
3. In dem Ordner 4328112 ein Terminal öffnen
4. Im Terminal `python3 -m venv venv`eingeben
5. Im Terminal `source venv/bin/activate` eingeben --> im Terminal sollte nun stehen: (venv)Macbookname
6. Im Terminal folgende packages mit dem Befehl `pip3 install -r requirements.txt` eingeben:
7. Der Ordner 4328112 sollte nun 2 Ordner und ein Python Modul mit dem Namen run.py enthalten
8. Starten Sie die Applikation indem Sie im Terminal `python3 run.py` eingeben
9. Browser öffnen
10.`localhost:5000` aufrufen
11. Applikation testen

Bem Start erscheint eine INFO-Meldung von SQL-Alchemy: Diese einfach ignorieren.

Des Weiteren ist die Seite unter folgendem Link zu erreichen:https://ltchatita.herokuapp.com/login?next=%2Fchat

## Datenbankanbindung

Für die Datenbankanbindung wurde SQLite verwendet. Über das Python Package "SQL-Alchemy" lassen sich SQLite Datenbanken mit Python managen.
In der Datei db_models.py wird das Datenbankschema definiert. Dazu werden drei Tabellen erstellt:

* User
* Chat
* Message

Diese Tabellen stehen in unterschiedlichen Beziehungen zueinander:

* 1 User zu n-Chats
* 1 Chat zu n-Messages
* n-User zu n-Messages

Zur Erstellung der n * n Beziehung wird eine Verknüpfungstabelle ("link") verwendet mit welcher die beiden Primärschlüssel miteinader verbunden werden.

Zum Funktionsumfang gehören folgende Datenbankzugriffe:

* Erstellen von Usern
* Erstellen von Chats
* Löschen von Chats
* Schreiben von Nachrichten
* Lesen von bereits geschriebenen Nachrichten

## Tests

