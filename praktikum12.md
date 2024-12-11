Selles praktikumis tegelesin Linuxis scriptimisega. Ülessandes 4 ja 5 sain koodid gpt abiga tehtud, ülessande 6 koodi tegin ise tsükliga.

<img width="446" alt="praktikum12 1" src="https://github.com/user-attachments/assets/3d81d664-9e38-44da-bcb8-f95606622b9c">
<img width="437" alt="praktikum12 2" src="https://github.com/user-attachments/assets/445da319-c5de-45d6-baf3-3b3b1c88122c">
<img width="442" alt="Praktikum12 3" src="https://github.com/user-attachments/assets/9836d938-2ec3-47f2-9525-9c87047dc60a">
<img width="428" alt="praktikum12 4 1" src="https://github.com/user-attachments/assets/7eabdfe5-2ad8-49fd-a3fd-4013ddc5451f">

Ülessanne 4 kood: 
#!/bin/bash

if [ "$#" -ne 2 ]; then
    echo "Kasutamine: $0 <laiend A> <laiend B>"
    exit 1
fi

laiend1=".$1"
laiend2=".$2"

for fail in *"$laiend1"; do
    if [ -e "$fail" ]; then
        uus_fail="${fail/$laiend1/$laiend2}" 
        mv "$fail" "$uus_fail" 
        echo "Fail '$fail' nimetati ümber failiks '$uus_fail'."
    else
        echo "Ühtki faili laiendiga $laiend1 ei leitud."
    fi
done

<img width="400" alt="Praktikum12 5" src="https://github.com/user-attachments/assets/44940556-63b1-4a9e-ab0a-8fc40d675176">
<img width="440" alt="praktikum12 5 2" src="https://github.com/user-attachments/assets/fac47199-f9af-45b3-896e-21ff0fac7cd4">
Ülessanne 5 kood:
#!/bin/bash
if [ -z "$1" ]; then
    echo "Kasutus: $0 <protsessi_nimi>"
    exit 1
fi

protsessinimi=$1
IFS=$'\n' 

leidusid=0
for rida in $(ps -A)
do
    protsessiinfo=$(echo " $rida" | tr -s ' ' | cut -d ' ' -f2,5-)
    pid=$(echo "$protsessiinfo" | cut -d ',' -f1)
    nimi=$(echo "$protsessiinfo" | cut -d ',' -f2)

    if [[ "$nimi" == *"$protsessinimi"* ]]; then
        echo "Protsess: $nimi, PID: $pid"
        leidusid=1
    fi
done

if [ $leidusid -eq 0 ]; then
    echo "Protsessi nimega '$protsessinimi' ei leitud."
fi

<img width="428" alt="praktikum12 6 1" src="https://github.com/user-attachments/assets/ee910c5c-2151-4417-87d8-1b981cf372b2">
<img width="325" alt="praktikum12 6 2" src="https://github.com/user-attachments/assets/01e9bea5-50e7-4956-87c1-8d33ef15d736">
Ülessanne 6 kood: 
#!/bin/bash

astenda () {
  tulemus=1
  for (( i=1; i<=$2; i++ ))
  do
    tulemus=$(($tulemus * $1))
  done
  echo $tulemus
}

tulemus=$(astenda 9 5)
echo "9^5 = $tulemus"


<img width="544" alt="praktikum12 7" src="https://github.com/user-attachments/assets/dfe8fff3-cb56-4553-bcea-fb1aeeec9d43">
