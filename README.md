# Pour l'évaluation

- **Prendre 10 min à chaque fin de séance pour écrire ce qu'on a fait
    dans le fichier
    [./rapports_hebdomadaires.md](./rapports_hebdomadaires.md)**
- le rapport terminal doit être rédiger en Latex dans le répertoire
  [./rapports](rapports)

# Résolution de l'équation de Keller-Segel

## Objectif final, très ambitieux.

L'équation de Keller-Segel modélise la chimiotaxie, à savoir le
phénomène par lequel une espèce biologique (bactéries, cellules, etc.)
se déplace en fonction des espèces chimiques qui l'environnent.
<https://www.youtube.com/watch?v=ZUUfdP87Ssg>

Cette équation est en fait un système de deux EDP couplées entre elles,
décrivant la quantité de l'espèce biologique \rho(t,x) et la
concentration d'espèce chimique c(t,x). Pour la suite, nous dirons que
nous regardons des bactéries se dirigeant vers leur nutriment (du
glucose par exemple).

Les équations s'écrivent

\partial_t\rho(t,x) = \epsilon \Delta \rho(t,x) + \mathop{div}
(-\chi\rho(t,x)\nabla\c(t,x)),

\partial_t c(t,x) = k\Delta c -\lambda c -\alpha\rho(t,x) + f(t,x).

La première équation traduit le fait que les bactéries se dirigent dans
la direction privilégiée du gradient de c, avec le coefficient de
chimiotaxie \chi, et diffusent très faiblement avec le coeffcient
$\epsilon>0$. La seconde équation traduit la diffusion du nutriment,
avec un coefficient de diffusion k. Le terme -\lambda c symbolise la
dégradation du nutriment au cours du temps.  Le terme -\alpha\rho(t,x)
représente la consommation du nutriment par les bactéries.  Enfin, le
terme f(t,x) est le terme source par lequel on vient apporter des
nutriments.

## Première partie : recherche de resources, documentation

1. Commençons par l'équation portant sur c. Si on considère que
   \rho(t,x) est une donnée connue, nous avons une équation parabolique
   linéaire, de la forme

   \partial_t u - \Delta u = s(t,x),

   Trouver et synthétiser de la documentation sur ce type
   d'équation. Quelles conditions aux limites peut-on utiliser pour
   mettre en place notre boîte de Petri virtuelle ? Quel sera leur
   signification biologique ? 

   On répètera ce travail pour l'équation sur \rho (type d'équation,
   conditions aux bords).

2. Se documenter sur l'existence et le comportement des solutions du
   système.

3. Quels types de discrétisation en espace et quels schémas en temps
   peut-on envisager, en tenant compte des données \rho et c ?
   Détailler le système d'équations que l'on doit résoudre à chaque pas
   de temps, et les méthodes possibles pour le résoudre. Il est
   recommandé de séparer les équations pour les résoudre chacune avec
   une méthode adaptée.

## Deuxième partie : programmation dans un cas simplifié

L'objectif est de bien comprendre l'implémentation des méthodes, avant
de s'attaquer au problème complet. On s'intéressera d'abord à l'équation
sur c, dans le domaine 1D [0,1], en fixant l'autre inconnue à une valeur
choisie (pas forcément constante).

1. Détailler l'architecture du code à implémenter, en essayant d'avoir un code
   modulaire et extensible facilement. Entrées et sorties ? Structuration du
   code en fichiers ? Quels outils de l'ensemble scipy/numpy ?
2. Construire une solution analytique à cette équation, qui sera
   utilisée pour valider l'implémentation.
3. Programmer la résolution du problème, et vérifier cette
   implémentation à l'aide des tests de la question 2.

## Troisième partie : couplage des équations

Après avoir répété le procédé de la partie 2 avec la seconde équation,
nous allons mettre en place le lien entre les deux équations. Nous
aurons donc deux inconnues par point de discrétisation.

1. Reproduire la démarche de la deuxième partie pour implémenter un
   schéma de résolution de l'équation sur \rho

2. Utiliser ces deux schémas pour programmer la résolution du système de
   Keller-Segel.
   
3. Mettre en place un cas test qui illustrera en 1D le phénomène de
   chimiotaxie, en choisissant des conditions initiales et une fonction
   f(t,x) appropriées.

3. Produire le code de résolution du problème et le tester.

4. Comment faudrait-il modifier le code pour passer en dimension 2 ou 3
   ?

## refs

À compléter dans le répertoire [./refs](./refs).
