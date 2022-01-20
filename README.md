
# Métopes et JATS : notes de travail


## Declaration des images

### pb balises <label> & <caption>

mémo : Label doit contenir son "identitiant littéraire : Figure 2" et caption la légende, laquelle peut contenir un titre avec `<title>` [voir exemple JATS4R](Example-JATS4R-image-avec-DOI)

Article Kernbach
```xml
<graphic xlink:href="data/emergneurol_01_01_kernbach_fig01.jpg" xmlns:xlink="http://www.w3.org/1999/xlink"/>
Figure 1.</p>
<fig>
    <label>Meta-topologies in primary brain tumors
        <bold>.</bold></label>
</fig>
```

 > Figure 1. devrait être à l'intérieur de `<label>` et `Meta-topologies in primary brain tumors` dans `<caption>`


### Présence de la balise <caption>

Liu 
```xml
<fig>
    <label>Figure 1.</label>
    <caption>
        <p>Figure 1. Receiver operating characteristic (ROC) curve of the monocyte/high-density lipoprotein ratio (MHR) for intracranial and extracranial atherosclerotic stenosis.</p>
    </caption>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/neuro_01_08_fig1.jpg" />
</fig>
```


### pb mineur : une déclaration d'image sans label

Liu 
```xml
<p>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/neuro_01_08_table3.jpg" />
</p>
```


### pb mineur : une image non déclarée

Liu 
> Erwan commentaire : image "neuro_01_08_table2.jpg" n'est déclaré nulle part bien qu'étant présent parmi les images dépendentes et étant fait "référence" dans le jats 


### pb mineur : une balise autofermante inutile 


Article Kernbach
```xml
<p>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/emergneurol_01_01_kernbach_fig04.jpg" />
    Figure 4
    <fig />
    .
</p>
<fig>
    <label>Brain tumor meta-topologies and patient survival.</label>
</fig>
```

<br />

## Déclaration et référence des table


 Dans l'article Kernbach (METATOPOLOGIES) il est fait référence à 4 tables mais il n'y a qu'une table de déclarée en tant que telle sous la balise `<table>`, les autres tables étant introduites comme des images de table, sous la balise `<graphic>` donc, ce qui est très problématique...

Reference
```xml
<xref rid="table1">
    <underline>Table 1</underline>
</xref>
```

Declaration
```xml
<table-wrap specific-use="frame">
    <table id="Tableau1">
        [...]
    </table>
</table-wrap>
<p content-type="table-caption">Table 1</p>
<p content-type="table-legend">Table 1. Comparison of factors between the non-stenosis group and the atherosclerotic stenosis group.</p>
```

<br />

## Référence des images

### Des variations dans l'identifian `rid`

```rid=
    figX
    figureX
    FigureX
```

### Exemple

Article Aljabri
```xml
<xref rid="fig1">
    <underline>Figure 1</underline>
</xref>
```

Article Kernbach 

```xml
<xref rid="figure1">
    <underline>Figure 1</underline>
</xref>
```

Article Arnold
```xml
<xref rid="Figure1">
    <underline>figure 1</underline>
</xref>
```



----

## Example JATS4R image avec DOI

[source](https://jats4r.org/display-objects-figures-tables-boxed-text-etc/#example-3-a-figure-with-alternative-graphical-representations)

```xml
<fig id="elementa.000120.f001" position="float">
      <object-id pub-id-type="doi">10.12952/journal.elementa.000120.f001</object-id>
      <label>Figure 1. </label>
      <caption><title>Map of the study area and location of sampling sites in 2013 and 2014.</title>
           <p>Samples were taken in (A) Kanajorsuit Bay, Greenland (N 64.44632, W 51.57724), between 27 March and 5 April, 2013, and in (B) Kobbefjord, Greenland (N 64.15340, W 51.42275), between 12 and 21 March, 2014.</p></caption>
     <graphic position="float" mimetype="image" xlink:type="simple" xlink:href="journal.elementa.000120.f001.png"/>
</fig>
```

