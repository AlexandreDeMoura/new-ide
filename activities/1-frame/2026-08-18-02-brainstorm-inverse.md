# Brainstorm inversé

- **Étape :** 1. Frame
- **Date :** 2026-08-18
- **Question de départ :** À quoi ressemblerait Nuée dans un monde sans contraintes — et, retour sur terre, qu'est-ce qui pourrait empêcher ce projet de réussir ? Quelles pistes de Success Criteria ces empêchements éliminent-ils ?
- **Participants / sources :** Alexandre (solo). Méthodologie : `methodology/1. FOCUSED - Frame.md`, activité « Brainstorm inversé ». S'appuie sur `2026-08-18-01-connexion-vision-projet.md`.

## Déroulé

Activité menée en deux temps séparés, sans les mélanger.

**Temps 1 — l'utopie.** Un éventail de mondes idéaux produit sans hiérarchie, sur cinq axes (la vue, le rapport à l'agent, le rapport au temps, le collectif, la mesure). Tri en trois catégories : ce qui est un **cap** (le projet cherche à s'en approcher), ce qui est **refusé même sans contraintes** (donc un principe, pas un arbitrage de périmètre), et le reste.

**Temps 2 — le retour sur terre.** Liste des empêchements possibles sur cinq axes (mesurer, produire, faire adopter, mener le projet, tenir la prémisse), puis tri : bloquant / assumé / non-problème. C'est ce tri qui alimente le Success Criteria par élimination, et le Damage Control par ce qui reste sous surveillance.

## Matière brute

### Temps 1 — L'utopie : branches explorées

**Axe : la vue elle-même**

- **U1. La vue est parfaite et instantanée.** À chaque token écrit par l'agent, la spec inversée est à jour, exacte, exhaustive. Zéro latence, zéro règle manquée, zéro bruit.
- **U2. La vue ne grossit jamais.** Une app de 300 000 lignes se lit avec le même effort qu'une app de 300.
- **U3. La vue est un langage, pas un écran.** Ce qu'on lit, on peut le modifier, et le code suit.
- **U4. La vue porte l'intention, pas seulement le comportement.** Elle sait *pourquoi* la règle existe.

**Axe : le rapport à l'agent**

- **U5. L'utilisateur ne se trompe plus jamais de prompt.** Il pilote son agent avec les mots de son domaine métier, sans réinterprétation.
- **U6. L'agent ne peut rien produire que l'utilisateur n'ait pas regardé.** Le code non revu n'existe pas.
- **U7. La carte de couverture du regard.** Chaque règle porte un état : vue et validée / générée, jamais regardée.

**Axe : le rapport au temps**

- **U8. L'histoire de la logique est navigable.** Quelle règle est apparue quand, à la suite de quel prompt. Un historique de comportements, pas de diffs.
- **U9. Il n'y a pas de jour 1.** La valeur est pleine dès la première minute ; la courbe de valeur inversée disparaît.
- **U10. Le legacy n'existe plus.** N'importe quelle codebase existante devient lisible instantanément.

**Axe : le collectif**

- **U11. La vue est un standard.** Tous les projets se lisent dans le même format ; on prend en main l'app d'un inconnu en cinq minutes.
- **U12. L'app se joue dans la vue.** On l'utilise et les règles s'allument en direct.

**Axe : la mesure**

- **U13. Le capteur de modèle mental.** On connaît à tout instant l'écart entre ce que l'utilisateur croit que son app fait et ce qu'elle fait.
- **U14. Le compteur de bêtises de l'agent.** On sait, prompt par prompt, si la sortie était juste.
- **U15. Le contrefactuel.** Le même utilisateur vit le même projet avec et sans Nuée.

**Caps retenus : U1, U4, U5, U8, U11, U12.**

**Refusés même dans un monde sans contraintes : U3 et U6.** Ce refus est le résultat le plus structurant du temps 1 — il transforme deux points en principes :

> **La lecture seule n'est pas un renoncement de MVP, c'est un choix.** Même si l'édition depuis la vue était gratuite, elle n'est pas voulue.

> **Nuée ne rend jamais la review obligatoire et ne bloque rien.** Le regard humain reste facultatif, y compris dans l'utopie.

**Mesure idéale retenue : U13.** Objection levée pendant l'échange : U13 semblait rouvrir M2 (l'outil détecte le malentendu à la place de l'humain), écarté par principe en activité 01. Levée — mesurer l'écart *en tant qu'observateur de la discovery* n'est pas *afficher* l'écart à l'utilisateur. Le principe tient.

**Tension notée, non tranchée :** U4 retenu comme cap contredit le principe « la vue est dérivée du code » (activité 01) — une vue qui porte l'intention doit tenir cette intention quelque part, et le code ne la porte pas.

**Cap lointain ajouté, hors MVP :** certaines couches de décision technique sont aujourd'hui déléguées à l'IA (choix d'architecture, introduction d'une lib de server state…) et il n'est pas question de demander à un vibecodeur de les trancher. Mais Nuée devrait faire remonter progressivement son plafond technique, jusqu'à ce que certaines de ces couches repassent dans ses cordes. Explicitement hors priorité MVP.

### Temps 2 — Les empêchements, et leur tri

**Ce qui empêcherait de mesurer**

- **E1. Aucune baseline n'existe.** → *Non-problème.* « Un avis positif très subjectif est suffisant. Les gens n'ont pas switché de VS Code à Cursor avec des success metrics en béton. »
- **E2. L'écart de modèle mental n'est observable qu'avec un protocole lourd** (faire décrire l'app, confronter au code, coder l'écart). → *Non-problème, pour la même raison* : c'est précisément pourquoi l'avis subjectif positif fait office de critère à ce stade.
- **E3. La première mesure arrive plusieurs semaines après l'installation** (courbe de valeur inversée). → *Non-problème.*
- **E4. Le déclaratif ment** (biais d'engagement de celui qui a investi son attention). → *Assumé.* « Tant que de nouveaux utilisateurs sont contents et deviennent des ambassadeurs, je me fiche qu'une partie de leur motivation vienne du temps investi. »
- **E5. Effet Nuée contre effet projet** : à J+30 l'utilisateur comprend mieux son app parce qu'il l'a construite. → *Non-problème.*
- **E6. Le volume** : à 5 utilisateurs, aucun pourcentage n'a de sens. → *Non-problème.* « Je n'ai pas besoin d'un échantillon statistiquement significatif pour commencer à itérer. »
- **E7. O5 n'est pas plus mesurable que O1** (« moins de bêtises » suppose un référentiel de bêtises). → *Non-problème.*

**Ce qui empêcherait le produit d'exister**

- **E8. La spec inversée est un problème non résolu** : extraire des règles justes *et* exhaustives en continu ; faux positifs et règles manquées sont l'état de l'art. → *Problème réel, mais assumé.* Argument retenu : sur Cursor ou Lovable, le vibecodeur fait déjà pleinement confiance à l'IA. Avec Nuée il y a **une couche de vérification IA en plus** (l'IA doit produire les informations qui peuplent les vues) et **une couche de vérification humaine en plus** (pas seulement la QA manuelle, mais la lecture des vues). La montée en puissance des modèles est le pari sous-jacent.
- **E9. Le coût** : re-dériver la vue à chaque modification, c'est de l'analyse LLM permanente. → *Assumé, et mis sous surveillance.* Niveau posé : **+20 % de coût en tokens au maximum.**
- **E10. La latence — une vue en retard est une vue qui ment.** → *Résolu par conception.* L'état de fraîcheur de la vue est connaissable à tout moment via les changements trackés par Git. Troisième principe dur : **la vue est à jour, ou elle dit qu'elle ne l'est pas.** Elle ne ment jamais par omission.
- **E11. Le ticket d'entrée est un IDE complet** (éditeur, terminal, git, preview, déploiement) pour remplacer Cursor au démarrage d'un projet. → **Gros problème, non résolu, reporté.**
- **E12. Dépendance amont à Codex / Claude Code**, qui peuvent intégrer eux-mêmes une vue logique. → *Non-problème.* Nuée est open source ; les vibecodeurs préfèrent leur abonnement mensuel à des appels d'API facturés. Et si un acteur intègre la vue : « ce projet mourra d'une belle mort, celle d'avoir fait avancer l'open source. »

**Ce qui empêcherait l'adoption**

- **E13. La bascule est demandée au moment de plus grande satisfaction** avec l'outil actuel. → *Assumé.* Ceux qui déclarent que tout va bien avec Cursor alors qu'ils ont déjà souffert sur des apps plus avancées sont probablement séduisibles par un gros effort de direction artistique. Sinon, on accepte de ne pas les convaincre pendant le MVP.
- **E14. Le vibecodeur brûlé n'a pas forcément conclu « il me faut comprendre ».** → *Assumé, voir E13.*
- **E15. La génération suivante de modèles rend la compréhension moins urgente.** → *Assumé.* Certaines informations de Nuée perdront en pertinence dans une ou deux générations, mais l'amélioration des modèles et la baisse des coûts sont aussi des opportunités pour Nuée. Et des modèles qui s'améliorent menacent bien plus les IDE que Nuée.
- **E16. Cursor / Lovable / Replit ajoutent une vue logique en quelques mois.** → *Non-problème.* « Tant mieux pour eux. La mission de Nuée est de faire évoluer le domaine de recherche sur les produits IA. »
- **E17. La DA organique cultive l'émerveillement passif** que Nuée veut remplacer. → *Assumé, et posé comme obligatoire.* « La DA organique est nécessaire pour se faire une place dans un marché concurrentiel. »
- **E18. L'utilisateur regarde la vue sans reviewer** — juger coûte, le vibe coding existe pour ne pas payer ce coût. → *Reformulé.* Juger coûte trop cher à un non-tech, mais cela ne veut pas dire qu'il refuse d'y passer du temps : dans un IDE, le temps qu'il y aurait passé n'aurait de toute façon eu aucun effet. Le refus observé est un refus d'effort inutile, pas un refus d'effort.
- **E19. Le vibecodeur ne veut pas monter en compétence technique.** → *Assumé.* « Dans ce cas Nuée ne plaira pas à ce profil. »

**Ce qui empêcherait le projet lui-même**

- **E20. Solo : mener la discovery et construire un IDE complet.** → *Problème réel.* Stratégie : récupérer le maximum d'existant — connexion à Codex et Claude Code pour les modèles et l'écriture du code, et quelque chose d'existant pour Git.
- **E21. Recruter des vibecodeurs brûlés** prêts à démarrer un vrai projet dans un outil inconnu et à y rester plusieurs semaines. → *Challenge non négligeable, assumé.* Pari : beaucoup de vibecodeurs sont curieux de découvrir en premier la prochaine innovation du secteur.
- **E22. Aucune Timebox posée.** → *Tranché pendant l'activité :* **la première itération de FOCUSED se fait en une semaine.**
- **E23. La tentation de construire l'outil plutôt que de tester l'hypothèse.** → *Non-problème.*

**Ce qui empêcherait la prémisse d'être vraie**

- **E24. Comprendre n'est peut-être pas le prérequis du jugement** — tester suffirait. → *Écarté par l'observation.* Beaucoup de vibecodeurs ont demandé à leur IA d'écrire massivement des tests pour régler ce problème. Ça ne suffit pas : **les tests sont eux-mêmes sensibles au malentendu** entre ce que l'utilisateur croit que le code fait et ce qu'il fait. Un test généré sur une compréhension fausse valide la compréhension fausse.
- **E25. La règle métier n'est peut-être pas le bon grain** — trop fine pour juger, trop grosse pour agir. → *Ouvert.* À explorer dans les étapes suivantes de FOCUSED.

## Ce que j'en retiens pour le livrable

### Ce qui alimente le Success Criteria

Le tri de E1 à E7 est net : **toutes les objections de mesurabilité sont écartées d'un bloc**, au motif qu'un avis positif subjectif suffit à ce stade. Cela élimine d'un coup les Success Criteria exigeant un protocole, une baseline, un contrefactuel ou un échantillon — donc les formulations quantitatives de O1 et de O5.

Deux points restent à trancher dans le livrable :

- **La piste retenue ne correspond à aucun des objectifs priorisés en activité 01.** « Des utilisateurs contents qui deviennent ambassadeurs » n'est ni O1 (justesse du modèle mental) ni O5 (qualité de la sortie de l'agent) : c'est une métrique de satisfaction et de recommandation, proche de O7, écarté en activité 01 comme métrique d'adoption. Soit O1/O5 reviennent comme indicateur mesuré de façon déclarative, soit le Success Criteria assume ce déplacement — mais les deux ne tiennent pas ensemble.
- **L'ampleur du changement attendu n'est pas posée.** C'est l'erreur courante que la méthode signale explicitement à l'étape Frame : un critère sans ordre de grandeur ne permet de trancher aucune décision ultérieure. « Un avis positif subjectif » n'est pas encore un critère — il manque le combien : combien d'utilisateurs, quelle proportion, quel signal tient lieu de « content » (déclaration, recommandation spontanée, retour à l'outil).

