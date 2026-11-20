AWK: Scrivere un programma AWK che prende in input un file .csv e stampa il terzo campo solo se viene matchata la stringa "banana".
File di input di esempio:
```
apple,banana,strawberry
pear,peach,lemon
banana,kiwi,orange
```
Output desiderato:
```
strawberry
orange
```
`frutta_awk.sh`

```
#!/bin/bash
if [[ "$#" -ne 1 || ! -f "$1" ]] ; then
	echo "inserire un solo argomento come file"
	exit 1
elif [[ "$1" = *.csv ]]; then 
	awk -F, '/banana/ {print $3}' "$1"
else
	echo "il file in argomento non è .csv"
	exit 2
fi
```
