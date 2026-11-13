3)ho preso l'ultima riga ottenuta dall' interrogazione dell' rpm il quale mi riportava le versioni del kernel linux attualmente installate sul mio sistema e confrontata con la versione del kernel attualmente in uso (uname -r). 
```
prova2=$(rpm -q kernel | tail -n 1 | sed 's/^kernel-//');

prova3=$(uname -r);

  

echo $prova2;

echo $prova3;

if [[ "$prova2" == "$prova3" ]]; then

        echo "ho in uso l'ultimo kernel scaricato"

        echo "$prova2"

else

        echo "non ho in uso l'ultima versione installata"

        echo "$prova3"

fi

```
