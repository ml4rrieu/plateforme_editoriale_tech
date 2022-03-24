# Balises à ajouter manuellement pour un JATS riche (manquantes à Métopes)

`màj 2022-03-22`

* Chaîne

Métopes (.docx) -> Métopes (TEI/XML) -> sublime (TEI/JATS)> indent XML -> ajouts manuels -> validator JATS4R -> modif pour JATSParserPlugin > Submission OJS -> chargement images -> chargement Galley PDF & XML


* Utilisations du JATS
    * JATS OAI
    * JATS pour CrossRef
    * JATS pour pubmed


## Journal-meta

Nécessaire pour valider la DTD : balise journal-id et issn

```xml
<journal-meta>
    <journal-id journal-id-type="publisher">Emerging Neurologist</journal-id>
    <issn pub-type="ppub">xxxx-xxxx</issn>
    <issn pub-type="epub">xxxx-xxxx</issn>
    <publisher>
        <publisher-name>Université de Paris</publisher-name>
    </publisher>
</journal-meta>
```

nota : Métopes ajoute une balise `<issn\>`

#question : faut il intégrer d'autres abréviations de notre revue ? `journal-id-type` peut recevoir plusieurs valeurs : "nlm-ta" ou "id-type" ? 



<br />
<br />

## Article-meta

### DOI 


```xml
<article-meta>
   <article-id pub-id-type="doi">10.1234/emerg.neurol.54fg</article-id>
   ...
```

Il est à générer et récupérer dans OJS, dans l'onglet publication d'une soumission.


### Identifiants ORCID 


```xml
<article-meta>
    ...
    <contrib contrib-type="author">
    <contrib-id contrib-id-type="ORCID">0000-0002-8968-7050</contrib-id>
    <name>
        <surname>DHARAMSI</surname>
        <given-names>Tejas</given-names>
    </name>
    <aff>
        <xref ref-type="aff" rid="aff01"/>
    </aff>
    </contrib>
```


### Identifiants ROR 

```xml
<article-meta>
    ...
    <contrib-group>
        ...
         <aff id="aff01">
            <institution-wrap>
                <institution-id institution-id-type="ROR">04tfzc498</institution-id>
                <institution>Neuroradiology Department, Advanced Imaging and Radiomics Center, Istituto di Ricovero e Cura di Carattere Scientifico (IRCCS) Mondino Foundation, Pavia, Italy</institution>
             </institution-wrap>
         </aff>
    </contrib-group>
```

### Volume, Issue, Page


```xml
<article-meta>
    ...
</pub-date>
    <volume>1</volume>
    <issue>1</issue>
    <fpage>6</fpage>
    <lpage>14</lpage>
    ...
</article-meta>
```


### Date de publication

```xml
<article-meta>
    ...
    <pub-date publication-format="electronic" date-type="pub" iso-8601-date="2022-04-01">
        <day>01</day>
        <month>04</month>
        <year>2022</year>
    </pub-date>
```

### Dates soumission,

 :::info
 2022-03-10 : a été inséré dans Métopes XMLmind : cliquer sur le "+" après publicationStmt
 :::
```xml
<article-meta>
    ...
    <history>
        <date date-type="received" iso-8601-date="2021-11-01">
            <day>01</day>
            <month>11</month>
            <year>2021</year>
        </date>
    <date date-type="accepted" iso-8601-date="2022-01-01">
        <day>01</day>
            <month>01</month>
            <year>2022</year>
    </date>
    </history>
```

possible d'avoir une autre date `acceptation`, `rev-receive`

### Licence CC-BY


