# Problèmes rencontrés avec Métopes

```
XMLmind 9.5.1
Métopes v3
```

## Transformation TEI vers JATS : perte de la fusion des cellules d'un tableau

l'indication de la fusion des cellules est bien présente dans la TEI mais n'est pas retranscrite dans le JATS. 

Fichier `2022-01-04_article_test_diamenti__TEI.xml` ligne 548
```xml
 <row>
    <cell rend="text-align:start;" rendition="#Cell2.A3" rows="16">
        <hi rend="bold" style="typo_gras">wT2</hi>
    </cell>
    <cell rend="text-align:start;" rendition="#Cell2.A3">VL_left-right*</cell>
    <cell rend="text-align:start;" rendition="#Cell2.A3">+2.809572</cell>
    <cell rend="text-align:start;" rendition="#Cell2.A3">+3.063086</cell>
    <cell rend="text-align:start;" rendition="#Cell2.A3">0.00371575</cell>
</row>
 ```

 Fichier `2022-01-04_article_test_diamenti.xml` ligne 574
 ```xml
 <tr>
    <td>
        <bold>wT2</bold>
    </td>
    <td>VL_left-right*</td>
    <td>+2.809572</td>
    <td>+3.063086</td>
    <td>0.00371575</td>
</tr>
 ```