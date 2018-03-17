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
/img_blog_server.raw/vol_vol2/var/www/1/fp-content/users/admin.php   
- 'userid' => 'admin',  
- 'password' => '6a0a3033f490014f6b61c2c476f63637',  
- 'www' => 'http://localhost.net/',  
- 'email' => 'myflatpress@localhost.net',

## Supermario.exe
- Supermario.exe wurde von folgenden IP Adressen heruntergeladen (Auszug von vhost1.myflatpressserver.de_access.log) :
  - 192.168.178.101 - - [28/Aug/2015:12:15:37 +0000] "GET /supermario.exe HTTP/1.1" 200 143872 "http://vhost1.myflatpressserver.de/" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0)
  - 192.168.178.102 - - [28/Aug/2015:12:19:13 +0000] "GET /supermario.exe HTTP/1.1" 200 143872 "http://vhost1.myflatpressserver.de/" "Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; Trident/4.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0)"












