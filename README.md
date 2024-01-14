# PilkkiCUP

Tulokset välilehti, Sija sarake

``` excel
=IF(COUNTIF(C2:M2 ;">0");RANK(S2;S$2:S$16) + COUNTIFS(S$2:S$16;$S2;T$2:T$16;">"&T2) + IF((COUNTIF($S$2:S2;S2)-1) > 0; (COUNTIF($T$2:T2;T2)-1); 0); "")
```
