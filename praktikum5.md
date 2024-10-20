Selles praktikumis tegelesin failiõigustega Linuxis.

ÜL 5.1 - Ülesandes tuli katsetada milliseid minimaalõigusi oli vaja, et a) faili lugeda ja b) fail kustutada.
a) alguses andsin kaustale kõik õigused uuesti kasutades: chmod 700 /tmp/kaust ja seejärel andsin õiguse lugeda faili minufail.txt, kasutades: chmod 600 /tmp/kaust/minufail.txt ja siis proovisin lugeda: cat /tmp/kaust/minufail.txt ja lgeski välja Rein Umret. Aga kui ma andsin chmod 000, siis ei saanud faili avada. Kokkuvõtteks: omanikul on vaja r ja x õigusi, et lugeda faili sisu.

b)Nende õigustega sain kustutada faili kasutades: rm /tmp/kaust/minufail.txt. Seejärel lõin kirjutasin faili tagasi: kasutades echo "Rein Urmet" > /tmp/kaust/minufil ja see lõi tagasi faili. Aga kui muutsin kausta õigusi kasutades: chmod 500 /tmp/kaust/minufail.txt, sellega võtsin ära kirjutamis õigused ja peale seda ei saanud faili kustutada. Kokkuvõtteks: omanikul on vaja kausa õiguseid w ja x, et faili kustutada.

