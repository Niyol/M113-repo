# Documentation for the server 
## Anpassung : blog_server.raw
- Eine initiale Untersuchung mittels Testdisk zeigt eine Fehlermeldung -> "Bad relative sector".
- Laut sudo parted blog_server.raw unit s print ist die Partitiontabelle beschädigt, indem die Länge der Partition größer als der Datenträger ist.
- Eine neue größe wird berechnet:
  - New_End =  5242880 – 1 = 5242879
  - New_Size = new end – start + 1 > 5242879 – 2048 + 1 = 5240832
- Mittels sudo sfdisk -d blog_server.raw > bkup.txt wird die Partitiontabelle aus der Image extrahiert.
- Nachdem sie vom Hand geändert wird, wird sie mittels sudo sfdisk  blog_server.raw < bkup.txt in die Image nochmal kopiert.
- sudo parted blog_server.raw unit s print zeigt jetzt keine Fehlermeldungen
## Flatpress
### Anmeldedaten
/img_blog_server.raw/vol_vol2/var/www/1/fp-content/users/admin.php   
- 'userid' => 'admin',  
- 'password' => '6a0a3033f490014f6b61c2c476f63637',  
- 'www' => 'http://localhost.net/',  
- 'email' => 'myflatpress@localhost.net',
### Erster Kommentar
/img_blog_server.raw/vol_vol2/var/www/1/fp-content/content/15/08/entry150828-140229.txtVERSION|fp-1.0.3|SUBJECT|Mein erster Blog|CONTENT|Jetzt habe ich endlich auch einen Blog :). |AUTHOR|admin|DATE|1440770549|

## Supermario.exe
- Supermario.exe wurde von folgenden IP Adressen heruntergeladen (Auszug von vhost1.myflatpressserver.de_access.log) :
  - 192.168.178.101 - - [28/Aug/2015:12:15:37 +0000] "GET /supermario.exe HTTP/1.1" 200 143872 "http://vhost1.myflatpressserver.de/" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0)
  - 192.168.178.102 - - [28/Aug/2015:12:19:13 +0000] "GET /supermario.exe HTTP/1.1" 200 143872 "http://vhost1.myflatpressserver.de/" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0)"

## File Carving
... Ermitlungen laufen noch...

- 39876 Dateien werden mittels PhotoRec gefunden.
- Manche Dateien sind auch mit dem selben Trojaner infiziert andere Dateien zeigen einen Log.

Wed Mar 21 18:43:46 2018Command line: PhotoRec /log /d I:\blog_server I:\blog_server.raw
Elapsed time 0h02m11sPass 1 +39876 filestxt: 24340/24340 recovered
- gz: 5169/5169 recoveredpyc: 3052/3052 recovered
- elf: 2927/2933 recovered
- tx?: 2834/2834 recovered
- tz: 757/757 recovered
- png: 453/453 recovered
- gif: 193/193 recovered
- a: 40/40 recovered
- ps: 36/36 recovered
- ttf: 22/22 recovered
- jpg: 20/20 recovered
- exe: 11/11 recovered
- ico: 10/11 recovered
- zip: 5/5 recovered
- gpg: 3/3 recovered
- class: 1/1 recovered
- bz2: 1/1 recovered
- dwg: 1/1 recovered
- dat: 1/1 recovered
- iso: 0/1 recovered
- Total: 39876 files found

## (Mögliche) Urheberrechtsverletzung
Die angebotene "supermario.exe" Datei enthält einen Trojaner. Vtl. wird das Computerspiel referenziert, um den Besucher dieses Blogs zu überzeugen, die .exe Datei herunterzulande und abzuspielen. 
/var/www/1/index.php
- Download new Super Mario Emulator
- Der Link zeigt eine Abbildung des bekannten Computerspiels : http://media2.giga.de/2010/12/New_Super_Mario_Bros.jpg
