# Pyrat - HackMyVM (Medium)

![Pyrat.png](Pyrat.png)

## Übersicht

*   **VM:** Pyrat
*   **Plattform:** HackMyVM (https://hackmyvm.eu/machines/machine.php?vm=Pyrat)
*   **Schwierigkeit:** Medium
*   **Autor der VM:** DarkSpirit
*   **Datum des Writeups:** 29. April 2024
*   **Original-Writeup:** https://alientec1908.github.io/Pyrat_HackMyVM_Medium/
*   **Autor:** Ben C.

## Kurzbeschreibung

Das Ziel dieser Challenge war es, die User- und Root-Flags der Maschine "Pyrat" zu erlangen. Die initiale Reconnaissance offenbarte einen SSH-Dienst auf Port 22 und einen Python SimpleHTTPServer auf dem ungewöhnlichen Port 8000. Ein Hinweis am Ende des Original-Writeups deutete auf Verbindungsprobleme mit dem Dienst auf Port 8000 hin und empfahl eine "einfache Verbindung". Der detaillierte Weg zum Initial Access und zur Privilegieneskalation war im bereitgestellten Log nicht dokumentiert.

## Disclaimer / Wichtiger Hinweis

Die in diesem Writeup beschriebenen Techniken und Werkzeuge dienen ausschließlich zu Bildungszwecken im Rahmen von legalen Capture-The-Flag (CTF)-Wettbewerben und Penetrationstests auf Systemen, für die eine ausdrückliche Genehmigung vorliegt. Die Anwendung dieser Methoden auf Systeme ohne Erlaubnis ist illegal. Der Autor übernimmt keine Verantwortung für missbräuchliche Verwendung der hier geteilten Informationen. Handeln Sie stets ethisch und verantwortungsbewusst.

## Verwendete Tools

*   `arp-scan`
*   `nmap`
*   *Weitere Tools für Initial Access und Privilegieneskalation wurden im Log nicht gezeigt.*

## Lösungsweg (Zusammenfassung)

Der Angriff auf die Maschine "Pyrat" gliederte sich in folgende Phasen:

1.  **Reconnaissance:**
    *   IP-Adresse des Ziels (192.168.2.111) mit `arp-scan` identifiziert. Hostname `pyrat.hmv` in `/etc/hosts` eingetragen.
    *   `nmap`-Scan offenbarte Port 22 (SSH, OpenSSH 8.2p1 Ubuntu) und Port 8000 (http-alt, Python 3.11.2 SimpleHTTPServer).
    *   Der Dienst auf Port 8000 zeigte keinen Titel und Nmap hatte Schwierigkeiten bei der genauen Dienstidentifikation.

2.  **Enumeration, Initial Access & Privilege Escalation (nicht im Log detailliert):**
    *   Der bereitgestellte Log endet nach dem Nmap-Scan.
    *   Ein Hinweis im Original-Writeup deutet auf Verbindungsprobleme mit Port 8000 und die Notwendigkeit einer "einfachen Verbindung" hin.
    *   Die weiteren Schritte zur Erlangung des initialen Zugriffs und der Eskalation zu Root waren im Log nicht dokumentiert.

3.  **Flags (aus dem Bericht entnommen, Weg nicht dokumentiert):**
    *   User-Flag: `996bdb1f619a68361417cabca5454705`
    *   Root-Flag: `ba5ed03e9e74bb98054438480165e221`

## Wichtige Schwachstellen und Konzepte (basierend auf den initialen Funden)

*   **Dienste auf Nicht-Standard-Ports:** Der Python SimpleHTTPServer lief auf dem ungewöhnlichen Port 8000.
*   **Potenziell instabiler oder fehlkonfigurierter Dienst:** Der Hinweis auf Verbindungsprobleme und die Fingerprint-Fehler bei Nmap für Port 8000 deuten auf einen unüblichen oder instabilen Dienst hin.
*   *(Nicht dokumentiert)* Die tatsächlichen Schwachstellen, die zum Initial Access und zur Privilegieneskalation führten, sind aus dem Log nicht ersichtlich.

## Flags

*   **User Flag:** `996bdb1f619a68361417cabca5454705`
*   **Root Flag:** `ba5ed03e9e74bb98054438480165e221`

## Tags

`HackMyVM`, `Pyrat`, `Medium`, `Python SimpleHTTPServer`, `SSH`, `Linux`
