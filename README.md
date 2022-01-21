
# Métopes et JATS : notes de travail


## Declaration des images

### Problème majeur : il manque l'identifiant 

La déclaration d'une figure doit contenir un identifiant, nécessaire pour la validation du DTD. exemple : 

```xml
<fig id='monIdentifiant'>
    <label>Figure 1.</label>
    <caption>
        <p>Figure 1. Receiver operating characteristic (ROC) curve of the monocyte/high-density lipoprotein ratio (MHR) for intracranial and extracranial atherosclerotic stenosis.</p>
    </caption>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/neuro_01_08_fig1.jpg" />
</fig>
```

Or aucun n'apparait dans la déclaration des images. (Par contre on en trouve dans les tables `<table id="Tableau1">`)



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

**Examples JATS4R**

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

**Exemple de la balise `<caption>` en sortie de Métopes**

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


### Problèmes liés

**déclaration d'image sans label**

Article Liu 
```xml
<p>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/neuro_01_08_table3.jpg" />
</p>
```


**une image non déclarée**

Liu 
> Erwan commentaire : image "neuro_01_08_table2.jpg" n'est déclaré nulle part bien qu'étant présent parmi les images dépendentes et étant fait "référence" dans le jats 


**Une balise autofermante inutile**

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

**Exemple**

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

Les id et rid ne correspondent pas

Article Liu
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

## Valider le schématron de JATS4R si possible

Fichier aljabri

* la balise `<body>` ne peut pas contenir directement des <sec> ... les mots clés sont à placer dans un `<p>`

* `<fn-type="other">` deux identifiants fn

* sur les références bibliographiques

 > `<mixed-citation>` does not have a publication-type attribute.

 > Where possible `<mixed-citation>` should always have a child `<person-group>` which hold the contributors for that work, with their role being specified in the attribute person-group-type. This `<mixed-citation>` does not have a `<person-group person-group-type="...">`.



<br />
<br />

----

## Affichage

### exposant

cela provoque une référence sans déclaration dans le JATS : 
LIU 
```xml
<xref rid="a">
    <underline>
    <sup>a</sup></underline>
</xref>
```

### pb affichage dans le PDF 

LIU : 
Table 1 : comparison of facors between the non ... 
le contenu de la cellule (col="p", row = CRP) est vide