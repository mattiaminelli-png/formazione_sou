Supponiamo che abbiamo un file csv con i vostri dati
nome,cognome,numero
bisogna estrarre la colonna cognome. La prima lettera deve diventare 
sempre maiuscola, selezionare solo due cognomi

`anagrafica.csv`

```
nome,cognome,telefono,età,email
mattia,minelli,4234542q2,29,matmin@gmail.com
noemi,presta,48857438,30,noepres@gmail.com
vincenzo,abete,33949858,28,vincabet@gmail.com
bernard,ramohitaj,334858676,26,bernard@gmail.com
domenico,nasso,33234555y,26,domnas@gmail.com
viron,daiu,3433456776,27,viro@gmail.com
giulio,romano de mattia,334556,25,giulio@gmail.com

```
```
awk -F, '{ print $2 }' anagrafica.csv | sed 's/\<./\U&/g' | egrep -i 
"minelli|romano de mattia"
``` 
