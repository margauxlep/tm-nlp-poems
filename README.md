# tm-nlp-poems

Poèmes humains et poèmes générés par ChatGPT : une analyse comparative
Introduction
Problématique
Aujourd'hui, les LLM (large language models) sont capable de générer des textes d'une qualité impressionnante. En effet, les performances de ces modèles, dont le grand public a pris connaissance avec le célèbre ChatGPT, sont capables - selon certaines sources [ref] de passer le test de Turing; donc de produire un texte indifférentiable de celui d'un humain.

Toutefois, ces textes générés artificiellement par des LLM, manifestent-ils tout de même encore des différences statistiques avec des textes dits "naturels" ?

En effet, ces modèles étant "probabilistiques", ils sont capables de générer un texte crédible. Cela signifie-t-il pour autant qu'ils reproduisent le langage humain dans toute sa diversité?

Nous faisons l'hypothèse qu'au contraire, ces textes ne sont capable de ne reproduire, dans la plus grande partie, que les expressions "moyennes" et "génériques" que nous utilisons, résultant dans un perte de diversité, par rapport à ce que l'on retrouve dans le langage naturel.

Méthode
Pour réaliser notre expérience, nous avons décidé de réaliser une analyse comparative de poèmes; le but étant de repérer d'éventuellement différences statistiquement significatives entre des poèmes humains et des poèmes générés artificiellement. Pour ce faire, nous souhaitons comparer la variabilité du vocabulaire, la fréquence de "bi-grams", (ajouter des choses)

Dataset
Nous avons réalisé manuellement une base de donnée de 100 poèmes, dont 50 ont été écrits par des humains et 50 ont été générés par une machines. les 50 poèmes écrits par des humains sont issus de la littérature dite "canonique", et une grande majorité (dire précisément combien) sont de la forme sonnet. Nous avons choisi 14 auteurs différents :

André Breton
Arthur Rimbaud
Alphonse de Lamartine
Alfred de Vigny
Charles Baudelaire
Guillaume Apollinaire
Gérard de Nerval
Jean Racine
Pierre Corneille
Pierre de Ronsard
Paul Verlaine
Stéphane Mallarmé
Tristan Tzara
Victor Hugo
Pour ce qui est des 50 poèmes "artificiels", nous les avons généré avec ChatGPT, interface basée sur le modèle GPT-3 d'Open AI. Pour que notre analyse comparative soit pertinente, nous avons, pour chaque poème humain, demandé à ChatGPT d'écrire un poème "dans le style de" l'auteur, et de la même forme. (Notons que la forme n'a pas toujours été respectée par ChatGPT).

Exemple de prompt : "écris un sonnet dans le style de Guillaume Apollinaire"
Pour augmenter la variabilité du dataset, nous avons quelques fois précisé un thème.

Exemple de prompt : "écris un sonnet sur un meuble dans le style de Charles Baudelaire"
