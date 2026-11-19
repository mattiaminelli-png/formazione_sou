Scrivere uno script che accetti un argomento numerico e stampi la sequenze di numeri 
da 1 a quel numero con l'indicazione se è pari o dispari. 
Controllare il corretto numero di argomenti passati allo script e che l'argomento sia di tipo numerico, 
in caso contrario generare una condizione di errore.

```
#!/bin/bash

if [[ "$#" -ne 1 ]]; then
	echo "Hai inserito $# numeri, il massimo consentito è uno"
	exit 1
fi

n=1
if [[ "$1" =~ ^[1-9][0-9]*$ ]]; then
	while [[ n -le "$1" ]]; do
		if ((  n % 2 == 0 )); then
			echo "$n è pari"
		else
			echo "$n è dispari"
		fi
	((n++))
	done
else
	echo "il valore inserito non è un numero intero positivo"
	exit 2
fi

```
