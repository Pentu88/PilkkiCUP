# 1 Sarjataulukko
Tällä välilehdellä kilpailijat esitetään pisteytykseen perustuvassa paremmuus järjestyksessä.

![sarjataulukko](Cup_Sarjataulukko.png)

- 1 [Sarjataulukko](standings.md)
  - 1.1 [1.1 Sija](#11-Sija)
  - [1.2 Kilpailija](#12-kilpailija)
  - [1.3 Pisteet](#13-pisteet)
  - [1.4 yht. paino](#14-yht-paino)
  - [1.5 Kisat](#15-kisat)
  - [1.6 p/Kisa](#16-pkisa)
  - [1.7 g/Kisa](#17-gkisa)
  - [1.8 Voitot](#18-voitot)
  - [1.9 Top 3](#19-top-3)
  - [1.10 Suurin, kisat](#110-kisan-suurin)
  - [1,11 Suurin, kausi](#111-suurin-kausi)
- [2. Tulokset](results.md)
- [3. Suurin kala](biggest_fish.md)
- [4. Sijoitus](ranking.md)

## 1.1 Sija

Lisätään järjestyksessä seuraava sija -luku, mikäli "Tulokset" -välilehdellä on kirjattu vastaavalle riville mikätahansa sijoitus sarakkeessa A.

`=IF(Tulokset.A2 = "";"";1)`

> [!NOTE]
> Tämä on ongelmallinen tapa, mikäli välissä on kilpailijoita, joilla ei ole vielä tulosta.
> Tähän voisi käyttää esimerkiksi tulosten / kilpailijoiden määrä -soluja. 

## 1.2 Kilpailija

Etsitään kilpailijan nimi `Tulokset` -välilehden `B` -sarakkeesta (haku alueen 2. sarake). Tulos palautetaan riviltä, jolla kilpailijan sijoitus vastaa etsittyä sijoitusta. 

`=VLOOKUP(B4;Tulokset.$A$2:$P$13;2;0)`

> [!Note]
> Tässä tulee käyttää uudessa versiossa "esitys lukua" sijoituksen sijasta. Sijoitus voi olla jaettu tietyissä tilanteissa, lisäksi tuloksen puuttuessa, ei myöskään määritellä sijoitusta. 

## 1.3 Pisteet

Haetaan arvo `Tulokset` -välilehden `S` -sarakkeesta (haku alueen 18. sarake), johon on laskettu kilpailijoiden keräämät pisteet. Tulos palautetaan riviltä, jolla kilpailijan nimi vastaa etsittyä nimeä.

`=IF(B4="";"";VLOOKUP(C4;Tulokset.$B$2:$U$13;18;0))`

## 1.4 Yht. paino

Haetaan arvo `Tulokset` -välilehden `T` -sarakkeesta (haku alueen 19. sarake), johon on laskettu yhteen kunkin kilpailijan keräämä saalis koko kauden ajalta. Tulos palautetaan riviltä, jolla kilpailijan nimi vastaa etsittyä nimeä.

`=IF(B4="";"";VLOOKUP(C4;Tulokset.$B$2:$U$13;19;0))`

## 1.5 Kisat

Haetaan arvo `Tulokset` -välilehden `U` -sarakkeesta (haku alueen 20. sarake), johon on laskettu yhteen kunkin kilpailijan osallistumiset koko kauden ajalta. Tulos palautetaan riviltä, jolla kilpailijan nimi vastaa etsittyä nimeä.

`=IF(B4="";"";VLOOKUP(C4;Tulokset.$B$2:$U$13;20;0))`

## 1.6 p/Kisa

Lasketaan kilpailijan pistekeskiarvo.

`=IF(B4="";"";D4/F4)`

## 1.7 g/Kisa

Lasketaan kilpailijan keskimääräinen saalis osakilpailua kohden. 

`=IF(B4="";"";E4/F4)`

## 1.8 Voitot

Haetaan arvo `Sijoitus` -välilehden `S` -sarakkeesta (hakualueen 18. sarake), johon on laskettu kilpailijan voitot kuluvalta kaudelta.

`=IF(B4="";"";VLOOKUP(C4;Sijoitus.$B$2:$U$13;18;0))`

## 1.9 Top 3

`=IF(B4="";"";VLOOKUP(C4;Sijoitus.$B$2:$U$13;18;0) + VLOOKUP(C4;Sijoitus.$B$2:$U$13;19;0) + VLOOKUP(C4;Sijoitus.$B$2:$U$13;20;0))`

## 1.10 Kisan suurin

Haetaan arvo `Suurin kala` -välilehden `S` -sarakkeesta (hakualueen 18. sarake), johon on laskettu kilpailijan osakilpailu kohtaiset "suurin kala" voitot kuluvalta kaudelta.

`=IF(B4="";"";VLOOKUP(C4;'Suurin kala'.$B$2:$U$13;18;0))`

## 1.11 Suurin (kausi)

`=IF(B4="";"";VLOOKUP(C4;'Suurin kala'.$B$2:$U$13;20;0))`
