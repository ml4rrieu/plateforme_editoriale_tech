
# Métopes & JATS


## 1. Problèmes Métopes dans la production du JATS v

voir les issues



<!--

TITRE Mots-clés traduits apparaissent en double

contenu  
Les mots-clés traduits, dans une langue différente de l'article, apparaissent en double : une fois en format structuré et une 2e fois directement après la balise `<body>`, ce qui crée une erreur DTD.


exemple `2022-01-25-10h30__article_test__dharamsi__JATS.xml`
```xml
<kwd-group kwd-group-type="author-keywords" xml:lang="fr">
    <kwd>Électroencéphalogramme</kwd>
    <kwd>Télé-EEG</kwd>
    <kwd>EEG</kwd>
</kwd-group>
```
```xml
<body>Mots-clés : Électroencéphalogramme, Télé-EEG, EEG
    <p>Acknowledgments. This work was conducted under the auspices of the IBM Science for Social Good initiative.</p>
```

-->


## 2. Balises à ajouter manuellement pour un JATS riche (non présentes dans Métopes)

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

* Volume, Issue

introuvables dans le JATS

* Dates de soumission (et acceptation ? )
 
non trouvable dans Métopes


* Declaration of interest

une seule déclaration pour l'ensemble des auteurs
```xml
<author-notes>
    <fn fn-type="coi-statement">
        <p>Competing Interests: The authors have declared that no competing interests exist.</p>
    </fn>
</author-notes>
```

plusieurs déclarations selon les auteurs, cf. [jats4r.org](https://jats4r.org/conflict-of-interest-statements/#examples)



<br />
<br />

## 3. Correspondances teminologiques entre le menu de Métopes (Word) et les bases JATS

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


