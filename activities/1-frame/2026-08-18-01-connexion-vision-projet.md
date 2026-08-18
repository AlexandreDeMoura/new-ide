# Connexion vision-projet

- **Étape :** 1. Frame
- **Date :** 2026-08-18
- **Question de départ :** Le sujet du projet est formulé au niveau Vision (« un monde où l'IA écrit 100% du code »). Quels sont les barreaux manquants — Mission, Stratégie, Objectif — qui relient cette vision à une action à mener ? Et quels objectifs secondaires cette descente permet-elle d'écarter ?
- **Participants / sources :** Alexandre (solo). Méthodologie : `methodology/1. FOCUSED - Frame.md`, activité « Connexion vision-projet » (d'après Jeff Weiner, *From Vision to Values*).

## Déroulé

Descente de la chaîne à 5 niveaux (Vision → Mission → Stratégie → Objectif → Projet) en posant à chaque palier la question « comment ? ». Contexte : projet personnel d'exploration, sans entreprise préexistante — les niveaux Mission et Stratégie sont donc à écrire, pas à retrouver.

À chaque niveau, un éventail de branches a été produit sans hiérarchie, puis soumis à réaction. Le sens de parcours descendant a été retenu contre le parcours remontant, la formulation initiale du sujet étant déjà haute dans la chaîne.

Séparation opérée d'emblée : la phrase de départ contenait deux affirmations de nature différente — une Vision (« l'IA écrit 100% du code ») et une hypothèse de solution déjà formée (« l'arborescence de fichiers et le code source ne sont plus les bonnes informations à montrer »). La seconde a été retirée du niveau Vision pour ne pas verrouiller la réponse avant la question.

## Matière brute

### Niveau 1 — Vision : branches explorées

Six mondes compatibles avec « l'IA écrit 100% du code », mais menant à des projets différents :

- **A. Le code devient un artefact de compilation.** Personne ne lit le code, comme personne ne lit l'assembleur. La source de vérité remonte vers l'intention.
- **B. Le goulot d'étranglement se déplace vers la vérification.** Produire est gratuit donc sans valeur ; le coût dominant devient de savoir si ce qui a été produit est juste.
- **C. Le développeur devient celui qui dit non.** Il ne produit plus, il contraint. Une journée de travail est une suite de décisions, pas de fichiers modifiés.
- **D. Le logiciel devient jetable.** On ne maintient plus, on régénère. Plus de dette, plus d'archéologie.
- **E. La population des builders est multipliée.** La barrière technique tombe ; l'utilisateur n'est plus un développeur.
- **F. Le logiciel se dé-partage.** Chacun génère son outil pour lui-même ; plus de codebase commune.

**Retenu : C, adossé à B.** Reformulation issue de l'échange :

> Quand produire du code devient gratuit, le métier de builder devient un métier de jugement. Mais on ne peut pas juger ce qu'on ne comprend pas — la compréhension de ce qui existe déjà devient donc le prérequis rare, et le vrai coût.

**Écarté :** D (si l'on régénérait tout, comprendre l'existant n'aurait aucune valeur — or le projet suppose qu'on vit avec ce qui a été généré) ; F (même raison). **Retenu à moitié :** A — on ne montre pas le code, mais il reste la source de vérité, c'est lui l'arbitre du malentendu.

**Reformulation de E, non anticipée :** la population visée n'est pas « quelqu'un qui n'a jamais codé », mais **quelqu'un qui code sans lire de code et qui s'est déjà brûlé** — le vibecodeur expérimenté ayant subi du legacy généré sur Cursor, Claude Code ou Lovable. Population qui n'a pas besoin d'être convaincue que le problème existe.

### Niveau 2 — Mission : branches explorées

- **M1. Rendre lisible le comportement sans passer par le code.** Montrer ce que l'app fait, jamais comment elle est faite.
- **M2. Être le détecteur de malentendus.** L'outil montre les écarts entre croyance et réalité ; son unité de valeur est la surprise.
- **M3. Faire de la règle métier la source de vérité.** L'outil extrait les règles ; c'est elles qu'on manipule.
- **M4. Rendre reprenable un projet qu'on n'a pas écrit.** Récupération de contrôle sur une codebase générée.
- **M5. Fournir la matière de la décision.** Répondre à « si je change ça, qu'est-ce qui casse ».
- **M6. Être le miroir qui apprend.** L'utilisateur construit un modèle mental juste à force d'usage.

**Retenu : M1, M3 et M6.**

**Écarté — et c'est le premier principe produit du projet :**

> **Le détecteur de malentendu, c'est l'humain, pas l'IA.** L'humain doit disposer des outils qui le mettent en état de détecter ; un outil qui signale lui-même l'écart vole à l'humain le travail qu'on veut lui garder.

M2 tombe donc par principe, pas par arbitrage de périmètre.

**M4 :** écarté du MVP, pas du projet.

**Objection levée sur M3 :** M1 et M6 sont en lecture seule, M3 tel que formulé impliquait un système bidirectionnel d'un tout autre ordre de grandeur. Tranché : **la vue est en lecture seule dans tous les cas.** L'écriture du code passe toujours par un chat branché sur Codex et/ou Claude Code. Nuée remplace l'arborescence de fichiers et la vue centrale du code d'un fichier sélectionné — il ne les édite pas.

**Objection levée sur M6** (un outil dont le succès se mesure à sa propre désuétude) : le logiciel étant continuellement modifié par de nouvelles features, des refactos, des refontes et des migrations, l'enjeu pédagogique n'a pas de fin. L'objectif n'a jamais été de fabriquer un développeur professionnel ni de le renvoyer vers un IDE classique.

### Niveau 3 — Stratégie : branches explorées

- **S1. La spec inversée.** Reconstruire depuis le code une spécification lisible — règles métier, conditions, comportements — tenue à jour.
- **S2. La cartographie comportementale.** Représenter l'app comme un graphe de parcours, états et transitions.
- **S3. L'interrogation.** Aucune représentation figée ; l'outil répond à des questions.
- **S4. L'exécution instrumentée.** Les règles s'allument en direct pendant l'usage de l'app.
- **S5. Le diff d'intention.** L'utilisateur écrit d'abord ce qu'il croit, l'outil confronte ensuite.
- **S6. Le tour guidé.** L'outil hiérarchise et raconte, du plus important au plus périphérique.

**Retenu : S1.** **Reporté au futur lointain, comme fonctionnalités avancées :** S2 et S5. **Non retenus :** S3, S4, S6.

### Niveau 5 — Projet : l'action à mener

**Nuée** (nom retenu au cours de l'activité). Un environnement de vibe coding où l'utilisateur démarre un nouveau projet — au lieu de le démarrer sur Cursor ou Lovable. Nuée est connecté à des instances Codex et/ou Claude Code. Quand l'IA modifie le code source, elle modifie aussi les vues de Nuée : l'utilisateur visualise la logique de son application et peut la reviewer, là où auparavant il avançait à l'aveugle en acceptant le code puis en vérifiant a posteriori par QA manuelle. La QA manuelle reste possible, elle n'est plus le seul filet.

**Second principe dur, tranché pendant l'activité :**

> **La vue est dérivée du code.** Le code reste seul arbitre ; la vue est recalculée. Elle ne peut donc pas mentir. Contrepartie assumée : elle ne peut pas porter d'intention que le code ne porte pas.

L'alternative écartée était que l'agent maintienne code et vue en parallèle — auquel cas la vue peut diverger du code, et l'outil censé éliminer les malentendus devient lui-même la source de malentendu la plus crédible, puisque c'est celle que l'utilisateur lit.

**Contenu de la vue :** règles métier, pages, endpoints — la liste des informations que Nuée montre en remplacement du code n'est pas arrêtée.

### Le moment d'usage, et la tension qu'il crée

L'usage se place au **démarrage d'un projet neuf**, pas sur une codebase existante. Nuée n'est donc pas un remède mais un vaccin.

Conséquence relevée : **la courbe de valeur est inversée.** Au jour 1, il n'y a rien à comprendre — la spec inversée d'une app vide est vide. L'adoption est demandée au moment où l'utilisateur est le plus satisfait de son outil actuel, contre une valeur qui n'arrive qu'après plusieurs semaines, quand la confusion s'installe. La douleur qui définit la population est passée ; le produit s'utilise au présent pour un bénéfice futur.

Trois sorties possibles avaient été posées : assumer et faire porter la promesse sur la peur ; trouver une valeur au jour 1 étrangère à la compréhension ; rouvrir M4 pour entrer sur un projet existant où la douleur est immédiate.

**Position prise :** la deuxième, en assumant explicitement la première partie du coût — « j'accepte que ça en rebute certains et que Nuée soit impacté dans sa rétention chez les users les moins patients ».

**La valeur du jour 1 est esthétique, pas cognitive.** Une direction artistique visant l'organique — comme si l'on créait un être vivant — et des animations rendant la génération de code « wow » : l'utilisateur voit naître les premiers blocs de son application dans une vue moderne et futuriste. L'intérêt des premiers jours n'est pas dans la richesse de la vue (peu de règles, peu de pages, peu d'endpoints) mais dans une *delightful experience* à chaque prompt envoyé à Codex ou Claude Code.

**Risque noté, non tranché :** rendre la génération de code spectaculaire cultive l'émerveillement passif que Nuée existe précisément pour remplacer. Regarder une app naître comme un organisme et reviewer une règle métier sont deux états d'esprit opposés.

### Niveau 4 — Objectif : branches explorées

- **O1. Prouver que la spec inversée est lisible.** Comprendre son app sans jamais ouvrir un fichier.
- **O2. Prouver que la review de logique attrape ce que la QA manuelle rate.** Repérer un écart avant de tester à la main.
- **O3. Prouver que la vue tient dans le temps.** Après N itérations d'agent, la spec est toujours juste et lisible.
- **O4. Prouver qu'on peut arracher quelqu'un à Cursor.** Bascule d'outil au démarrage.
- **O5. Prouver que comprendre fait mieux prompter.** L'agent produit moins de bêtises parce qu'on le pilote depuis une vue juste ; le gain se mesure sur la sortie de l'IA, pas sur l'état mental de l'humain.
- **O6. Prouver que ça tient à l'échelle.** La spec reste navigable quand l'app grossit — là où l'arborescence de fichiers décroche.
- **O7. Prouver que l'utilisateur revient.** Nuée devient l'écran par défaut, pas la vue de secours.

**Retenus pour le MVP : O1, O2, O3, O5, O6.** **Priorité la plus haute : O1 et O5.** **Écartés : O4 et O7.**

Nature de mesure relevée par groupe : O1, O2 et O5 sont qualitatifs et observables sur quelques utilisateurs, donc compatibles avec une discovery courte ; O3 et O6 sont des risques techniques testables sans utilisateur ; O4 et O7 sont des métriques d'adoption demandant volume et temps — leur écartement est cohérent avec une timebox de discovery.

### La chaîne complète

> Mon projet **Nuée** contribue à améliorer **la justesse du modèle mental qu'un vibecodeur a de son application, et la qualité de ce qu'il obtient de son agent** (O1 + O5), dans le cadre d'une stratégie de **spec inversée dérivée du code** (S1), qui participe à ma mission de **rendre lisible le comportement d'une application sans passer par le code, en exposant les règles qui le régissent, pour rendre l'utilisateur de plus en plus conscient des enjeux techniques** (M1 + M3 en lecture + M6), afin de tendre vers cette vision : **quand produire du code devient gratuit, le métier de builder devient un métier de jugement — et la compréhension de l'existant devient le prérequis rare** (C adossé à B).

## Ce que j'en retiens pour le livrable

### Ce qui alimente le Success Criteria

- **Un arbitrage reste entier : O1 et O5 sont co-prioritaires, or le Success Criteria n'admet qu'un indicateur.** Ce sont deux métriques de natures opposées — O1 mesure un état de l'utilisateur (qualitatif, déclaratif, fragile), O5 mesure un comportement observable de sortie de l'agent. Le choix n'est pas cosmétique : il détermine si la discovery se joue en entretien ou en mesure.
- **Le « niveau actuel » de l'indicateur n'existe pas.** La méthode demande indicateur + ambition + situation. Le produit n'existant pas et n'ayant pas de base installée, l'activité « Observation des métriques dans la durée » est impraticable telle quelle. Une baseline devra être établie autrement — vraisemblablement en observant le workflow actuel, du vibe coding sans Nuée.
- **La métrique ne pourra pas être mesurée au jour de l'installation** (courbe de valeur inversée). Contrainte directe sur la Timebox : le délai avant première mesure est un paramètre du projet, pas un détail d'exécution.

### Ce qui alimente le Damage Control

- **La DA « organique » contre la vigilance.** Candidat le plus sérieux : contrôler que l'expérience spectaculaire ne dégrade pas l'attention portée à la review.
- **La lisibilité de la vue à mesure que l'app grossit** (O6) : la vue dérivée peut devenir aussi illisible que ce qu'elle remplace.
- **La latence entre la modification du code par l'agent et la mise à jour de la vue** : une vue en retard est une vue qui ment, ce que le principe « dérivée du code » était censé interdire.

### Ce qui est mis de côté

- **Vision :** D (logiciel jetable), F (logiciel dé-partagé) — définitivement, ils contredisent la prémisse du projet.
- **Mission :** M2 (l'outil détecte les malentendus) — écarté par principe. M4 (reprendre un projet existant) — écarté du MVP seulement ; c'est ce choix qui crée la courbe de valeur inversée, il est donc le premier candidat à la réouverture si l'entrée par le projet neuf ne tient pas.
- **Stratégie :** S3, S4, S6 non retenus ; S2 et S5 reportés comme fonctionnalités avancées.
- **Objectif :** O4 et O7, incompatibles avec une timebox de discovery.

### Ce qui n'a pas été abordé

- **La Timebox.** Aucun élément produit par cette activité. À traiter à part.
- **Le contenu exact de la vue** (quelles informations remplacent le code) reste ouvert — c'est un sujet d'étape Observe et Unfold, pas de Frame.
