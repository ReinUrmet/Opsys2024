Selles praktikumis tegelesin failiõigustega Linuxis.

ÜL 5.1 - Ülesandes tuli katsetada milliseid minimaalõigusi oli vaja, et a) faili lugeda ja b) fail kustutada.
a) alguses andsin kaustale kõik õigused uuesti kasutades: chmod 700 /tmp/kaust ja seejärel andsin õiguse lugeda faili minufail.txt, kasutades: chmod 600 /tmp/kaust/minufail.txt ja siis proovisin lugeda: cat /tmp/kaust/minufail.txt ja lgeski välja Rein Umret. Aga kui ma andsin chmod 000, siis ei saanud faili avada. Kokkuvõtteks: omanikul on vaja r ja x õigusi, et lugeda faili sisu, aga omanikul ei ole vaja w õigusi, et faili lugeda.

b)Nende õigustega sain kustutada faili kasutades: rm /tmp/kaust/minufail.txt. Seejärel lõin kirjutasin faili tagasi: kasutades echo "Rein Urmet" > /tmp/kaust/minufil ja see lõi tagasi faili. Aga kui muutsin kausta õigusi kasutades: chmod 500 /tmp/kaust/minufail.txt, sellega võtsin ära kirjutamis õigused ja peale seda ei saanud faili kustutada. Kokkuvõtteks: omanikul on vaja kausa õiguseid w ja x, et faili kustutada.

Ül 5.2 - Ülesandes on küsitud: Miks chmod a=x skriptifail ei ole piisav õigus shelli skriptifaili käivitamiseks? Vastus: See ei anna piisavaid õigusi, sest see annab ainult x õigused ehk execution rights, aga sul puudub lugemis õigused mistõttu ei saa shell lugeda skriptifaili sisu ja seetõttu ei tea mis käsklusi täita.

Ül 5.3 - Miks on igal kasutajal oma grupp? Vastus: Igal kasutajal on oma grupp kuna nii on lihtsam failiõigusi hallata, turvalisuse mõttes, see isoleerib kasutaja andmed.

Ül 5.6 - jah, esiteks: Tavaline kasutaja võib saada kõrgemaid õigusi ja pääseda tundlikule infole, naiteks pääseks juku isa kõikide õpilaste hinnetele ligi mis oleks andmelekke. teiseks: Ründajad saavad käivitada ohtlikke skripte, kasutades kõrgemaid õigusi. 

Ül 5.7 - Peeter saab ise faili kustutada ja teised kasutajad nagu näiteks opetaja ja jukuisa saavad s

eda kustutada ainult siis kui anda neile oma failide omandiõiguse.

Ül 5.9 - chattr +i-parameetriga faili saab kustutada ainult root kasutaja ja kidas seda kustutasin panen alla pildina.

<img width="959" alt="praktikum5 4" src="https://github.com/user-attachments/assets/b33086a7-5310-4c1b-8ade-55963626a205">
<img width="674" alt="praktikum5 5" src="https://github.com/user-attachments/assets/96831c17-708d-499b-9593-9d91c2147000">
<img width="656" alt="praktikum5 8" src="https://github.com/user-attachments/assets/5ccfcdab-9ab6-4fdf-98e3-101ae906392f">
<img width="425" alt="praktikum5 9" src="https://github.com/user-attachments/assets/76e4255b-812d-434e-999e-c09788c32acb">
