# machine-learning-intro
Machine learning explained from the ground up using image classification as an example (Norwegian)


Vi må gjør det enklere hvis du skal få til å lage dette fra grunnen av. Her er det enkleste eksemplet jeg kommer på lage. Vi kan gjøre det mer komplett etter hvert som du har fått til første del. Til å starte med tror jeg det er best å lage et ferdig trent nett som klassifiserer bilder.



Se for deg at vi har 10 bilder, 4 har en vertikal strek og 6 har en horisontal strek. De er alle 5*5 pixler. Ingen av strekene helt i kanten men de trenger ikke være i midten. Hver av disse er layer_0. 



/////////////////////////////////////////////////////////////////////////////////



Så skal du lage layer1. Dette blir forskjellig for alle bildene i layer0.



Vi bestemmer oss for at vi skal ha tre kerneler. I denne runden er de deterministiske (du bruker ikke vekter denne gangen, nå skal du forstå hvordan det virker). Siden vi vet hvordan bildene vi skal klassifisere ser ut kan vi bestemme oss for hvilke vekter vi skal ha for hvert pixel i kernelene. 



Den første kernelen er 

0 1 0

0 1 0

0 1 0



Den andre er 

0 0 0

1 1 1

0 0 0



Den tredje er (Se om du kan forstå hvorfor vi setter alle vekten fra denne til null i neste ledd)

1 0 0

0 1 0

0 0 1



For å lage layer2 må du for hvert punkt i bilde gange sammen elementvis og summere. Jeg har vist deg hvordan det blir.  Ikke ta med kanten (starter en pixel inn og en pixe ned), du kommer til å ende opp med en matrise som er 3*3 for hver kernel. Dette må gjøres for hvert bilde. 



/////////////////////////////////////////////////////////////////////////////////





Nå skal du lage layer2. Mellom layer1 og layer2 ligger vektene du skal optimere i neste runde, men i denne runden er de deterministisk. Vi har to klasser (vertikal strek og horisontal strek) så da blir det to noder i layer2.



For hver av de to nodene tar du summen av alle vektene i layer1 ganger med vektene vi velger. Dette må du gjøre hvert bilde.



Vektene som går til den første noden i layer 2: Denne noden klassifiserer et bilde til å ha en vertikal strek. Vektene fra nodene som er regnet ut med den første kernelen blir en, de andre er er null.



Vektene som går til den andre noden i layer 2:  Denne noden klassifiserer et bilde til å ha en horisontal strek. Vektene fra nodene som er regnet ut med den andre kernelen blir en, de andre er er null.



Til slutt må du lage en outputfuksjon. Den sammenligner de to nodene i layer2 og skriver ut indexen til noden som har høyest verdi. Dette kalles en argmax funksjon, vi skal senere gjøre denne til en softmax.



Denne algoritmen kommer til å klassefisere bildene rett. Målet i runde to er at vi skal slippe å sette vektene manuelt men at de skal settes med maskinlæring.



Hvis du vil jeg skal hjelpe deg er det er best om du deler dette på et repo. Det blir litt rart og ikke så effektivt å svare på spørsmål her inne.
