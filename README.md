
# Métopes & JATS


[1. Problèmes Métopes dans la production du JATS](#1-problèmes-métopes-dans-la-production-du-jats)

[2. Balises à ajouter manuellement pour un JATS de qualité (manquantes à Métopes)](#2-balises-à-ajouter-manuellement-pour-un-jats-de-qualité-manquantes-à-métopes)

[3. Correspondances teminologiques entre le menu de Métopes (word) et les bases JATS](#3-correspondances-teminologiques-entre-le-menu-de-métopes-word-et-les-bases-jats)

[4. Problèmes rencontrés dans les JATS envoyés](#4-problèmes-rencontrés-dans-les-jats-envoyés)

[5. Vers une validation des recommandations du JATS4R](#5-vers-une-validation-des-recommandations-du-JATS4R)

<br />
<br />


## 1. Problèmes Métopes dans la production du JATS


* Les mots-clés traduits, dans une langue différente de l'article, apparaissent en double : une fois en format structuré et une 2e fois directement après la balise `<body>`, ce qui crée une erreur DTD.

Article dharamsi
fichier `2022-01-25-10h30__article_test__dharamsi__JATS.xml`
```xml
<kwd-group kwd-group-type="author-keywords" xml:lang="fr">
    <kwd>Électroencéphalogramme</kwd>
    <kwd>Télé-EEG</kwd>
    <kwd>EEG</kwd>
</kwd-group>
```
```xml
<body>Mots-clés : Électroencéphalogramme, Télé-EEG, EEG
    <p>Acknowledgments. This work was conducted under the auspices of the IBM Science for Social Good initiative.</p>
```

* Lorsqu'une adresse email est indiquée pour un auteur, elle est dupliquée à chacun les auteurs dans la TEI et absente de tous les auteurs dans le JATS
 
Article dharamsi TEI
```xml
<byline style="auteur_Courriel">
    <email>
        <ref target="mailto:auteur@duckduckgo.com">auteur@duckduckgo.com</ref>
    </email>
</byline>
<docAuthor style="txt_auteur">Payel DAS</docAuthor>
<byline style="auteur_Courriel">
    <email>
        <ref target="mailto:auteur@duckduckgo.com">auteur@duckduckgo.com</ref>
    </email>
</byline>
```

Article dharamsi JATS
```xml
<contrib contrib-type="author">
    <name>
        <surname>DHARAMSI</surname>
        <given-names>Tejas</given-names>
    </name>
    <aff/>
</contrib>
<contrib contrib-type="author">
    <name>
        <surname>DAS</surname>
        <given-names>Payel</given-names>
    </name>
    <aff/>
</contrib>
```


* Balise `<article>` ne possède pas les namespace

```xml  
<article article-type="research-article" dtd-version="1.2" specific-use="ojs-display" xml:lang="en">
```

JATS4R rajoute les éléments suivants
```xml  
<article xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:mml="http://www.w3.org/1998/Math/MathML" xmlns:ali="http://www.niso.org/schemas/ali/1.0/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" article-type="research-article" dtd-version="1.2" specific-use="ojs-display" xml:lang="en">
```


<br />
<br />

## 2. Balises à ajouter manuellement pour un JATS riche (manquantes à Métopes)

* Ajout des ORCIDs des auteurs (nécessaire pour les auteurs qui n'ont pas de IDREF)

```xml
<contrib-id contrib-id-type="ORCID">0000-0001-6042-1358</contrib-id>
    <name>
        <surname>Diamanti</surname>
        <given-names>Luca</given-names>
    </name>
    <aff>
        <xref ref-type="aff" rid="aff02"/>
        <xref ref-type="aff" rid="aff01"/>
   </aff>
</contrib>
```


* Ajout des identifians ROR dans les affiliations

```xml
 <aff id="aff01">
    <institution-wrap>
        <institution-id institution-id-type="ROR">04tfzc498</institution-id>
        <institution>Neuroradiology Department, Advanced Imaging and Radiomics Center, Istituto di Ricovero e Cura di Carattere Scientifico (IRCCS) Mondino Foundation, Pavia, Italy</institution>
     </institution-wrap>
 </aff>
```



<br />
<br />

## 3. Correspondances teminologiques entre le menu de Métopes (word) et les bases JATS

* Balise `label`

* Balise `Caption`


mémo : Label doit contenir son "identitiant littéraire" : "Figure 2" et caption la légende

```xml
<fig id="fig1">
    <label>Figure 1.</label>
    <caption><p>Flow diagram.</p></caption>
    <graphic xlink:href="data/2022-01-21__article_test__dharamsi-fig1.jpg"/>
</fig>
```


**Exemple JATS4R**

```xml
<fig id="elementa.000120.f001" position="float">
      <object-id pub-id-type="doi">10.12952/journal.elementa.000120.f001</object-id>
      <label>Figure 1. </label>
      <caption><title>Map of the study area and location of sampling sites in 2013 and 2014.</title>
           <p>Samples were taken in (A) Kanajorsuit Bay, Greenland (N 64.44632, W 51.57724), between 27 March and 5 April, 2013, and in (B) Kobbefjord, Greenland (N 64.15340, W 51.42275), between 12 and 21 March, 2014.</p></caption>
     <graphic position="float" mimetype="image" xlink:type="simple" xlink:href="journal.elementa.000120.f001.png"/>
</fig>
```
[source](https://jats4r.org/display-objects-figures-tables-boxed-text-etc/#example-3-a-figure-with-alternative-graphical-representations)

<br />
<br />

## 4. Problèmes rencontrés dans les JATS envoyés à la production

* Déclaration d'image sans label

Article Liu 
```xml
<p>
    <graphic xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="data/neuro_01_08_table3.jpg" />
</p>
```

* Une balise autofermante inutile

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

* id et rid de table qui ne correspondent pas

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


## 5. Vers une validation des recommandations du JATS4R

### Fichier aljabri

* la balise `<body>` ne peut pas contenir directement des <sec> ... les mots clés sont à placer dans un `<p>`

* `<fn-type="other">` deux identifiants fn

* sur les références bibliographiques

 > `<mixed-citation>` does not have a publication-type attribute.

 > Where possible `<mixed-citation>` should always have a child `<person-group>` which hold the contributors for that work, with their role being specified in the attribute person-group-type. This `<mixed-citation>` does not have a `<person-group person-group-type="...">`.

### Fichier LIU

l'exposant provoque une référence sans déclaration dans le JATS : 

```xml
<xref rid="a">
    <underline>
    <sup>a</sup></underline>
</xref>
```

LIU : 
Table 1 : comparison of facors between the non ... 
le contenu de la cellule (col="p", row = CRP) est vide