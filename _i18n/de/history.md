
## 23. April 2019: HAMNET auf 70-cm und andere Baender - Sachstand

```
Subject: HAMNET auf 70-cm und andere Baender - Sachstand
Date: Tue, 23 Apr 2019 07:21:11 +0200
From: Jann Traschewski <jann@gmx.de>
To: as-koordination@de.ampr.org

Liebe Freunde,

das Thema "HAMNET auf 70-cm" verfolgen wir nun schon einige Jahre und es
bahnen sich langsam Loesungen an. Ich moechte hier kurz ueber die
einzelnen Ideen und deren Fortschritte berichten.

Als Spektrum steht uns in DL seit vielen Jahren der Kanal 439,700 MHz
(Oberband) und 434,900 MHz (Unterband) mit jeweils 200 kHz zur
Verfuegung (4,8 MHz Shift). Angepeilt wird fuer diesen Duplex-Kanal ein
hoeherwertiges Modulationsverfahren, um eine Brutto-Datenrate von bis zu
1 MBit/s (bei sehr gutem Signal-Rauschabstand) zu erzielen. Ausserdem
darf man das stark belegte ISM-Band als Spielwiese fuer Sendearten mit
Bandbreiten bis zu 1,6 MHz betrachten.


1. SDR-basierte Eigenentwicklung (439,700 MHz Basisstation - 434,900 MHz
Teilnehmer)

Grundlegende Gedanken zur Aktivierung der beiden Frequenzen wurden in
einer kleinen Gruppe bereits beleuchtet. Sehr schnell wurde allerdings
klar, dass die zeitlichen Ressourcen der Teilnehmer zur Umsetzung der
Ideen nicht ausreichen wuerden. Chris, DL1COM, und Jann, DG8NGN, haben
sich daher in ihrem QRL erfolgreich nach Moeglichkeiten der
Ausschreibung einer Abschlussarbeit zu dem Thema umgeschaut. Details
dazu werde ich in einer separaten Nachricht zur Suche eines geeigneten
Kandidaten bekanntgeben.


2. LTE mit 1,4 MHz Bandbreite (23-cm Basisstation - 433,920 MHz Teilnehmer)

Von SRS (Software Radio Systems) gibt es auf Github
(http://github.com/srsLTE/srsLTE) den Code fuer eine Basisstation
(eNodeB) mit Unterstuetzung von 1,4 MHz und FDD (Frequency Division
Duplex). Passend dazu auch den Code fuer einen Teilnehmer (UE). Eine
Idee waere es den Downlink der Basisstation zum Teilnehmer auf 23-cm
(~1243 MHz) laufen zu lassen, waehrend der Uplink des Teilnehmers auf
der 70-cm ISM-Mittenfrequenz (433,920 MHz) zur Basisstation sendet.

Mit der Annahme, dass fehlende Signalanteile (ISM-Stoerungen!) des
Teilnehmers sich nur auf die erreichbare Datenrate auswirkt
(OFDM-Modulation), koennte man das beste aus dem ISM-Band herausholen!
Der groesste Aufwand ist an der Basisstation zu erwarten, die eine hohe
Ausgangsleistung benoetigt, um im 23-cm-Band den Teilnehmer auch bei
"non-line-of-sight"-Bedingungen noch zu erreichen. Jeder ist aufgerufen
diese Idee zu evaluieren.


3. Narrowband IoT (Internet-of-Things) LTE (439,700 MHz Basisstation -
434,900 MHz Teilnehmer)

Der "physical layer" von NB-IoT (3GPP Cat. NB1 / NB2) koennte >200
kBit/s transportieren, was zwar unter der angepeilten
Datenuebertragungsrate liegt, aber vielleicht doch einen Blick wert ist.
Im Downlink kommt OFDMA mit 12x 15kHz Traegern zum Einsatz (180 kHz
Bandbreite) und im Uplink SC-FDMA. Die tatsaechliche Nutzdatenrate pro
Teilnehmer liegt aber nochmal deutlich unter dem des "physical layers"
(~25 kbps / DL und ~64 kbps / UL). Das Dokument
https://www.keysight.com/upload/cmc_upload/All/20170612-A4-JianHuaWu-updated.pdf
gibt einen recht guten Einblick.

Von SRS (Software Radio Systems) ist uns eine kommerzielle
Implementierung bekannt, die aber auf Nachfrage von Ralph, DK5RAS, bald
oeffentlich gemacht werden soll. Zitat: "We plan to release our NB-IoT
features within the open-source srsLTE suite this year and it would be
great to see them used by the ham radio community. We don't have a firm
release date set just yet but we'll post all notices to the srslte-users
mailing list as they become available."


4. New Packet Radio by Guillaume, F4HDK

Guillaume, F4HDK, hat mit dem "NPR - New Packet Radio"-Projekt
(https://hackaday.io/project/164092-npr-new-packet-radio) eine sehr gute
Grundlage zur Aktivierung des 70-cm-Bandes geschaffen. Fertig, guenstig
und beschaffbar. Das DARC VHF/UHF/SHF-Referat hat sich 10 Bausaetze
(bereits eingetroffen) und 2 Endstufen (im Zulauf) besorgt und wird
damit erste Erfahrungen sammeln (Danke an Hans, DL8MCG). Zum Einsatz
kommt 2- oder 4-GFSK im Simplex-Betrieb mit Hilfe des RF-Moduls "RF4463
F30" (500mW).

Mit 4GFSK kommt man bei der Uebertragungsrate schnell an seine Grenzen.
Guillaume gibt 360kbps (Raw datarate) und 220kbps (Useful datarate) bei
einer Bandbreite von 270 kHz an. Weitere Bandbreiten bei hoeherer
Datenrate sind 450 kHz und 750 kHz. Auf unsere Rueckfrage hat er
signalisiert, dass bei entsprechenden Bedarf auch eine 200 kHz Variante
laengerfristig entstehen kann.


5. Klassisches IP-over-AX.25

Weiter ist es moeglich ueber das altbekannte Packet Radio Netz mit
IP-over-AX.25 in das HAMNET einzusteigen. Als Bindeglied dient der
IGATE-Knoten (AX.25-Call = IGATE SSID = 0). Verbindet man sich mit dem
Knoten per AX.25 und gibt "getip" ein, so wird fuer das Rufzeichen eine
IP-Adresse aus dem IP-Pool 44.130.254.128/25 fuer 40 Tage (57600
Minuten) reserviert und ausgegeben. Traegt man diese IP-Adresse in
seinen TCP/IP-Stack ein und benutzt IGATE als ARP, so kann eine
(langsame) Verbindung mit dem HAMNET aufnehmen.


6. D-Star DD (Digital Data)

ICOM hat neben dem D-Star Digital Voice System auch eine Implementierung
fuer digitale Daten (D-Star DD) in Kooperation mit der JARL entwickelt.
Fuer D-Star DD gibt es von ICOM einen Einschub fuer ein ICOM-Relais und
auf Nutzerseite (es funktioniert auch Peer-to-Peer) den ICOM ID-1. Beide
Geraete arbeiten im 23-cm-Band mit 150 kHz Bandbreite und einer
Datenuebertragungsrate von 128 kbps (brutto).

Hansi, DL9RDZ, Michael, DK5HH, und Jann, DG8NGN, haben vor laengerer
Zeit mit Gnuradio an einer "open source"-Variante fuer D-Star DD
gearbeitet. Erfolgreich getestet wurde der Code von einem Ettus B210 zu
einem ICOM-ID1 (bidirektional) und RX-Only von ICOM-ID1 und Einschub am
Relais auf einen Ettus B210 und einem RTL-SDR-Stick. Der Code wurde
bisher nicht veroeffentlicht, da noch vereinzelnd Paketverluste
auftreten. Nachdem sich das Projekt aktuell nicht weiterbewegt werden
wir den aktuellen Stand veroeffentlichen.

Eine interessante Idee waere es D-Star DD im "Downlink" vom Knoten zum
User (RTL-Stick) und den "Uplink" ueber klassisches IP-over-AX.25 zu
realisieren ("schneller Downlink", "langsamer Uplink").


7. HRD70-Projekt (http://www.hrd70.com)

Vom HRD70-Projekt (Ham Radio Data for 70cm) gab es zur Hamradio 2017 ein
Interview (https://www.youtube.com/watch?v=12E5bB_ME9I) und auf der
Amateurfunktagung 2018 in Muenchen ein Vortrag
(https://media.ccc.de/v/afu-tm18-1008-hrd70_high_speed_70_cm_daten_transceiver_fuer_hamnet).
Auf der Amateurfunktagung wurde angekuendigt, dass der Source Code bei
Fertigstellung des Projekts publiziert wird. Uns ist keine Neuigkeit zu
dem Projekt bekannt.


73,
Jann
DG8NGN
```

