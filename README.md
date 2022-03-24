# Métopes & JATS


## 1. Problèmes Métopes dans la production du JATS

voir les issues



## 2. Balises à ajouter manuellement pour un JATS riche (non présentes dans Métopes)

Voir document dédié [balises-ajout-manuel-pour-JATS-riche.md](./balises-ajout-manuel-pour-JATS-riche.md)

* Ajout des ORCIDs (lorsque les auteurs n'ont pas d'IDREF)

* Ajout des identifians ROR dans les affiliations

* journal-meta

* DOI

* Volume, Issue, Page

* licence `<persmissions>`

* Corresponding author (pour indique l'email)

* Ethics Statements

* Data Availability (le cas échéant)

* Declaration of interest



## 3. Correspondance teminologique entre le menu de Métopes (Word) et les bases JATS

 `<label>` doit contenir l' "identitiant littéraire" de l'image, "Figure 2". 

`<caption>` doit contenir la légende.

```xml
<fig id="fig1">
    <label>Figure 1.</label>
    <caption><p>Flow diagram.</p></caption>
    <graphic xlink:href="data/2022-01-21__article_test__dharamsi-fig1.jpg"/>
</fig>
```

```xml
<fig id="elementa.000120.f001" position="float">
      <object-id pub-id-type="doi">10.12952/journal.elementa.000120.f001</object-id>
      <label>Figure 1. </label>
      <caption><title>Map of the study area and location of sampling sites in 2013 and 2014.</title>
           <p>Samples were taken in (A) Kanajorsuit Bay, Greenland (N 64.44632, W 51.57724), between 27 March and 5 April, 2013, and in (B) Kobbefjord, Greenland (N 64.15340, W 51.42275), between 12 and 21 March, 2014.</p></caption>
     <graphic position="float" mimetype="image" xlink:type="simple" xlink:href="journal.elementa.000120.f001.png"/>
</fig>
```
[source JATS4R](https://jats4r.org/display-objects-figures-tables-boxed-text-etc/#example-3-a-figure-with-alternative-graphical-representations)


