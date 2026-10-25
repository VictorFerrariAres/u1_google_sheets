# La funció que més m'ha costat: `XLOOKUP` / `PROCX`

Sincerament, la funció que més se'm ha travessat amb diferència ha sigut **`XLOOKUP`** (o `PROCX` en català). Llegint la documentació oficial de Google semblava súper senzilla, però a la pràctica m'he emboliat bastant amb la sintaxi i els paràmetres opcionals.

Al principi no entenia per què em donava l'error `#N/A` o em sortia el missatge rar sobre `ARRAYFORMULA`. El problema principal era que li estava passant les matrius malament (ficava rangs separats per comes com si fossin blocs individuals) i, a sobre, quan arrossegava la fórmula cap avall **se m'oblidava fixar les cel·les amb el signe de dòlar (`$`)**. Això feia que el rang de cerca es mogués i fos un desastre.

### Què he provat al full per entendre-la?

-   **Provar matriu per matriu:** En lloc de fer la fórmula gran de cop, he anat provant de fer cerques senzilles columna per columna per veure si tornava el valor correcte.
    
-   **Fixar els rangs amb `$`:** M'he adonat que posant `$A$2:$A$49` la taula es quedava quieta i ja no fallava en copiar la fórmula cap avall.
    
-   **Provar el paràmetre d'error:** He provat d'escriure `"No existeix"` com a quart paràmetre per comprovar si realment s'amagava l'error `#N/A` quan posava un ID inventat al cercador.
    
-   **Combinar amb `HSTACK`:** Per al cercador, he provat d'unir totes les columnes de retorn en una sola fórmula matricial per no haver d'escriure la fórmula sis vegades seguides.
