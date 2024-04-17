# 4 sija
Tällä välilehdellä on laskettu kilpailijan sijoitus erikseen kussakin osakilpailussa. 

![sarjataulukko](Cup_sijoitus.png)

sija
`=Tulokset.B2`

Kilpailija
`=IF(Tulokset.C2 = ""; ""; Tulokset.C2)

Kisapäivät
`=IF(Tulokset.D1 = ""; ""; Tulokset.D1)`

Tulokset
`=IF(Tulokset.D2="";"";RANK(Tulokset.D2;Tulokset.D$2:D$21;0))`

1. Sija
`=IF($B2 = ""; ""; COUNTIF($C2:$R2;1))`

2. Sija
`=IF($B2 = ""; ""; COUNTIF($C2:$R2;2))`

3. Sija
`=IF($B2 = ""; ""; COUNTIF($C2:$R2;3))`
