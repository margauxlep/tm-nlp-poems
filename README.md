# Poèmes humains et poèmes générés par ChatGPT : une analyse comparative

## Problématique
Aujourd'hui, les LLM (large language models) sont capable de générer des textes d'une qualité impressionnante. En effet, les performances de ces modèles, dont le grand public a pris connaissance avec le célèbre ChatGPT, sont capables - selon certaines sources [ref] de passer le test de Turing; donc de produire un texte indifférentiable de celui d'un humain.

Toutefois, ces textes générés artificiellement par des LLM, manifestent-ils tout de même encore des différences statistiques avec des textes dits "naturels" ?

En effet, ces modèles étant "probabilistiques", ils sont capables de générer un texte crédible. Cela signifie-t-il pour autant qu'ils reproduisent le langage humain dans toute sa diversité?

Nous faisons l'hypothèse qu'au contraire, ces textes ne sont capable de ne reproduire, dans la plus grande partie, que les expressions "moyennes" et "génériques" que nous utilisons, résultant dans un perte de diversité, par rapport à ce que l'on retrouve dans le langage naturel.

## Objectif de la recherche 

Dès lors, l’objectif de notre recherche est d’une part d’observer si les poèmes générés par ChatGPT 3.5 font montre d’une diversité lexicale et thématique inférieure à des poèmes humains, et d’autre part, d’analyser qualitativement ces poèmes dans le but d’explorer les mécanismes de « création » de ChatGPT. Pour ce faire, nous souhaitons comparer des poèmes générés par le modèle de langage avec des poèmes humains issus de la littérature canonique et tester les limites de ChatGPT 3.5, en comparant également les performances du modèle pour différents types de prompting.

## Dataset

Notre dataset est constitué de 200 poèmes, divisés en quatre groupes de 50. Un groupe de poèmes humains, et trois groupes de poèmes générés par ChatGPT. En premier lieu, nous avons sélectionné 50 poèmes de la littérature “canonique”. Les poèmes ont été écrits par les auteurs suivants : André Breton, Arthur Rimbaud, Alphonse de Lamartine, Alfred de Vigny, Charles Baudelaire, Guillaume Apollinaire, Gérard de Nerval, Jean Racine, Pierre Corneille, Pierre de Ronsard, Paul Verlaine, Stéphane Mallarmé, Tristan Tzara, Victor Hugo. Puis, nous avons généré des poèmes avec ChatGPT 3.5 . Nous avons testé trois différents niveaux de prompting.

Pour le premier niveau de prompting, nous avons donné des indications minimales. Pour chaque poème de notre dataset de “poèmes humains”, nous avons généré un poème en indiquant le type de poème (sonnet, poème en écriture automatique, etc.) et le style de l’auteur.

Ex : Écris un sonnet dans le style d’Arthur Rimbaud

Pour le deuxième niveau de prompting, nous avons donné un exemple à imiter. Nous avons pris chaque poème de notre dataset de “poèmes humains” et demandé à ChatGPT de générer un poème ressemblant à celui-ci.

Ex : Écris un poème qui ressemble à celui-ci : 
Napoléon mourant vit une Tête armée… 
Il pensait à son fils déjà faible et souffrant : 
La Tête, c’était donc sa France bien-aimée, 
Décapitée aux pieds du César expirant.
Dieu, qui jugeait cet homme et cette renommée, 
Appela Jésus-Christ ; mais l’abîme s’ouvrant, 
Ne rendit qu’un vain souffle, un spectre de fumée : 
Le Demi-Dieu, vaincu, se releva plus grand.
Alors on vit sortir du fond du purgatoire 
Un jeune homme inondé des pleurs de la Victoire, 
Qui tendit sa main pure au monarque des cieux ;
Frappés au flanc tous deux par un double mystère, 
L’un répandait son sang pour féconder la Terre, 
L’autre versait au ciel la semence des dieux !

Pour le troisième niveau de prompting, nous avons donné des indications pour “reproduire” le poème. Nous avons indiqué le début du poème, la forme, les thèmes, les champs lexicaux, et le style général.

