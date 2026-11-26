1\) Simulare un merge conflict tra due branch. Dare evidenza dall'intera sessione 
Git, l'errore riscontrato e risoluzione del conflitto.

ho creato due branch prova_1 e prova_2 con stesso file, successivamente l'ho 
modificato su entrambi i branch in modo diverso, così da crearmi un conflitto e da 
dover scegliere uno dei due file

`git merge prova_1`
```
Auto-merging esercizi/esercizi_track_extra/esercizi_git/esercizio_conflitti_git.md
CONFLICT (content): Merge conflict in 
esercizi/esercizi_track_extra/esercizi_git/esercizio_conflitti_git.md
Automatic merge failed; fix conflicts and then commit the result.
```

`git status`
```
On branch prova_2
Your branch is up to date with 'origin/prova_2'.

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Changes to be committed:
    new file:   file_mancante_secondo_branch.md

Unmerged paths:
  (use "git add <file>..." to mark resolution)
    both modified:   esercizio_conflitti_git.md
```

`cat esercizio_conflitti_git.md` 
```
1\)Simulare un merge conflict tra due branch. Dare evidenza dall'intera 
<<<<<<< HEAD
sessione Git, l'errore riscontrato e risoluzione del conflitto.
Ho spostato e modificato quella dopo, ho aggiunto questa riga. ho modificato la 
prima.
%%
con git restore \<file> lo ho prima eliminato riportandolo al commit precendete
con git restore --staged \<file> dopo aver fatto add, me lo sono tolto dallo 
staging 
%%
in questo modo sto divergendo rispetto a prova_1
=======
sessione Git, l'errore riscontrato e risoluzione del conflitto. Su prova_1 ho fatto 
questa 
modifica così da generare conflitto su stessa riga. entrambi i branch hanno messo 
mano su 
questa riga. Ho aggiunto questa riga.
>>>>>>> prova_1
```
a questo punto ho modificato il file tenendo il file da <<<< HEAD a ===; cancellando di 
conseguenza il resto.

`git add esercizio_conflitti_git.md`
``` 
git status
On branch prova_2
Your branch is up to date with 'origin/prova_2'.

All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
	new file:   file_mancante_secondo_branch.md
```
```
git commit -m "commit per il merge" 
[prova_2 25b458b] commit per il merge
```
```
git status
On branch prova_2
Your branch is ahead of 'origin/prova_2' by 3 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
```
`git push`
``` 
Enumerating objects: 13, done.
Counting objects: 100% (13/13), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 587 bytes | 587.00 KiB/s, done.
Total 5 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:mattiaminelli-png/formazione_sou.git
   32676d4..25b458b  prova_2 -> prova_2
```

`git log -5  --oneline --graph --all`
```
*   25b458b (HEAD -> prova_2, origin/prova_2) commit per il merge
|\  
| * 83fc75f (origin/prova_1, prova_1) modifica fatta anche nel primo branch così da 
creare conflitto poichè entrambi i branch hanno modificato il file originale
| * 11cdbb3 aggiunta di un secondo file che mancherà nell'altro branch
* | 32676d4 ho modificato il file in modo diverso anche da github per gestire le 
modifiche con il commit
|/  
* 744d395 aggiunta della cartella per gli esercizi git e del file per creare conflitto
```
