Per quanto riguarda l'esercizio 1 la cui traccia era: Creare un file in /tmp e chiamarlo app.log
Mettersi in tail su questo file e al tempo stesso iniziare a direzionare dell’output all’interno del file con questa dicitura:
“ Error: descrizione errore”,
“ Info: descrizione info”
vedere cosa succede al file in tail.
Aggiungere almeno 2 righe di ogni tipologia di messaggio
Una volta terminato di direzionare l’output e accertatosi che il file non sia vuoti, eseguire tramite il comando grep la ricerca degli errori contenuti  nel file
Risultato:

![[Screenshot 2026-11-03 alle 16.07.45.png|700]]ho creato uno script 'errore.sh' con all'interno un ciclo for andando ad aggiungere per 3 volte le due diciture intervallate con tempi diversi usando sleep; ridirezionato il tutto all'interno del file.txt. Per eseguire lo script ho usato ./errore.sh dopo aver aggiunto con chmod +x errore.sh il permesso di esecuzione. Il risultato  l'ho osservato con `tail -f file.txt`. poi ho preso le frasi contenenti error attraverso il comando `grep -w "error" file.txt` con -w sono stato solo più selettivo. 
in questo mi è stato consigliato di aggiungere -i così da renderlo caseinsensitive .

script.sh
``` 
#!/bin/bash

for i in {1..3};

do 

echo "error:descrizione errore" >> file.txt;

sleep 3;

echo "info:descrizione info" >> file.txt;

sleep 2

done
```
