Conventions
===========



I - Avant-Propos
=================
Les conventions présentes dans ce document sont très largement inspirées des conventions déefinies par les sites http://www.loribel.com et http://www.cyberzoide.net , qui sont des adaptations des conventions de Sun.

- Les conventions de codages d'[Oracle](http://www.oracle.com/technetwork/java/javase/documentation/codeconvtoc-136057.html) 
- La convention de nommage de [Loribel](http://www.loribel.com/java/normes/nommage.html)
- le JavaStyle d'[Hugo Etiévant](http://cyberzoide.developpez.com/java/javastyle/)

Ces guides ont été compilés dans un premier document co-écrit avec Gaël Salaün dans le cadre de notre travail au [LIUM](http://www-lium.univ-lemans.fr/).

Il a été ré-adapté et amélioré au fur et à mesure d'expériences afin de mieux coller aux exigences des projets JavaEE.


II - Introduction
==================

Selon le site de [Sun](http://www.oracle.com/technetwork/java/codeconv-138413.html) voici les arguments pour définir des conventions de programmation :

> Code conventions are important to programmers for a number of reasons:
> 
> - 80% of the lifetime cost of a piece of software goes to maintenance.
> - Hardly any software is maintained for its whole life by the original author.
> - Code conventions improve the readability of the software, allowing engineers to
> understand ­new code more quickly and thoroughly.
> - If you ship your source code as a product, you need to make sure it is as well
> packaged and clean as any other product you create.

Le document de conventions a plusieurs rôles :

 - centralise l'information
 - permet de prendre des décisions claires quand des ambiguités se présentent
 - peut être étendu afin de mieux répondre aux besoins

Et tout cela dans un but :
 
 - rendre homogène les développements de différents programmeurs ou équipes
 - rendre la maintenance plus facile


II - Organisation des projets
=============================


> **Bonne pratique :** Gardez à l'esprit la simplicité. Veillez à ce pas sur-découper un projet si celà n'est pas nécessaire !!!


Nommage : 
L'idée ici est encore de rester simple : 

Une application sera découpée en : 

- Projet-gui : pour la partie B
- Projet-service : Pour la partie publication de services
- Projet-business : 

ou :

- Projet-backend
- Projet-frontend
- 

Une autre ,


III - Organisation interne des projets
==============================
Un projet de développement logiciel est organisé en de multiples répertoires qui doivent adopter la structure suivante :

a) Projet sous Maven
----------------------------

La convention à respecter pour les nommage sous Maven

Pour l'externalisation des ressources, se reporter aux documents de bonnes pratiques.


b) Projet sous ANT (ou autre)
------------------------------

Cette organisation est plus a suivre dans un contexte de projet interne.


    PROJET /                 racine du projet
          src/               répertoire des sources
            |- test/         répertoire des tests
            |- java/         répertoire 
          lib/               librairies utiles au projet
          web/               contenu web du projet : JSP, HTML, 
            |- WEB-INF/      descripteur de déploiement (web.xml), configuration applicative.
            |- css/          feuilles de style
            |- scripts/      scripts Javascripts
            |- images/       images
            |- media/        autres ressources (PDF, etc.)
          doc/               javadoc et documentation du projet
          bin/               classes Java compilées
          dist/              contenu du WAR packagé.
          build.xml          fichier de build ANT
          build.properties   fichier de conf ANT
          LICENCE            Licence sous laquelle l'application est distribuée.
          readme.txt         Description du projet

IV - Gestion des versions
=========================
Les numeros de versions des applications développées au LIUM suivent le schéma suivant : `major.minor.revision`.

*Par exemple :* 2.1.13

où:

 - **major** : un nombre incrémenté à chaque fois qu'il y'à un saut significatif dans les fonctionnalités.
 - **minor** : un nombre incrémenté seulement lors de fonctionnalités mineures ou lors de correctifs de bugs significatifs.
 - **revision** : un nombre incrémenté quand des correctifs de bugs mineurs sont mis en place.


La première version publiée d'un logiciel sera donc la 1.0.0. Toutes les versions en dessous de cette valeur sont considérées comme des versions alpha ou beta, c'est à dire, des versions à usage interne, des versions de tests ou encore des versions qui ne sont pas assez stables pour un déploiement général.

De la même manière, la version 0.9.0 doit être utilisée pour indiquer une version beta. Résumé rapide des étapes de développement :

- **Pre­alpha** : Toutes les fonctionnalités ne sont pas encore développées. Démontre la faisabilité et la structure basique de l'application. (version < 0.7.x)
- **alpha** : Toutes les fonctionnalités sont développées et l'application est prête pour les tests. (version 0.8.x)
- **bêta** : version qui a passé les tests système et les tests de régression et qui est maintenant prête pour les bêta­tests, c'est à dire, des tests en conditions réel avec des vrais utilisateurs. (version 0.9.x)
- **Release** : Produit final (version >= 1.0.0). N.B. :

Il existe d'autres termes spécifiques à certains projets, entreprises ...
 - EA : Early Access, version Alpha 

Chez Eclipse par exemple, on a les termes suivantes.

 - Milestone (Mx) : version en cours de développement. Probablement pas pleinement fonctionnelle. Pas sûr qu'elle soit stable. Comporte encore potentiellement des problèmes.
 - Release Candidate (RCx). version Bêta en cours de tests et correction mineure et potentiellement candidate pour devenir la première version Release (Eclipse notamment utilise cette numérotation)
 - GA (General Availability) : première version "release" offcielle. Stable et pleinement fonctionnelle.
 - Service Release (SR) : mise à jour corrective sur la version release. plusieurs versions : SR1, SR2, etc.


Avec Maven, on parle de version SNAPSHOT pour les versions en cours de développement.

    1.0-SNAPSHOT
En prenant soin `1.0-SNAPSHOT` de  

Ce chapitre est une copie de ce que l'on peut trouver ici :
 
 - Gestion des numéros de version : http://en.wikipedia.org/wiki/Software_version
 - Les étapes de développement : http://en.wikipedia.org/wiki/Development_stage

V - Subversion
==============


Les utilisateurs anonymes peuvent y accéder en lecture, les authentifiés peuvent y écrire.

Les conventions reconnues de Subversion s'y appliquent.

Pour les différentes composantes d'un même projet, le projet devra porter un préfixe montrant à quel projet global il appartient.

> *Exemple* : pour les projets Toto, il faut utiliser le préfi xTotr  :Totor_Client, Totor_Server,n, ...

L'utilisation de subversion dans Eclipse se fait via le plugin subclispe : http://subclipse.tigris.org

Voir l'Annexe I pour des détails sur la gestion des branches et tags.

VI - Formattage
===============
Le formattage du code consiste en son écriture aéré et homogène.

Il est recommendé de ne pas excédé 2000 lignes dans un fichier Java et de ne pas dépasser les 80 colonnes.

A) Blocs
--------
L’entrée dans un nouveau bloc fils impose le rajout d’un niveau d’indentation. Deux blocs de
même niveau doivent débuter sur la même colonne (même niveau d’indentation).

