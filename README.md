
# Métopes et JATS : notes de travail


## Declaration des images


### Problème balises `<label>` & `<caption>`

mémo : Label doit contenir son "identitiant littéraire" : Figure 2 et caption la légende, laquelle peut contenir un titre avec `<title>` [voir exemple JATS4R](#example-jats4r-image-avec-doi)


Article Kernbach
```xml
<graphic xlink:href="data/emergneurol_01_01_kernbach_fig01.jpg" xmlns:xlink="http://www.w3.org/1999/xlink"/>
Figure 1.</p>
<fig>
    <label>Meta-topologies in primary brain tumors
        <bold>.</bold></label>
</fig>
```

 > Commentaire Erwan : Figure 1. devrait être à l'intérieur de `<label>` et `Meta-topologies in primary brain tumors` dans `<caption>`


### Présence de la balise `<caption>`

Article Liu 
```xml
<fig>
    <label>Figure 1.</label>
    <caption>
        <p>Figure 1. Receiver operating characteristic (ROC) curve of the monocyte/high-density lipoprotein ratio (MHR) for intracranial and extracranial atherosclerotic stenosis.</p>
    </caption>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/neuro_01_08_fig1.jpg" />
</fig>
```


### Problèmes mineurs : une déclaration d'image sans label

Article Liu 
```xml
<p>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/neuro_01_08_table3.jpg" />
</p>
```


### Problème mineur : une image non déclarée

Liu 
> Erwan commentaire : image "neuro_01_08_table2.jpg" n'est déclaré nulle part bien qu'étant présent parmi les images dépendentes et étant fait "référence" dans le jats 


### Problème mineur : une balise autofermante inutile 

également : 
- `Figure 4` dans label 
- `Brain tumor  ...` dans caption
- balise `<graphic ` à placer à l'intérieur de `<fig>`

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
<br />

## Référence des images

### Des variations dans l'identifian `rid`

```
rid=
    fig1
    figure1
    Figure1
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



<br />
<br />

## Déclaration et référence des tables


Dans l'article Liu il est fait référence à 4 tables. La première est bien déclarée (cf infra); la seconde est par contre absente, sans déclaration, et les deux suivantes le sont en tant que figure.

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
<br />

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

