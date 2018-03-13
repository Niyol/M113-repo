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












