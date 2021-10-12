## Nick Dewaele


### About me

I am a Ph.D. student at KU Leuven working on the numerical analysis of multilinear models used in data analysis. What this means is explained [below](#wat-is-factoranalyse) (in Dutch). My research is supervised by [Nick Vannieuwenhoven](https://people.cs.kuleuven.be/~nick.vannieuwenhoven) and [Paul Breiding](https://pbrdng.github.io/). My contact information is available [here](https://www.kuleuven.be/wieiswie/nl/person/00124993).

### Research
#### Article preprints
- Three decompositions of symmetric tensors have similar condition numbers
  - Nick Dewaele, Paul Breiding, Nick Vannieuwenhoven, [arXiv 2110.04172](https://arxiv.org/abs/2110.04172)
- The condition number of many tensor decompositions is invariant under Tucker compression
  - Nick Dewaele, Paul Breiding, Nick Vannieuwenhoven, [arXiv 2106.13034](https://arxiv.org/abs/2106.13034)

#### Talks
- [Computing the condition number of tensor decompositions through Tucker compression](https://indico.cs.dm.unipi.it/event/7/contributions/19/attachments/12/12/abstract_mettix.pdf)
  - At the METTIX conference in Perugia, Italy, September 2021
- [The sensitivity of block term decompositions](http://www.ipam.ucla.edu/wp-content/uploads/2021/04/Dewaele-Poster-TMWS3.pdf)
  - At the IPAM workshop on _Mathematical Foundations and Algorithms for Tensor Computations_, April 2021

### Education
I have been a TA (_"assistent"_, >= 2020) or co-TA (_"jobstudent"_, <= 2019) for the following bachelor level courses:
- [Computergesteund probleemoplossen in de natuurkunde](https://onderwijsaanbod.kuleuven.be/2021/syllabi/n/G0P36BN.htm) (2022-...)
- [Toepassingen van de meetkunde in de informatica](https://onderwijsaanbod.kuleuven.be/2021/syllabi/n/G0Q37CN.htm) (2020-...)
- [Analyse, deel 3](https://onderwijsaanbod.kuleuven.be/2018/syllabi/n/H08W0AN.htm) (2018-2019)
- [Lineaire algebra](https://onderwijsaanbod.kuleuven.be/2018/syllabi/n/H0M69BN.htm) (2018-2019)
- [Wiskunde voor probleemoplossen](https://onderwijsaanbod.kuleuven.be/2018/syllabi/n/H01B9AN.htm) (2018)

I have also supervised master's theses on the following topics
- Completing correlation matrices for portfolio optimisation (P.E. Verleye & J. Nelis, 2021-2022)
- Riemannian optimisation on toric varieties (A. Lescroart, 2020-2021)

### Wat is factoranalyse ?
[Wikipedia](https://nl.wikipedia.org/wiki/Factoranalyse) definieert factoranalyse als een _statistische techniek die voor een groot aantal geobserveerde variabelen een kleiner aantal achterliggende variabelen identificeert_. Laten we illustreren met een voorbeeld.

Een psycholoog wil een model van persoonlijkheden ontwikkelen. Hiervoor heeft hij een vragenlijst met 100 vragen opgesteld, en deze vragenlijst is door een groot aantal proefpersonen beantwoord. Elke vraag bestaat uit een stelling, en de proefpersoon beantwoordt met een score van 0 (niet akkoord) tot 10 (akkoord). De antwoorden zijn gestructureerd als volgt:


|     | vraag 1 | vraag 2 | ... | vraag 100 |
| --- | :-----: | :-----: | :-: | :-------: |
| Alice | 3 | 0 | ... | 2 |
| Bob | 9 | 1 | ... | 7 |
| ... | ... | ... | ... | ... |

Er is een vermoeden dat de 100 vragen niet volledig losstaan van elkaar, omdat het antwoord op de ene vraag het antwoord op de andere gedeeltijk kan voorspellen. Bijvoorbeeld, op de vragen "Ik volg steeds een plan" en "Ik hou van orde" zal een proefpersoon typisch gelijkaardige antwoorden geven. Dat wijst erop dat hetzelfde persoonskenmerk op meerdere verschillende manieren gemeten wordt. Hoewel er 100 verschillende vragen gesteld worden, kan het zijn dat er in werkelijkheid maar een handvol kenmerken de antwoorden van een persoon op de vragenlijst verklaart. We hebben echter nood aan een systematische methode om te herkennen welke groepen vragen gelijkaardige kenmerken meten. Deze systematische methode heet factoranalyse.

Om dit vraagstuk op te lossen, vraagt de psycholoog om hulp bij de wiskundige, met de vraag om een vijftal achterliggende variabelen te bepalen. Deze gaat aan het werk op de volgende manier. Hij maakt vijf nieuwe testen, met al dezelde vragen als in de originele vragenlijst. Voor elke test wordt aan elke vraag een gewicht toegekend. Om even op de zaken vooruit te lopen: we willen dat elk van deze nieuwe testen een persoonskenmerk meet (bijv. dat de eerste test ordelijkheid meet) en dat de gewichten per vraag aangeven hoeveel die vraag aansluit bij dat persoonskenmerk. De gewichten zouden eruit kunnen zien als:

| vraag 1 | vraag 2 | ... | vraag 100 |
| :-----: | :-----: | :-: | :-------: |
| 0.05 | 0.02 | ... | 0.15 |

Voor elke proefpersoon is er dan een totaalscore te berekenen voor die test. De score per vraag is het opgegeven antwoord op de vraag, vermenigvuldigd met het gewicht van die vraag (precies zoals op een klassiek examen). Voor elke persoon wordt de score per vraag opgeteld tot een totaal. Dit zou bijvoorbeeld kunnen zijn:

| Persoon | Score |
| ------ | :-: |
| Alice | 33 |
| Bob   | 12 |
| ...   | ... |

De score op de test meet niet of de antwoorden juist of fout waren, maar wel of de proefpersoon vaak akoord ging met de stellingen (vragen) die veel gewicht kregen. Als de vragen met het meeste gewicht allemaal overeenkomen met een gelijkaardig persoonskenmerk, beantwoorden de proefpersonen met de hoogste scores ook het meest aan dat persoonskenmerk. Het idee is dus om voor elk persoonskenmerk zo een test te maken aan de hand van vragen uit de originele lijst, telkens met andere gewichten.

Herinner dat de bedoeling was om de originele tabel met de antwoorden van de proefpersonen samen te vatten tot een minimum aan informatie. Dat doen we door enkel de totaalscores op de nieuwe testen bij te houden, en de antwoorden op de individuele vragen te negeren. Per persoon hebben we dus vijf totaalscores in plaats van honderd antwoorden op individuele vragen. De samenvatting van de originele tabel ziet er dan bijvoorbeeld uit als volgt:

| Persoon | Score op test 1 | ... | Score op test 5 |
| ------ | :-: | :-: | :-: |
| Alice | 33 | ... | 76 |
| Bob   | 12 | ... | 40 |
| ...   | ... | ... | ... |


Als elke van de vijf testen &eacute;&eacute;n van de voornaamste persoonskenmerken meet, bekomen we op deze manier een goede samenvatting van de originele gegevens. Als &eacute;&eacute;n van de testen geen duidelijk persoonskenmerk meet, hebben we waarschijnlijk een slechte samenvatting. Het is mogelijk om wiskundig te kwantificeren of we een goede samenvatting hebben door te kijken hoeveel percent van de originele tabel gereconstrueerd kan worden uit de nieuwe. Dit wordt dus het criterium om vijf persoonskenmerken te identificeren: stel de testen op een zodanige manier op dat de totaalscores zoveel mogelijk verklaren over de originele tabel met de antwoorden op de vragen.

De wiskundige heeft enkele algoritmen ter beschikking om dit vraagstuk op te lossen. &Eacute;&eacute;n van die algoritmen wordt uitgevoerd op een computer, en resultaat ervan bestaat uit vijf sets van gewichten. Voor elke set van gewichten is er een nieuwe test. Die worden overhandigd aan de psycholoog.

De psycholoog is zeer tevreden met de resultaten. Hij ziet dat de eerste test vooral gewicht legt bij de vragen iets met ordelijkheid te maken hebben. De tweede test legt vooral gewicht bij vragen over beleefdheid, enz. Hij heeft de vijf persoonskenmerken gevonden die het best overeenkomen met de vragen uit de vragenlijst.

De hierboven beschreven proceduren bevat de grondslagen van verschillende methoden voor factoranalyse, waaronder PCA, ICA, PARAFAC, BTD, etc. De toepassingen zijn allesbehalve beperkt tot de psychologie, maar reiken tot scheikunde, verwerking van biomedische gegevens, machinaal leren, enz. De achterliggende wiskunde is met andere woorden perfect herbruikbaar en het bovenstaande was maar &eacute;&eacute;n van vele voorbeelden. Behalve de louter toepassingsgerichte vragen zijn er tal van wiskundige vragen hierover interessant om te onderzoeken:
1. Op welke manier wordt de optimale oplossing berekend? Hoe kan het vermelde algoritme ge&iuml;mplementeerd worden?
2. Bestaat er soms meer dan &eacute;&eacute;n optimale oplossing? 
3. Hoe bepalen we het aantal achterliggende variabelen? In het bovenstaande voorbeeld was 5 een willekeurige keuze.
4. Bestaan er verschillende modellen die het bovenstaande idee kunnen formaliseren?
5. Hangt de nauwkeurigheid van het resultaat af van hoe de berekeningen worden uitgevoerd?
6. Hoe nauwkeurig kunnen de optimale gewichten bepaald worden als we bedenken dat de originele gegevens typisch niet perfect accuraat zijn?

Ik hou mezelf bezig met enkele van deze vragen, in het bijzonder vragen 5 en 6.
