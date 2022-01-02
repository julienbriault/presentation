---
marp: true
theme: gaia
markdown.marp.enableHtml: true
---

<style>
    section {
    background-color: #fefefe;
    color: #333;
    }
    img[alt~="center"] {
    display: block;
    margin: 0 auto;
    }
    blockquote {
    background: #ffedcc;
    border-left: 10px solid #d1bf9d;
    margin: 1.5em 10px;
    padding: 0.5em 10px;
    }
    blockquote:before{
    content: unset;
    }
    blockquote:after{
    content: unset;
    }
</style>

<!-- paginate: false --->
<!-- header: "" -->
<!-- _backgroundColor: #d74946 -->
<!-- _color: white -->

<br>

# Soutenance de fin d'étude
**Comprendre pour mieux placer efficacement la sécurité dans une approche DevOps** 
<br>
Julien Briault
Promotion 2021/2022 EISI 22.3 CS | IPSSI

---
<!-- paginate: true --->
<!-- header: _IPSSI/Normation_  -->
## Avant-propos

Les sources (code) sont disponibles sur [Github](https://github.com/julienbriault/presentation).

Cette présentation est sous licence **CC BY-SA FR 2.0** (tout comme le mémoire).

Ainsi chacun est libre de le *diffuser*, de le *modifier*, sans oublier de **citer** l'auteur !

“*L’Homme et sa sécurité doivent constituer la première préoccupation de toute aventure
technologique*” - **Albert Einstein**

---

## ~$ [whoami](https://blog.jbriault.fr/whoami/)

**Julien BRIAULT**

- System Engineer chez **Rudder/Normation**
- Responsable Informatique aux [Restos du Coeur](https://www.restosducoeur.org/) (~ 1 an)
- Auteur principal sur [blog.jbriault.fr](https://blog.jbriault.fr) 
- Développeur C/Golang/Python

**#mao-dj** **#dev**  **#net** **#automation** **#open-source** **#free-software**

![bg fit right:40%](img/julien.png)

---
<!-- header: "" -->
![bg](img/set.png)


---

# Rudder, qu'ésaquo ?

- Entreprise éditrice de logiciel **Open Source** du même nom
  - Basée à Paris (3ème proche de République)
  - A une dizaine d'années
  - 14 collaborateurs (dont une majorité de devs)
 
- Créatrice du **[DevOps Rex](https://2019.devopsrex.fr/)** (conférence autour du DevOps)

- Le logiciel :
  - Seul acteur *français* et *européen* dans la gestion de configuration et sa mise en conformité des systèmes.
---
<!-- header: _IPSSI/Normation_  -->
# Sommaire

- Introduction
  - Les motivations : pourquoi ce choix de sujet ?
- Conduite et démarche de recherche
- Les origines
- La sécurité dans le DevOps, oui mais comment ?
- Des solutions pour garantir cette sécurité ?
- Dans la vie, ça marche comment ?
- Conclusion
- Le futur

---
<!-- _class: lead -->
<!-- _backgroundColor: #2d409e -->
<!-- _color: white -->

# Introduction

---
# Introduction

#### Pourquoi avoir fait ce choix de sujet ?

- Sujet qui me tient à coeur
  - Contributeur à des projets comme [**naxsi**](https://github.com/nbs-system/naxsi) ou encore [**crowdsec**](https://github.com/crowdsecurity/crowdsec). Mais également [Rudder](https://www.rudder.io/)...
- Rudder est un outil qui se veut ***DevSecOps***\*
<br>

\* Terme marketing pour désigner le fait que l'outil est à destination à la fois des *ops*, des *devs* (dans une certaine mesure) et des *équipes de sécu*.

---

# Introduction

#### Pourquoi avoir fait ce choix de sujet ?

- Beaucoup d'informations autour du DevOps mais peu finalement sur la sécurité dans celui-ci
- Le sujet n'est pas toujours bien compris
  - Détailler pour mieux comprendre pour installer les bonnes pratiques de sécurité
- Une réponse souvent logique mais pas évidente à comprendre : **DevSecOps**
---

# Introduction

#### Pourquoi avoir fait ce choix de sujet ?

Des programmes de recherche autour du DevOps n'incluant pas la sécurité et mettant l'accent sur les performances.

Exemple : **DORA** (Devop Research and Assessment) de **Google**.

---
<!-- _class: lead -->
<!-- _backgroundColor: #2d409e -->
<!-- _color: white -->
# Conduite et démarche de recherche
---

# Conduite et démarche de recherche

- L'acquisition des connaissances se traduit par l'***intuition*** et l'***expérience personnelle***.

- J'entends par :
  - L'**intuition** : connaissance immédiate du sujet abordé
  - L'**expérience personnelle** : l'essai et l'errreur 

- Cette démarche ne resulte en rien d'un *raisonnement logique* (au sens scientifique du terme).

---
<!-- _class: lead -->
<!-- _backgroundColor: #d25a2e -->
<!-- _color: white -->

# Les origines
---
# Les origines

![width:700px](img/devops.png)

\**Image tirée du talk de *Denis GERMAIN* nommé **[SRE](https://www.youtube.com/watch?v=C8bcFLmZzAY)**.*


---

La sécurité, encore une fois oublié... Vraiment ?

- Analyse des concepts fondamentaux
  - **Kaizen** (amélioration continue)
  - **Scrum** (méthode : comment collaborer ?)
  - **Lean Startup** (constuire, mesurer, apprendre)

---
<!-- _class: lead -->
<!-- _backgroundColor: #2d409e -->
<!-- _color: white -->
# Rentrer dans le vif du sujet
--- 
# La sécurité, oui mais comment ?

- Reprendre les différentes étapes du DevOps (*plan*, *build*, *release*, *deploy*, *operate*, *monitor*).
  - Comprendre
  - Déterminer les actions pour la sécurité déjà apportés
  - Améliorer
---

- Apporter des solutions méthodologiques et techniques à chaque pan du DevOps.
- Mais, ce n'est pas que de la technique...
  - D'après le **DEDSORD**, il est souvent oublié le point de vu *business* (des histoires de ROI par exemple).
  - Le **BIA** (Business Impact Analysis) plus qu'important mais trop souvent oublié

---
<!-- _class: lead -->
<!-- _backgroundColor: #137a66 -->
<!-- _color: white -->

# Finalité
---
# Des solutions

Pour garantir la sécurité d'un environnement DevOps, on va retrouver :
- Des questions posées (par exemple : "est-ce testable ?")
- Des solutions techniques
- De la méthodologie

Le choix des solutions c'est principalement basé sur une analyse de receuils de bonnes pratiques et d'expériences personnelles/professionnelles.

---
#### La collaboration
* L'équipe sécurité travaille avec les développeurs (l'équipe "DevOps")
  * Dès le début des projets (shift security to the left)
  * Rédiger des user stories orientées sécurité (> scénarios d'abus)
  * Partage d'expérience (communication ++)
* Aller plus loin :
  *  Nomination de **security champions**
      \+ Scalabilité
      \+  Diffusion naturelle des bonnes pratiques

---

#### La formation/sensibilisation

- Formation au développement sécurisé
  - OWASP Top 10
  - CWE Top 25
  - Certifications : *GWEB*, *CSSLP*, *CASE*
- Sensibilisation
  - Par l'équipe sécurité
    - Démos de piratage (DVWA, Metasploitable)
  - E-Learning
  - OWASP Top 10 (bis)

---
<!-- _class: lead -->
<!-- _backgroundColor: #531f61 -->
<!-- _color: white -->

# Le futur
---
# Le futur
#### Le retour aux sources

- Premier CDI *signé*
- Poste : **Network Engineer SRE** ![bg fit right:40%](img/deezer.png)

**#network** **#sre** **#core-infra** **#automation**

---
# Le futur

Créer une startup autour du projet [**Ichigo**](https://github.com/ichigoproject).

- Projet à orientation **NetDevOps**
  - Automatisation
  - Déploiement
  - Audit
  - Sauvegarde

![bg fit right:40%](img/ichigo.png)

---
<!-- header: "" -->
![bg left:33%](img/set-2.jpg)
<br>
# Merci pour votre écoute !
Place aux questions !

---
