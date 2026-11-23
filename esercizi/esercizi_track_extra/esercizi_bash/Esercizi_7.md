EXTENDED REGEX: Utilizzare il comando egrep per risolvere i seguenti esercizi (dando esempi di possibili input):
- 1\)Matchare sequenze alfabetiche di almeno un carattere, sia maiuscole 
che minuscole 
- 2\)Togliere tutte le righe di commento di uno script Bash matchando le 
righe che iniziano con '#'
- 3\)Matchare in un file le righe che contengono sequenze di 'a' ripetute 
da 3 a 6 volte
- 4\)Matchare in un file tutte le righe che contengono una delle seguenti 
parole: apple, pear, orange

```
1\)fil di input: file1regex.txt
HelloWorld
abcXYZ
qwertyuiopASDFGHJKL
MaIuScOlEmInUsCoLe
ciao723
123_456!!#@
ciao!
ciao_mondo
ciao-mondo
3ciao
c1ao
user@mail
A.B
OK
```
`grep -iE '[a-z]+' file1regex.txt`
`grep -iEv '[a-z]+' file1regex.txt` mi mostra quello che non ho preso 
ovvero `123_456!!#@` percui il comando richiesto prende tutto tranne 
questa riga.
ho usato il -i per questo caso, ma se avessi avuto necessità di cercare 
altro come per esempio: `O[a-zA-Z]+` quindi un qualcosa con la O è 
importante non mettere il flag -i. 

2\)come input ho usato lo stesso file. dato che mancono i commenti #, ho 
fatto con sed prima l'aggiunta del commento #
`sed -i 's/^/#/' file1regex.txt` in questo modo ho aggiunto a tutte le 
righe il commento
comando per eliminare le righe con il commento #

`sed '/^#/d' file1regex.txt`

3\)Generato un file gi input chiamato file3aaa.txt
```
Il gatto fece miaaao e scappò in giardino.
La casa ha una sala molto grande.
Che caaaaldo oggi, mamma mia!
Abbiamo scritto aa sulla lavagna.
Urlava maaaaaaaaah senza mai fermarsi.
Uffa, aaaaaa che noia questa lezione!
Le lettere a a a a sono separate da spazi.
banaaaana
```
`grep -E '\<[^a]*a{3,6}[^a]*\>' file3aaa.txt`
inizialmente avevo usato questo come regex, ma la presenza di una singola 'a' prima o dopo del 
range,come per esempio in banaaaana che non lo avrebbe reso valido. 
perui mi sono limitato a considerare solo gli estremi ma nelle diverse 
possibilità sfruttando il raggruppamento ()e la pipe |

`grep -E (\<|[^a])a{3,6}([^a]|\>) file3aaa.txt` 
così da definire gli estremi intorno alla sequenza a{3,6}



4\) file frutta.txt
```
apple,banana,strawberry
pear,peach,lemon
banana,kiwi,orange
grape,melon,cherry
pineapple,mango,kiwi
Apple,PEAR,Orange
lemon, apple ,lime
pears,oranges,plum
applepear,melon,fig
peach,apricot,banana
```  
`grep -Ew 'apple|pear|orange' frutta.txt`
output:
```
apple,banana,strawberry
pear,peach,lemon
banana,kiwi,orange
lemon, apple ,lime
```
in questo modo non mi prende parole come applepear o pears
