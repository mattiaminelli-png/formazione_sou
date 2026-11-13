passatemi l'output di questi comandi:
lsblk
df -h
ls -l /dev/disk/by-uuid
cat /etc/fstab

ridirezionate l'output di tutti i comandi appendendo l'output di ogni singolo comando in un file OUT.LOG
bonus se il comando lo fate con un one-liner

Ho ottenuto il risultato inizialmente con il comando:
```
lsblk > out.log && df -h >> out.log && ls -l /dev/disk/by-uuid >> out.log && cat /etc/fstab >> out.log
```

successivamente con :

```{ lsblk; df -h; ls -l /dev/disk/by-uuid; cat /etc/fstab; } >> OUT.LOG```