Ex: Voici des instructions pour écrire un poème :
-	Commence par « Esprit parisien ! démon du Bas-Empire ! Vieux sophiste épuisé qui boit, toutes les nuits, »
-	Respecte la forme sonnet (deux quatrains et deux tersets)
-	Écris un poème qui parle de l’Esprit parisien en le personnifiant. Prends un ton cynique et ironique pour faire une critique sociale
-	Met en lumière l’hypocrisie, la cruauté et la superficialité de l’Esprit parisien 

## Méthode
Pour réaliser notre expérience, nous avons décidé de réaliser une analyse comparative de poèmes; le but étant de repérer d'éventuelles différences statistiquement significatives entre des poèmes humains et des poèmes générés artificiellement. Voici les étapes que nous avons suivies : 

### Preprocessing
Pour mener à bien notre analyse, nous avons suivi un processus de prétraitement des données afin de garantir leur cohérence et leur comparabilité. Voici les étapes que nous avons suivies :
-	Importation des poèmes dans une DataFrame pandas : nous avons rassemblé un ensemble de 200 poèmes humains et leurs équivalents générés par ChatGPT, selon les trois niveaux de prompting mentionnés précédemment. Pour faciliter la correspondance ultérieure, nous avons conservé le nom de chaque fichier associé à son contenu.
-	Séquençage du texte : nous avons commencé par éliminer les marqueurs de saut de ligne (‘\n’) pour assurer une représentation continue du texte. Ensuite, nous avons utilisé la bibliothèque NLTK pour effectuer la tokenisation des poèmes, tout en supprimant les mots vides (stopwords) en utilisant la liste des stopwords français fournie par NLTK. La liste des stopwords français de NLTK contient les articles (« le », « les », « un », « mon », « ma », etc.), les prépositions et conjonctions (« et », « de », « dans », « ou », « y » etc.) les pronoms, et toutes les formes verbales des verbes « être » et « avoir ».

### Variabilité lexicale : fréquence des mots
L’analyse de la variabilité lexicale a été réalisée en utilisant la librairie LexicalRichness  Les étapes que nous avons suivies sont les suivantes :
-	Calcul des métriques lexicales : nous avons calculé plusieurs métriques, notamment le nombre total de mots, le nombre de mots uniques (termes), et le ratio mots/termes, en utilisant à la fois notre propre tokenisation et celle proposée par LexicalRichness.
-	Distribution des mots : nous avons examiné la distribution des mots en fonction de leur fréquence pour chaque niveau de prompt (humain et ChatGPT).
-	Mots les plus fréquents : Nous avons extrait les mots les plus fréquents pour chaque niveau de prompt, ce qui nous a permis d’obtenir un aperçu des termes prédominants dans chaque groupe.
-	Indices de richesse lexicale : nous avons calculé plusieurs indices de richesse lexicale, notamment le “Measure of Textual Lexical Diversity” (MTLD), la mesure “Hypergeometric distribution diversity” (HD-D), ainsi que la mesure de diversité lexicale de Maas.
-	Analyse de ces indices en mesurant la déviation par rapport au groupe de contrôle (poèmes humains). En effet, chaque poème humain de notre dataset ayant servi de base pour un et un seul poème pour chacun des trois niveaux de prompting, les poèmes sont donc « regroupables » (matching) ; à chaque poème humain, correspond un poème de niveau 1, un poème de niveau 2 et un poème de niveau 3. Dès lors, nous avons calculé, pour chaque indice de richesse lexicale mentionné plus haut, la différence entre chaque poème généré par ChatGPT et son correspondant dans le groupe de contrôle (poème humain).


### Variabilité thématique : Topic Modelling
Pour analyser la variabilité thématique des poèmes, nous avons adopté une approche de “Topic Modelling” en utilisant le modèle Latent Dirichlet Allocation (LDA). Voici les étapes que nous avons suivies :
-	Préparation des données pour le LDA : nous avons regroupé l’ensemble des poèmes de chaque groupe (humain et ChatGPT) en un seul texte afin de former un corpus distinct pour chaque groupe.
-	Application du modèle LDA : nous avons utilisé la bibliothèque Gensim pour exécuter le modèle LDA. Pour simplifier notre analyse, nous avons fixé le nombre de thèmes (topics) à retourner à 10. Nous avons comparé les thèmes obtenus dans l’espoir d’identifier la diversité ou la redondance des thèmes, ce qui pourrait servir d’indicateur de la diversité thématique des poèmes.



