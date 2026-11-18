1) finalità di questo script è scrivere un ciclo for che mi permetta di numerare gli argomenti che vengono dati in input
e alla fine ne stampa il totale:

```
#!/bin/bash

n="0"
for x in "$@"
do
	n=$((n + 1))
	echo "$n: $x" 
done 
echo "Totale: $n argomenti"
#posso scrivere anche $# argomenti
```
posso ottenere il contatore anche in altro modo:
`((n++))`
`n+=1`

2)script che accetta dei path come input e mi indica che tipo è per ognuno.
controlla.sh
```
#!/bin/bash
for x in "$@"
do
	if [[ -f "$x" ]]; then 
		echo "$x: file regolare"
	elif [[ -d "$x" ]]; then 
		echo "$x: directory"
	elif [[ ! -e "$x" ]]; then
		echo "$x: non esiste"
	else
		echo "$x: esiste, altro tipo di file"
	fi
done
```
aggiornato il codice poichè se non avessi messo niente non mi dava nessun output. mentre in questo modo ho aggiunto un controllo.
controlla.sh
```
#!/bin/bash
if [[ "$#" -eq 0 ]]; then
    echo "Uso: controlla.sh <percorso1> <persorso2> ..."
    exit 1
fi

for x in "$@"
do
    if [[ -f "$x" ]]; then 
        echo "$x: file regolare"
    elif [[ -d "$x" ]]; then 
        echo "$x: directory"
    elif [[ ! -e "$x" ]]; then
        echo "$x: non esiste"
    else
        echo "$x: esiste, altro tipo di file"
    fi
done
```
3)script che chiede il nome dell'utente e controlla se già presente nel filesystem 

```
#!/bin/bash

read -p "Nome utente: " nome

if [[ -z "$nome" ]]; then
	echo "nessun nome inserito"
	exit 2
elif grep -q "^$nome:" /etc/passwd; then
	echo "l'utente $nome esiste"
else
	echo "l'utente $nome non esiste"
	exit 1
fi

```
in questo modo con -q non mando a schermo anche l'output anche se magari potrebbe essere utile per vedere se per caso mi prende utenti in modo involontario. però in questo già aver messo i ":" aiuta perchè l'output di quel comando mi trova diversi campi separati dai : quindi indica la terminazione. senza i due punto avrei riscontrato ambiguità poichè mi avrebbe potuto prendere es. mattia: ma anche mattia124: io voglio sapere se già presente l'utente che digito e non altri
variante più solida è considerando il comando id

```
#!/bin/bash
#inserisco un argomento da cli

if [[ "$#" -eq 0 ]]; then
        echo "Uso: utente.sh <nome_utente>" >&2
        exit 2

elif id "$1" > /dev/null 2>&1 ; then 
        echo "l'utente $1 esiste"
else
    	echo "l'utente $1 non esiste" 
        exit 1
fi
```
in questo caso nell'elif non potendo usare come per grep -q. ho ridirezionato lo stdout all'interno del file /dev/null e lo stderror anche con il comando 2>&1 ovvero stderror 2 ridirezionato nello stesso canale dello stdoutput 1, quindi nello stdout
potrei riscriverlo anche con il read, semplicemente ho usato questo per cambiare modo.
in questi script ho messo l'exit perchè altrimenti l'ultimo comando è un echo percui sarebbe sempre exit status 0. in questo modo posso capire dove sta l'errore.