## 14. November 2019: HAMNET-Zugang auf 70-cm – Automatische Stationen

```
Subject: HAMNET-Zugang auf 70-cm – Automatische Stationen
Date: Thu, 14 Nov 2019 10:24:41 +0100
From: Jann Traschewski <jann@gmx.de>
To: as-koordination@de.ampr.org

Liebe HAMNET-Community,

die Bemühungen zur Aktivierung des Breitbandkanals 439,700 MHz
(Oberband) und 434,900 MHz (Unterband) mit jeweils 200 kHz Bandbreite
für den Einstieg ins HAMNET tragen langsam Früchte.

Guillaume, F4HDK, hat mit seinem Projekt „NPR – New Packet Radio“
(https://hackaday.io/project/164092-npr-new-packet-radio) eine erste
Lösung für den Einstieg ins HAMNET auf 70-cm entwickelt. Das DARC
VHF/UHF/SHF-Referat hat in den letzten Monaten eng mit Guillaume bzgl.
unserer Systemanforderungen zum Einsatz an automatisch arbeitenden
Stationen (200 kHz Bandbreite + getrennte Sende-/Empfangsfrequenz)
zusammengearbeitet. Diese werden mit der neuesten Beta-Firmware vom
20.10.2019 erfüllt. Das System wurde auf den Zielfrequenzen letzte Woche
an einem HAMNET-Knoten mit drei aktiven Clients erfolgreich getestet.

Für den Einsatz von NPR an automatisch arbeitenden Stationen bedarf es
in Deutschland wie üblich einer Genehmigung nach §13 der
Amateurfunkverordnung. Das DARC VHF/UHF/SHF-Referat hat die
Rahmenparameter zur Nutzung von NPR auf 439,700 MHz und 434,900 MHz mit
der Bundesnetzagentur diskutiert und abgestimmt. Wir werden dabei auf
den Einsatz von Schutzzonen (ähnlich wie bei APRS 144,8 MHz) verzichten,
was sicher weiterer Erläuterungen bedarf:

Obwohl wir in Deutschland das gesamte 10 MHz Spektrum des 70-cm
Amateurfunkbandes für unsere Anwendungen nutzen können, stehen uns
aktuell für den Einstieg ins HAMNET an automatisch arbeitenden Stationen
nur die Frequenzen 439,700 MHz (+/- 100 kHz) und 434,900 MHz (+/- 100
kHz) zur Verfügung. Auch wenn der Betrieb in simplex mit zwei Frequenzen
attraktiv erscheint, so spricht doch einiges für den Betrieb in duplex.

Zum einen möchte man ein System zum Einstieg ins HAMNET an typischen
HAMNET-Knoten einsetzen. Dort befindet sich aber in der Regel bereits
Bestandsinfrastruktur in Form von 70-cm Anwendungen (Relaisfunkstellen
oder/und Funkruf), welche im Oberband (438-440) senden und im Unterband
(430-432) empfangen. In den meisten Fällen ist es daher schwierig eine
ausreichende HF-Entkopplung zu realisieren (434,900 MHz HAMNET-TX
schwierig vom Relais-RX zu entkoppeln und 439,700 MHz HAMNET-RX noch
viel schwieriger vom Relais-TX bzw. POCSAG zu entkoppeln).

Zum anderen erwarten wir eine hohe Dichte von HAMNET 70-cm
Einstiegspunkten, die sich im Simplex-Betrieb häufig gegenseitig hören
würden (HAMNET-Knoten haben in der Regel gute Standorte und oft freie
Sicht zueinander). Die Zielgruppe der HAMNET 70-cm Nutzer sind aber
genau diese, welche aufgrund der fehlenden Sichtverbindung zum
HAMNET-Knoten (in der Regel nutzt man bei bestehender Sicht das 13-cm-
oder 6-cm-Band) auch nicht die stärksten Signale abliefern werden. Durch
den Einsatz beider Frequenzen werden HAMNET-Knoten die Aussendungen der
Nutzer nicht beeinträchtigen.

Ein vollduplexfähiger HAMNET-Knoten bietet auch die Chance, den
Datenfluss vom Knoten zum Nutzer zu optimieren. Während der
HAMNET-Knoten an einen typischerweise halbduplexfähigen Nutzer sendet,
kann zeitgleich ein anderer Nutzer Daten zum HAMNET-Knoten abliefern. Im
Oberband kann der HAMNET-Knoten permanent getastet bleiben, so dass
keine Übertragungsgeschwindigkeitseinbußen durch Umschaltzeiten
entstehen. NPR ist aktuell in der „Master“-Version (HAMNET-Knoten) nur
halbduplexfähig (Vollduplexfähigkeit ist in Vorbereitung).

Nachdem wir nur einen Duplex-Kanal für den Einstieg ins HAMNET auf 70-cm
haben, ist davon auszugehen, dass beim Einsatz von Schutzzonen einige
Standorte nicht aktiviert werden könnten. Interessen und Möglichkeiten
der Funkamateure sind im permanenten Wandel, aber das „First Come –
First Served“-Prinzip bei der Ausstellung von Genehmigungen durch die
Bundesnetzagentur gepaart mit den nachvollziehbaren „Hortungsverhalten“
der verantwortlichen Funkamateure von automatisch arbeitenden Stationen
resultiert in einer stark reduzierten Flexibilität und ineffizienter
Frequenznutzung innerhalb unseres Experimentalfunkdienstes.

Wir setzen bei der Abkehr von Schutzzonen darauf, dass die Community im
Eigeninteresse die Umsetzung von HAMNET-Einstiegen im 70-cm-Band
optimiert und fordern (besonders im Kollisionsfall) von den Nutzern den
Einsatz von Richtantennen ein, um die Beeinflussung auf ein Minimum zu
reduzieren. Vom Nutzer ist die Ausgangsleistung so zu begrenzen, dass
der HAMNET-Knoten die ausgesendeten Pakete (auch bei Fading) gerade noch
zuverlässig dekodieren kann. Bei der HAMNET-70-cm-Planung innerhalb
einer Region können die Betreiber von HAMNET-Knoten durch geeignete Wahl
der Antennenpolarisation für eine bessere Entkopplung  an den Rändern
des Versorgungsbereiches einzelner Standorte sorgen.

Zuletzt möchten wir noch darauf hinweisen, dass langfristig bei der
Bundesnetzagentur die Gebühren für die Koordinierung von automatisch
arbeitenden Stationen aufwendungsbezogen in Rechnung gestellt werden
(derzeit haben wir noch die einmalige Gebühr von 200,- € pro Station mit
anschließender Änderungs-„Flatrate“). Ohne Schutzzonen gibt es keine
Koordinierung und damit keine Gebühren für die Koordinierung.

Der Einstieg ins HAMNET war bisher in vielen Fällen mangels direkter
Sicht nicht möglich. Mit der Aktivierung von HAMNET im 70-cm-Band soll
diese Lücke geschlossen und möglichst vielen OMs und YLs der Einstieg
ermöglicht werden.

Beantragung eines HAMNET-Einstiegs im 70-cm-Band:
Das digital ausfüllbare Formular der Bundesnetzagentur kann auf den
Seiten des DARC VHF/UHF/SHF-Referats heruntergeladen werden:
https://www.darc.de/der-club/referate/vus/automatische-stationen/#c33304
(Antrag auf eine Rufzeichenzuteilung zum Betrieb einer Amateurfunkstelle
gemäß § 13 Abs. 1 AFuV)

Der Antrag wird wie folgt ausgefüllt:
Betriebszweck:			HAMNET-Digi
Sendefrequenz MHz:		439,7
Empfangsfrequenz MHz:		434,9
Kanal:				leer lassen
Strahlungsleistung ERP in dBW:	11,76 (maximal)
Sendeart:			F1D
Bandbreite kHz:			200
Datenrate kBit/s		200
Sendeantenne Pol:		H oder V
Radius Versorgungsgebiet:	je nach Schätzung
Nutzungszeit:			1

Bestands-Genehmigungen:
Es gibt noch Hand voll Bestands-Genehmigungen für AX.25 basierte
Packet-Radio Nutzereinstiege mit 76800 Baud (in der Regel mit
„horizontaler Polarisation“, „76800 Baud“ und „Digi“ genehmigt). Soll
die Genehmigung von „Digi“ zu „HAMNET-Digi“ zur Nutzung mit NPR
umgeschrieben werden, so reicht ein kurzer Hinweis an die
Bundesnetzagentur (der Betrieb kann daraufhin sofort erfolgen). Dies
wird bei der BNetzA vermerkt und bei der nächsten Verlängerung der
Genehmigung gleich passend als „HAMNET-Digi“ ausgestellt.

Hinweise zur Einbindung an einem HAMNET-Knoten:
Das Modem kann in die bestehende User-Bridge vom HAMNET-Knoten mit
eingebunden werden. Langfristig plant die IP-Koordination DL spezielle
IP-Ressourcen fuer NPR bereit zu stellen (damit man bereits an der
IP-Adresse erkennt, ob einem Teilnehmer nur wenig Bandbreite zur
Verfuegung steht – vgl. 44.130.32.0/19 für Packet Radio).

Zu guter Letzt noch ein Dankeschön an Martin, DL4ZX (ex-DL2ZBN), und
Alexander, DL8AAU, die damals mit ihrem Projekt „70cm BreitbandTRX“
(http://www.liebeck.de/70_breit/70cm_him.htm) das Frequenzpaar für
Breitbandanwendungen im Bandplan gesichert haben. Der Dank gebührt
ebenso allen Mitgliedern des damaligen DARC VHF/UHF/SHF-Referats, die
uns das Spektrum für diese Anwendung erkämpft haben.

Vielen Dank auch an unser zuständiges Vorstandsmitglied (Christian,
DL3MBG), welches die ungeplanten zusätzlichen Kosten der Evaluierung und
Aufbereitung von NPR unkompliziert geregelt hat.

Wir wünschen allen OMs und YLs viel Erfolg beim Einstieg ins HAMNET auf
70-cm!
für das DARC VHF/UHF/SHF-Referat,
Jann Traschewski,
DG8NGN
DARC VHF/UHF/SHF-Referent
```