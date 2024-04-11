# homeassistant-zendure-hoymiles
Nulleinspeisung umgesetzt mit Homeassistant (Zendure &amp; Hoymiles) über MQTT

Vorbereitung:
- Zendure an HA über MQTT angebunden -> https://github.com/z-master42/solarflow/blob/main/README.md
- Hoymiles an HA über MQTT (Ahoy DTU) angebunden -> https://github.com/lumapu/ahoy/tree/main?tab=readme-ov-file
- Messstelle zum erfassen der Verbrauchsdaten (bei mir Discovergy)

Umsetzung:
Mein Script läuft alle 15 minuten und prüft den aktuellen Verbrauch und die Produktion. Desweiteren berücksichtige ich den aktuellen Stand meiner Batterie. Ziel ist es sicherzustellen das die Batterie mindestens 50% geladen ist. Bis 50% drossel ich die Einspeisung ins Hausnetz auf meinen Grundverbrauch, darüber gleiche ich die Einspeisung an meinen Hausverbrauch an.

Leider lässt sich Zendure - noch - nur über die APP ansteuern, daher habe ich hier Terminmodus eingestellt im Zeitfenster von 06:00 - 20:00 Uhr (besser wäre hier auch Sonnenauf - und untergang) werden der max output (bei mir 800W) ansonsten auf meinen Grundverbrauch (bei mir 140W) gedrosselt.

Hinweise:
- script.yaml -> mein Script, das sollte in der automatiesierung beim starten des Homeassistant eingeschlatet werden. Ich habe hier zusätzlich noch eingebaut das, das script nach sonnenuntergang beendet wird und zum sonnenaufgang gestartet
- hoymiles.yaml -> meine integration in den Homeassistant, entweder alles in die configuration.yaml (copy/paste) oder diese datei ablegen und in der configuration.yaml am Anfang noch einfügen mqtt: !include hoymiles.yaml
