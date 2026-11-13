4)ho sia provato in questo modo dalla cartella /etc/crontab dovendo mettere in questo modo root come user-name
altrimenti l'ho impostato anche con sudo crontab -e evitando così di dover anche specificare l'utente nel codice dentro crontab
```
SHELL=/bin/bash

PATH=/sbin:/bin:/usr/sbin:/usr/bin

MAILTO=root

  

# For details see man 4 crontabs

  

# Example of job definition:

# .---------------- minute (0 - 59)

# |  .------------- hour (0 - 23)

# |  |  .---------- day of month (1 - 31)

# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...

# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat

# |  |  |  |  |

# *  *  *  *  * user-name  command to be executed

30 6 * * 1 root /usr/bin/find /home/mattia723/Lavoro -type f -mtime +30 -exec rm {} \;

#40 10 * * * root /usr/bin/find /home/mattia723/Lavoro -type f -mtime +30 -exec rm {} \;
```

avevo verificato la validità della sintassi del comando con un crontab su dei file che mi ero creato con dd di diverso peso e successivamente modificato la data con touch in modo tale da ottenere una differenza di giorni maggiore di 30. successivamente ho controllato usando watch del comando ls la scomparsa dei file e quindi l'effettiva funzione del comando. 
