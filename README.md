# PilkkiCUP

PilkkiCUP on pienen porukan sarjamuotoinen leikkimielinen talvikalastus kilpailu. Kilpailu aloitettu jo keväällä 2014.

Jokainen tulos on dokumentoitu _PilkkiCUP_ -sarjan ensimäisestä osakilpailusta alkaen. Virallisena kilpailu pöytäkirjana toimii paperinen dokumentti, johon tulokset kirjataan, kun kipailijat tuovat saaliinsa punnittavaksi. 

Tähän dokumentaatioon on kerätty kaavat Excel -dokumentista, joka toimii epävirallisena digitalisoituna pöytäkirjana.

## Välilehdet
- [1. Sarjataulukko](standings.md)
- [2. Tulokset]()
- [3. Suurin kala]()

## 2 Tulokset

### 2.1 Sija

Käytetyt funktiot:
- IF
- RANK
- COUNTIFS
- COUNTIF

Sarakkeeseen `A` lasketaan jokaiselle kyseisellä kaudella osakilpailuun osallistuneelle henkilölle sijoitus vertailemalla kerättyjä pisteitä muiden kilpailijoiden pisteisiin. Pisteiden ollessa tasan, vertaillaan myös kokonais saaliita.
``` EXCEL
=IF(COUNTIF(C2:M2 ;">0");RANK(S2;S$2:S$16) + COUNTIFS(S$2:S$16;$S2;T$2:T$16;">"&T2) + IF((COUNTIF($S$2:S2;S2)-1) > 0; (COUNTIF($T$2:T2;T2)-1); 0); "")
```

Tarkastetaan ensin onko kilpailijalle kirjattu tuloksia (sarakkeet `C`-`R`). Mikäli tuloksia on kirjattu, lasketaan sijoitus luku kolmessa osassa. 

Ensin verrataan pisteitä (sarake `S`) muiden kilpailijoiden pisteisiin. 

``` EXCEL
RANK(S2;S$2:S$16)
```

Saatuun sijoitukseen lisätään kilpailijat, joilla on sama pistemäärä, mutta suurempi kokonais saalis (sarake ´T´). 

``` EXCEL
COUNTIFS(S$2:S$16;$S2;T$2:T$16;">"&T2)
```

Seuraavaksi tulokseen lisätään taulukossa ylempänä olevat saman pistemäärän keränneet.

``` EXCEL
IF((COUNTIF($S$2:S2;S2)-1) > 0; (COUNTIF($T$2:T2;T2)-1); 0)
```

### 2.2 Pisteet

``` EXCEL
=IF($B2="";"";IF(C2=0;0;C$18-(RANK(C2;$C$2:$C$16;0)-1))+IF(D2=0;0;D$18-(RANK(D2;$D$2:$D$16;0)-1))+IF(E2=0;0;E$18-(RANK(E2;$E$2:$E$16;0)-1))+IF(F2=0;0;F$18-(RANK(F2;$F$2:$F$16;0)-1))+IF(G2=0;0;G$18-(RANK(G2;$G$2:$G$16;0)-1))+IF(H2=0;0;H$18-(RANK(H2;$H$2:$H$16;0)-1))+IF(I2=0;0;I$18-(RANK(I2;$I$2:$I$16;0)-1))+IF(J2=0;0;J$18-(RANK(J2;$J$2:$J$16;0)-1))+IF(K2=0;0;K$18-(RANK(K2;$K$2:$K$13;0)-1))+IF(L2=0;0;L$18-(RANK(L2;$L$2:$L$13;0)-1))+IF(M2=0;0;M$18-(RANK(M2;$M$2:$M$13;0)-1))+IF(N2=0;0;N$18-(RANK(N2;$N$2:$N$13;0)-1))+IF(O2=0;0;O$18-(RANK(O2;$O$2:$O$13;0)-1))+IF(P2=0;0;P$18-(RANK(P2;$P$2:$P$13;0)-1))+IF(Q2=0;0;Q$18-(RANK(Q2;$Q$2:$Q$13;0)-1))+IF(R2=0;0;R$18-(RANK(R2;$R$2:$R$13;0)-1))+COUNTIF(C2:R2;0)+V2)
```

### 2.3 Saalis

``` EXCEL
=IF($B2 = ""; ""; SUM(C2:M2)+W2)
```

### 2.4 Osallistuminen

``` EXCEL
=IF($B2 = ""; ""; COUNT(C2:M2))
```

### 2.5 Osallistuminen

``` EXCEL
=IF($B2 = ""; ""; COUNT(C2:M2))
```
