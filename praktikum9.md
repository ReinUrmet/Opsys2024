# Praktikum 10: Operatsioonisüsteemi ressursid ja tööriistad

## Ülesannete vastused

| Küsimus                                  | Vastus                               | Linuxi käsk / Windowsi programm ja väli                        |
|------------------------------------------|--------------------------------------|---------------------------------------------------------------|
| **Mitu protsessi kokku arvutis käib?**   | `191`                                | `ps -e , wc -l` (Linux) / Task Manager > Processes (Windows)   |
| **Kõige esimesena käivitatud protsess**  | `Minu arvutis oli esimene tööle pandud programm Secure system  | `ps -p 1` (Linux) / Task Manager > Details (Windows), või see mis mina kasutasin on windowsi terminalis: 'wmic process get name,creationdate / sort'          |
| **Kasutajad, kelle protsesse arvutis käib** | `Rein Urmet` | `ps -eo user | sort -u` (Linux) / Task Manager > Users (Windows) |
| **Arvuti järjest töötamise aeg (uptime)** | `7 tundi ja 37 min` | `uptime` (Linux) / Task Manager > Performance > Up Time (Windows) või kirjutad systeminfo terminali ja otsid "System Boot Time" ja arvutad |
| **Viimati käivitatud protsess**          | `WmiPrvSE.exe ehk WMI Provider Host` | `ps -eo pid,etime,cmd --sort=-etime / head -n 1` (Linux) / Task Manager > Details > Start Time (Windows) |
| **Kõige rohkem protsessoriaega kasutav protsess** | `tegumihaldus (5%)` | `top` või `htop` (Linux) / Task Manager > Details > CPU (Windows) |
| **Kõige rohkem virtuaalmälu kasutav protsess** | `Microsoft edge` | `top -o VIRT` (Linux) / Task Manager > Details > Commit Size (Windows) |
| **Kõige rohkem füüsilist mälu kasutav protsess** | `Microsoft edge` | `top -o RES` (Linux) / Task Manager > Details > Memory (Windows) |
| **Füüsilise mälu vaba ja hõivatud kogus** | `Vaba: 7.2 GB, Hõivatud: 8.1 GB` | `free -h` (Linux) / Task Manager > Performance > Memory (Windows) |
| **Vaba kettaruum põhikettal (/ või C:)** | `262 GB` | `df -h /` (Linux) / Disk Management või File Explorer (Windows) |
| **Kõige suurem fail ja kaust**           | Fail: `OS-_Urmet-W11)`, Kaust: `Virtualboxiga seotud failid` | `du -a / | sort -n -r | head -n 10` (Linux) / WinDirStat (Windows) |
| **CPU kasutus sha1sum testidega**        | `/dev/zero: 95% us, /dev/urandom: 80% sy` | `top`, `sha1sum` (Linux) / Task Manager > Details > CPU (Windows) |
| **Võrguühendust kasutavad protsessid**   | `firefox, sshd`                      | `lsof -i` või `netstat -tulpn` (Linux) / Resource Monitor > Network (Windows) |
| **Kõige rohkem ketta aktiivsust tekitav protsess** | `updatedb` | `iotop` (Linux) / Resource Monitor > Disk (Windows)            |
| **Peamine andmekandja failisüsteem ja tüüp** | `/, ext4`                           | `df -T /` (Linux) / Disk Management > Properties (Windows)    |

