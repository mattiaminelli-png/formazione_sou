2\) Supponiamo di aver committato un file su un branch Git e tale commit 
non sia l'ultima. Trovare il rimuovere tale file non solo dal nostro 
branch, ma anche dall'intera history delle commit.

```
git filter-branch -f --index-filter 'git rm --ignore-unmatch --cached 
provo_conflitto.md' -- prova_1
```
ìnizialmente avevo creato questo branch con un file aggiunto nella stessa 
cartella del README.md

```
* 04b8afe (origin/develop, test, develop) svolgimento dell'esercizio 1 Git 
della track extra con aggiunta della relativa cartella
| *   25b458b (origin/prova_2, prova_2) commit per il merge
| |\  
| | * 83fc75f (HEAD -> prova1_1, origin/prova_1, prova_1) modifica fatta 
anche nel primo branch così da creare conflitto poichè entrambi i branch 
hanno modificato il file originale
| | * 11cdbb3 aggiunta di un secondo file che mancherà nell'altro branch
| * | 32676d4 ho modificato il file in modo diverso anche da github per 
gestire le modifiche con il commit
| |/  
| * 744d395 aggiunta della cartella per gli esercizi git e del file per 
creare conflitto
| * 2261c4a aggiunta di un file nella cartella principale
|/  
* fdd080f (origin/main, main) eseguito anche l'esercizio 7.4
* 39f5fb9 svolgimento dell'esercizio 7
 
```
era nel commit 2261c4a

```
* 04b8afe (HEAD -> test, origin/test, origin/develop, develop) svolgimento 
dell'esercizio 1 Git della track extra con aggiunta della relativa 
cartella
| *   25b458b (origin/prova_2, prova_2) commit per il merge
| |\  
| | * 83fc75f (origin/prova_1) modifica fatta anche nel primo branch così 
da creare conflitto poichè entrambi i branch hanno modificato il file 
originale
| | * 11cdbb3 aggiunta di un secondo file che mancherà nell'altro branch
| * | 32676d4 ho modificato il file in modo diverso anche da github per 
gestire le modifiche con il commit
| |/  
| * 744d395 aggiunta della cartella per gli esercizi git e del file per 
creare conflitto
| * 2261c4a aggiunta di un file nella cartella principale
|/  
| * ac9a660 (prova_1, prova1_1) modifica fatta anche nel primo branch così 
da creare conflitto poichè entrambi i branch hanno modificato il file 
originale
| * da91172 aggiunta di un secondo file che mancherà nell'altro branch
| * b05947e aggiunta della cartella per gli esercizi git e del file per 
creare conflitto
| * bf83b25 aggiunta di un file nella cartella principale
|/  
* fdd080f (origin/main, main) eseguito anche l'esercizio 7.4
* 39f5fb9 svolgimento dell'esercizio 7
 ```
nel mio caso rimane ancora quel file ma semplicemente perchè si trova in 
altri branch, però nel mio branch prova_1 è stato eliminato

```
ìnizialmente avevo pensato di risolverlo facendo git reset --soft fdd080f, 
naturalmente stando sul branch prova_1, poi successivamentre fare rm -f 
del file e commit dei file, in questo modo però quello che avevo in più 
commit lo ho compresso in uno solo 
 ```