### Ce qui alimente le Damage Control

- **Le coût en tokens : +20 % maximum** (E9). C'est le seul candidat déjà chiffré, et le seul dont le niveau ait été posé pendant l'activité.
- **La DA organique contre la vigilance** (E17) : assumée comme obligatoire, ce qui en fait un candidat de surveillance plutôt qu'un arbitrage.
- **La fraîcheur de la vue** (E10) sort du Damage Control : elle est traitée par conception, pas par surveillance.

### Ce qui alimente la Timebox

- **Une semaine pour la première itération de FOCUSED** (E22).
- **Incohérence à trancher dans le livrable :** cette timebox est celle du cycle de discovery, pas celle de la mesure. E3 a été écarté comme non-problème, mais il reste vrai que la valeur de Nuée n'apparaît qu'après plusieurs semaines d'usage. Le livrable doit dire lequel des deux horizons il engage — sinon le Success Criteria est inatteignable à l'intérieur de sa propre Timebox.

### Ce qui est mis de côté

- **U3 et U6** : refusés définitivement, ils deviennent des principes produit.
- **U2, U7, U9, U10, U13, U14, U15** : non retenus comme caps. U13 survit uniquement comme mesure idéale de référence, jamais comme fonctionnalité.
- **E11 (le ticket d'entrée est un IDE complet)** : reconnu comme gros problème, explicitement reporté à plus tard. C'est le seul empêchement classé « problème réel » sans stratégie de réponse.
- **E25 (le grain de la règle métier)** : renvoyé aux étapes Observe et Unfold.
- **La montée en compétence technique de l'utilisateur** : cap lointain, hors MVP.

### Tension ouverte

- **U4 (la vue porte l'intention) contre « la vue est dérivée du code »** (activité 01). Non tranchée, à ne pas laisser s'installer implicitement.
