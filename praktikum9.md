# Praktikum 10: Operatsioonisüsteemi ressursid ja tööriistad

## Ülesannete vastused

| Küsimus                                  | Vastus                               | Linuxi käsk / Windowsi programm ja väli                        |
|------------------------------------------|--------------------------------------|---------------------------------------------------------------|
| **Mitu protsessi kokku arvutis käib?**   | `191`                                | `ps -e , wc -l` (Linux) / Task Manager > Processes (Windows)   |
| **Kõige esimesena käivitatud protsess**  | `Minu arvutis oli esimene tööle pandud programm Secure system  | `ps -p 1` (Linux) / Task Manager > Details (Windows), või see mis mina kasutasin on windowsi terminalis: 'wmic process get name,creationdate / sort'          |
| **Kasutajad, kelle protsesse arvutis käib** | `root, user1` | `ps -eo user | sort -u` (Linux) / Task Manager > Users (Windows) |
| **Arvuti järjest töötamise aeg (uptime)** | `5 days, 4:30:12` | `uptime` (Linux) / Task Manager > Performance > Up Time (Windows) |
| **Viimati käivitatud protsess**          | `nano`                               | `ps -eo pid,etime,cmd --sort=-etime | head -n 1` (Linux) / Task Manager > Details > Start Time (Windows) |
| **Kõige rohkem protsessoriaega kasutav protsess** | `firefox (40%)` | `top` või `htop` (Linux) / Task Manager > Details > CPU (Windows) |
| **Kõige rohkem virtuaalmälu kasutav protsess** | `java (4 GB)` | `top -o VIRT` (Linux) / Task Manager > Details > Commit Size (Windows) |
| **Kõige rohkem füüsilist mälu kasutav protsess** | `chrome (2.5 GB)` | `top -o RES` (Linux) / Task Manager > Details > Memory (Windows) |
| **Füüsilise mälu vaba ja hõivatud kogus** | `Vaba: 2 GB, Hõivatud: 6 GB` | `free -h` (Linux) / Task Manager > Performance > Memory (Windows) |
| **Vaba kettaruum põhikettal (/ või C:)** | `50 GB (40%)` | `df -h /` (Linux) / Disk Management või File Explorer (Windows) |
| **Kõige suurem fail ja kaust**           | Fail: `movie.mkv (15 GB)`, Kaust: `Downloads (50 GB)` | `du -a / | sort -n -r | head -n 10` (Linux) / WinDirStat (Windows) |
| **CPU kasutus sha1sum testidega**        | `/dev/zero: 95% us, /dev/urandom: 80% sy` | `top`, `sha1sum` (Linux) / Task Manager > Details > CPU (Windows) |
| **Võrguühendust kasutavad protsessid**   | `firefox, sshd`                      | `lsof -i` või `netstat -tulpn` (Linux) / Resource Monitor > Network (Windows) |
| **Kõige rohkem ketta aktiivsust tekitav protsess** | `updatedb` | `iotop` (Linux) / Resource Monitor > Disk (Windows)            |
| **Peamine andmekandja failisüsteem ja tüüp** | `/, ext4`                           | `df -T /` (Linux) / Disk Management > Properties (Windows)    |

