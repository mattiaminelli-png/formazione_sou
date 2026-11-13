1\) CASI DI ERRORE CON TOUCH
ho ottenuto due tipi di errore con touch:
- primo caso: ho creato una cartella e rimosso i permessi di scrittura -w con chmod. in questo caso non posso fare il touch
- secondo caso: il flag -t permette di cambiare le informazioni riguardante il tempo, quindi l'anno, il mese,il giorno,l'ora,minuti e secondi, se sbaglio a scrivere il formato mi genera errore indicando formato di data non valido. ho messo solo anno e mese e mi ha dato errore.
```
[mattia723@localhost ~]$ touch prova/file.txt
touch: impossibile fare touch di 'prova/file.txt': Permesso negato

[mattia723@localhost ~]$ ls -lahrt
totale 72K
dr-xr-xr-x. 2 mattia723 mattia723    6  2 nov 17.19   prova
```

```
[mattia723@localhost ~]$ touch -t 202605 file.txt 
touch: formato di data "202605" non valido
```