```xml
<article-meta>
    ...
    <permissions>
         <copyright-statement>© 2022 The Author(s)</copyright-statement>
         <copyright-year>2022</copyright-year>
         <copyright-holder>The Authors</copyright-holder>
         <license license-type="open-access">
                <ali:license_ref start_date="2022-01-01">https://creativecommons.org/licenses/by/4.0/</ali:license_ref>
              <license-p>This is an open-access article distributed under the terms of the <ext-link ext-link-type="uri" xlink:href="https://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution License </ext-link>, which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly credited.</license-p>
         </license>
    </permissions>
```
[documentation JATS4R](https://jats4r.org/permissions/#examples)
    
### Declaration of interest
                                                           

```xml
<article-meta>
    ...
    <author-notes>
        <fn fn-type="coi-statement">
            <p>Competing Interests: The authors have declared that no competing interests exist.</p>
        </fn>
    ...
    </author-notes>
```
nota : engendre une erreur ds le Schematron, qui recommande `fn-type="COI-statement"` qui engendre lui même une erreure DTD TODO signaler a JATS4R
                               

:::info
Si un COI est à déclarer pour un auteur en particulier alors le modèle change cf. [exemple](https://jats4r.org/conflict-of-interest-statements/#examples)
:::
    
#quesion : est-ce à répliquer dans le body ? 

    
### Corresponding Author

`corresp="yes"` peut être ajouté dans Métopes (2022-03-10)
```xml
<article-meta>
    <contrib-group>
        <contrib contrib-type="author" corresp="yes" xlink:type="simple">
            <name name-style="western">
                <surname>Lin</surname>
                <given-names>Jennifer</given-names>
            </name>
             <aff>
                <xref ref-type="aff" rid="aff02"/>
                <xref ref-type="aff" rid="aff01"/>
            </aff>
            <xref rid="cor001" ref-type="corresp">*</xref>
        </contrib>
    </contrib-group>
    <author-notes>
    ...
    <corresp id="cor001">
        * E-mail:
        <email xlink:type="simple">jlin@crossref.org</email>
    </corresp>
    </author-notes>
```


[documentation JATS4R](https://jats4r.org/permissions/#context)



### Funding
    
:::info 
a priori ils seront peu présents. Choix de les intégrer en texte brut dans Statements, et non en format structuré.
:::

dans article-meta après abstracrt
Plus compliqué si des financements sont à préciser pour différents auteurs (comme pour les COI)
à placer juste après les keywords
```xml
<funding-group>
    <award-group id="ag1">
        <funding-source country="CN">
            <institution-wrap>
                <institution-id institution-id-type="doi" vocab="10.13039/open-funder-registry" vocab-identifier="10.13039/open-funder-registry">
                    10.13039/501100001809</institution-id>
                <institution>National Natural Science Foundation of China</institution>
            </institution-wrap>
        </funding-source>
        <award-id>61505139</award-id>
        <award-id>61675152</award-id>
    </award-group>
</funding-group>
```
[documentation JATS4R](https://jats4r.org/funding/#examples)



<br />
<br />
    
## Body & Back
    
    

### Ethics Statements

A intégrer dans le `<body>` pour affichage et dans le `back` pour JATS4R
    

```xml
<back>
...
<sec sec-type="ethics-statement">
    <title>Ethics Statement</title>
    <sec sec-type="ethics-consent-to-publish">
    <title>Patient consent for publication</title>
    <p>Not required.</p>
</sec>
<sec sec-type="ethics-approval">
    <title>Ethics approval</title>
    <p>Not required.</p>
</sec>
</sec>
</back>
```
[exemple 1 du JATS4R](https://jats4r.org/ethics-statements/#examples)
    
nota : dans l'exemple de JATS4R les balises `<strong>` provoquent une erreur DTD
    

### Data Availability (non systématique)

#question : est-ce que cela s'affichera, ou faut il le répliquer dans le body ? 
    

Les jeux de données sont à inclure dans `<back>` et dans les références bibliographiques. Des renvoies sont à inclure avec `<xref `

```xml
<back>
    ...
    <sec sec-type="data-availability">
        <title>Data Availability</title>
        <p>The data analysis file and all annotator data files are available in the Figshare repository, 
          <ext-link ext-link-type="uri" xlink:href="https://doi.org/10.6084/m9.figshare.1285515">https://doi.org/10.6084/m9.figshare.1285515</ext-link>
         <xref ref-type="bibr" rid="bibl11">[32]</xref>. The measured and simulated Euler angles, and the simulation codes are available from the Dryad database, <ext-link ext-link-type="uri" xlink:href="https://doi.org/10.5061/dryad.cv323">https://doi.org/10.5061/dryad.cv323</ext-link> <xref ref-type="bibr" rid="bibl12">[33]</xref>.
        </p>
    </sec>
    
</back>
```
[doc JATS4R](https://jats4r.org/data-availability-statements/)

## Mémo

### pour les figures

Vérifier pour les fig que le JATS est organisé selon le modèle
```xml
<fig> 
  <label> Figure 1. </label> 
  <caption> 
    <p> Receiver blabla… </p> 
  </caption> 
<graphic xlink : href = … /> 
</fig> 
```


<!--
## Licence

```xml
```
-->