Tout bloc est délimité par des accolades. L’accolade ouvrante doit être placée en fin de ligne,
à la suite d’un espace, après l’instruction/méthode/classe créant le bloc. L’accolade fermante
doit être placée en début d’une ligne vierge à la suite de la dernière instruction du bloc. 

**A ne pas faire**

    void myMethod 
    {
      int level;
    }
    ...
    while(true) { println("foobar"); }
    ...
    for(i = 1; i<10;i++) {
      println("%d\n", i)
    }

**A Faire :**

    void myMethod {
      int level;
    }
    ...
    while(true) {
      println("foobar");
    }
    ...
    for(i = 1; i<10;i++) {
      println("%d\n", i)
    }


B) Taille des lignes
--------------------
Une ligne ne doit pas exceéder 80 colonnes (indentations comprises).
Pour permettre l’écriture de code, il peut alors s’avérer nécessaire de revenir à la ligne à la
suite d’une virgule séparant différents paramètres d’une méthode, où à la précédence d’un
opérateur par exemple, et à l’extérieur de toute parenthèse, de préférence.

    setMyVarOfMyClass(myVeryLongVar1, MyVeryLongExpression1, myVeryLongVar2, myLonguestExpression2, 
                       myLonguestVariable3, myLonguestExpression3, myLonguestVariable4);



VII - Conventions de nommage et déclaration
===========================================

D'une manière générale, on utilisera l'anglais partout sauf pour les commentaires.

a) Packages
-----------
Le nom d'un package doit respécter les conventions suivantes : 
 
 1. Tout en **minuscule**.
 2. Utiliser seulement **[a-z], [0-9] et le point '.'**. Ne pas utiliser le tiret '-', underscore '_'
    d'espace ou d'autres caractères ($, *, accents, etc.)
 3. La convention de Sun indique que tout package doit avoir comme racine un des package suivants : 
    *com*, *edu*, *gov*, *mil*, *net*, *org* ou les deux lettres identifiants un pays (ISO 3166, 1981).

Pour mes projets, j'ai choisi un nommage du type `com.florentdupont.[Nom du Projet].*`

Il est recommandé de privilégier une programmation modulaire. Dans ce sens, les packages peuvent bien séparer ou regrouper les modules.

Une architecture modulaire permet :

 - de mieux séparer les concepts
 - une meilleure abstraction
 - une meilleure réutilisation
 - une interchangeabilité
 - facilite la maintenance du code

L'inconvénient majeur étant :
 - une intégration plus difficile

partie à revoir car un peu vieillote...


b) Classes
-----------

c) Interfaces
-------------

d) Méthodes
-----------


e) Variables
------------

f) Attributs 
------------

g) Constantes
-------------

h) Fichiers JAR
---------------

i) Inner classes
----------------

VIII - Commentaires
===================
Les commentaires sont en français.

Inutile d'en utiliser pour des usages triviaux comme des boucles, par exemple.
Inutile pour les getters et setters sauf s'ils ont un comportement qui ne soit pas standard.
Mais s'astreindre à en mettre pour les portions de code un peu délicates.
Préférer les commentaires utiles et algorithmes plutôt que les commentaires qui n'apportent aucun intérêt à la lecture.

a) Bloc de commentaire
----------------------

b) Commentaire mono-ligne
-------------------------

c) Inactivation d'une portion de code
-------------------------------------

d) Priorité entre commentaires
------------------------------

e) Cartouches
-------------

IX - Instructions
=================

a) Simple instructions
----------------------

b) Instruction de retour
------------------------

c) Structures de contrôle
-------------------------

d) Gestion des évenements
-------------------------

XXX - Annexe
============

1. Fichiers de configuration CheckStyle - PMD
---------------------------------------------
Les fichiers de configuration Checkstyle PMD correspondant aux conventions définies précedemment
sont disponibles sous http://adefinir



