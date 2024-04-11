# homeassistant-zendure-hoymiles
Nulleinspeisung umgesetzt mit Homeassistant (Zendure &amp; Hoymiles) über MQTT

Vorbereitung:
- Zendure an HA über MQTT angebunden ->
- Hoymiles an HA über MQTT (Ahoy DTU) angebunden ->
- Messstelle zum erfassen der Verbrausdaten (bei mir Discovergy)

Umsetzung:
Mein Script läuft alle 15 minuten und prüft den aktuellen Verbrauch und die Produktion. Desweiteren berücksichtige ich den aktuellen Stand meiner Battery. Ziel ist es sicherzustellen das die battery mindestens 50% geladen ist. Bis 50% drossel ich die Einspeisung ins Hausnetz auf meinen Grundverbrauch, darüber gleiche ich die Einspeisung an meinen Hausverbrauch an.

Leider lässt sich Zendure - noch - nur über die APP ansteuern, daher habe ich hier Terminmodus eingestellt im zeitfenster von 06:00 - 20:00 Uhr (besser wäre hier auch Sonnenauf - und untergang) werden der max output (bei mir 800W) ansonsten auf meinen Grundverbrauch (bei mir 140W) gedrosselt.

