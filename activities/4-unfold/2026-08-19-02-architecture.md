# Architecture

- **Étape :** 4. Unfold
- **Date :** 2026-08-19
- **Question de départ :** Quelles pages produit sont sollicitées, modifiées ou créées pour que le First Use Case se déroule ? Où l'utilisateur se trouve-t-il, écran par écran, entre le moment où il prompte et le moment où il ship ?
- **Participants / sources :** Alexandre (solo). Méthodologie : `methodology/4. FOCUSED - Unfold.md`, activité « Architecture ». S'appuie sur les trois livrables figés et sur `activities/4-unfold/2026-08-19-01-avant-apres.md`, dont les références (A*, P*) sont reprises telles quelles.

## Déroulé

Activité menée en trois vagues successives, chacune ouverte par une production d'écrans candidats et fermée par un arbitrage de l'utilisateur.

Le garde-fou de la méthode a été posé en ouverture : l'erreur courante de UNFOLD est de basculer dans le mapping technique, et elle est explicitement signalée comme guettant l'activité Architecture. Tout ce qui relève de la CLI, des templates de prompts, de la file de dérivation ou du cache a donc été tenu hors du champ. On dessine des écrans, et on regarde lesquels manquent.

Une contrainte a orienté la production : Avant/Après avait déjà produit une **ligne de moments**. Pour que cette activité serve à quelque chose, elle devait produire autre chose — **un flow de pages**. Les écrans sont donc numérotés en `E*`, indépendamment des moments `A*` / `P*`.

Quatre interventions ont modifié le cours de l'activité et sont consignées à leur place. Les trois premières sont arrivées ensemble, à la clôture de la vague 1 ; la quatrième est un élagage massif qui a fermé la vague 2.

La vague 3 est un élagage, donc une convergence — menée par l'utilisateur. Elle est consignée telle quelle. Aucune hiérarchisation des écrans survivants n'a été faite : le tri en 5 Touchpoints appartient au livrable.

## Matière brute

### Le flow d'ancrage — version initiale

Reprise du squelette d'Avant/Après, mais avec la question « sur quel écran suis-je ? » posée à chaque cran :

```
F1  brancher l'agent          →  F2  prompter
F3  l'agent code              →  F4  la vue se recalcule
F5  lire la vue               →  F6  repérer (ou pas) l'écart
F7  reprompter / accepter     →  F8  QA manuelle  →  F9  ship
```

Deux cas d'usage secondaires ajoutés au départ, parce qu'ils sollicitent des écrans que le flow principal ne touche jamais : **le jour 1** (projet vide) et **la reprise après absence**. La passation à un tiers (P20) et le diagnostic de bug remonté par un utilisateur réel (P15) ont été laissés hors champ.

---

### VAGUE 1 — Les écrans candidats

#### Zone A — Entrée dans le produit (traversée une seule fois par projet)

- **E1.** Écran d'installation / première ouverture.
- **E2.** Écran de branchement du moteur : Codex ou Claude Code, clé API.
- **E3.** Écran d'état des quotas — combien il reste, partagé entre coder et voir (A56).
- **E4.** Écran de création de projet / sélection du dossier.
- **E5.** Écran « importer un projet existant » qui répond non (A17, M4 hors MVP).
- **E6.** L'état vide de la vue — l'écran du trou de valeur du jour 1 (A13).
- **E7.** Écran de première dérivation : la passe complète, sa durée, son coût (A58).
- **E8.** Écran « Nuée sans agent branché » — l'écran mort (A54).

#### Zone B — L'atelier (traversé des centaines de fois)

- **E9.** Le chat de l'agent : sollicité, pas créé — Nuée n'y touche pas (4ᵉ principe).
- **E10.** La vue **règles métier**.
- **E11.** La vue **pages**.
- **E12.** La vue **endpoints**.
- **E13.** Le sélecteur entre les trois vues.
- **E14.** L'indicateur de fraîcheur : à jour / en retard / aveugle (3ᵉ principe, A61).
- **E15.** L'état « dérivation en cours » — la vue bouge pendant qu'on la lit (P8).
- **E16.** Le détail d'une règle unique.
- **E17.** La navigation transversale règle → page → endpoint.
- **E18.** L'affichage de la conso Nuée, distincte de celle de l'agent (A59).
- **E19.** L'écran de choix du modèle de dérivation, moins cher que celui qui code (A62).
- **E20.** Le terminal / les logs — où l'utilisateur voit passer les appels.

#### Zone C — Le moment post-génération (le cœur du Launch Tweet)

- **E21.** L'écran « ce qui vient de changer » — un **diff de vue**, pas un diff de code.
- **E22.** L'écran des **effets de bord** : ce qui a changé sans qu'on l'ait demandé (P4).
- **E23.** L'écran « est-ce que ça respecte ton intention ? » — troisième promesse du tweet.
- **E24.** L'action « copier cette règle vers le prompt » (A44 / P3) — seul canal vue → agent.
- **E25.** L'action « demander à l'agent d'expliquer cette règle » (P5).
- **E26.** L'écran de désaccord : « ce n'est pas ce que je voulais » (A46).
- **E27.** Un marquage « vu / pas vu » sur les règles (P6).

#### Zone D — Hors boucle

- **E28.** L'écran de reprise : « voilà ce qui a changé depuis ta dernière visite » (A8, P12).
- **E29.** L'écran de recherche dans la vue (P15, diagnostic).
- **E30.** L'export de la vue — vers un PRD, un pitch, un autre outil (P27).
- **E31.** La vue montrable / partageable (A50, P10).
- **E32.** L'écran de confrontation vue ↔ PLAN.md (P13, A37).

#### Trous relevés à l'issue de la vague 1

- **Entre F4 et F5 :** rien ne dit à l'utilisateur *qu'il devrait regarder*. La vue est passive ; le tweet promet « immédiatement ».
- **En F6 :** repérer l'écart suppose une comparaison. Avec le code d'avant (E21) ou avec l'intention (E23) ? Deux écrans différents, et le tweet promet les deux.
- **Après F9 :** rien. L'effet de récence n'a toujours aucun candidat, comme dans Avant/Après.

Rappel de la méthode appliqué ici : les moments à fort impact ne sont pas les plus complexes. Candidats « zéro complexité, impact fort » repérés : **E14** (la vue avoue qu'elle est périmée) et **E27** (ce que tu n'as jamais regardé) — ils n'exigent aucune intelligence, seulement un état.

---

### Intervention 1 — La QA manuelle reste, et elle bifurque le flow

> La QA manuelle est **la première chose que l'utilisateur fait** une fois que l'agent a codé, par excitation de voir le produit évoluer en direct. On ne combat pas ça. Quand la tâche est surtout front-end, la QA passe avant Nuée. Quand elle est surtout back-end, Nuée passe avant.

Le flow d'ancrage est redessiné :

```
F1 brancher l'agent → F2 prompter → F3 l'agent code → F4 la vue se recalcule
                                   │
                 ┌─────────────────┴─────────────────┐
        tâche FRONT                          tâche BACK
        F5a QA manuelle (l'œil)              F5b lecture de la vue
        F6a lecture de la vue                F6b QA manuelle
                 └─────────────────┬─────────────────┘
                          F7 repérer l'écart
                    F8 reprompter / accepter → F9 ship
```

Ce que la bifurcation fait apparaître, et qu'aucune activité antérieure ne montrait :

- **Sur le front, Nuée passe en second et hérite d'une attention déjà dépensée.** L'utilisateur a vu son écran, il a eu sa récompense. La vue arrive sur un utilisateur satisfait.
- **Sur le back, Nuée est premier et sans concurrent.** Il n'y a rien à voir à l'œil nu. Seul endroit du flow où la vue est le seul regard possible.
- **La bifurcation recoupe presque exactement les trois vues :** la QA front recouvre la vue *pages*, jamais les vues *règles métier* et *endpoints*.

**Conséquence relevée, non contestée :** tout écran qui s'interpose entre la fin de génération et le retour au produit se bat contre l'excitation. L'**interstitiel post-génération** — candidat touchpoint évident, et celui retenu par l'exemple BlaBlaCar Boost — meurt ici.

### Intervention 2 — Pas d'écran d'effets de bord

> Il n'y a pas d'écran effets de bord. L'utilisateur, en voyant ce qui a changé dans la logique métier, les endpoints et les pages, pourra vérifier qu'aucun malentendu ne s'est immiscé, et aussi vérifier « est-ce que ça respecte mon intention ».

**E22 et E23 disparaissent comme écrans.** Les effets de bord et la conformité à l'intention ne sont pas des fonctions : ce sont deux **lectures** que le diff des trois vues doit rendre possibles. Cohérent avec la conséquence posée en Avant/Après : la seule sortie de la vue est l'attention humaine.

### Intervention 3 — L'intention vit dans la tête, en v1

> En v1 l'intention vit dans la tête de l'utilisateur. Une feature sera ajoutée ensuite pour confronter les fichiers qu'il utilise (PLAN.md, PRD, page Notion via serveur MCP ou autre) à la réalité de ce qui a été implémenté en code.

**E32 sort de la v1** sans être écarté : il devient une extension identifiée, aux sources multiples. La veine 1 d'Avant/Après (le PLAN.md, A34–A42) n'est donc pas exploitable comme touchpoint produit à ce stade. En v1, l'écran de confrontation est l'utilisateur lui-même.

---

### VAGUE 2 — Les écrans que la bifurcation fait apparaître

#### Zone E — La preview de l'app

Si la QA manuelle est dans le flow, alors l'app en train de tourner est un écran du parcours. Aucune activité ne l'avait listé.

- **E33.** La preview de l'app — dans Nuée, ou dans un navigateur à côté ?
- **E34.** L'écran de lancement / redémarrage du serveur de dev.
- **E35.** L'écran d'erreur au runtime : l'app ne démarre pas, la QA est impossible.
- **E36.** Le passage preview → vue : « j'ai vu ça à l'écran, quelle règle le produit ? »
- **E37.** Le passage vue → preview : « cette règle, elle se voit où ? »
- **E38.** L'écran où les deux cohabitent : app à gauche, vue à droite.

E33 relevé comme le choix d'architecture le plus lourd de la liste : Cursor n'embarque pas la preview, Lovable oui, et la bascule hors de Cursor / Lovable (A19) se joue en partie là-dessus.

#### Zone C — refondue après l'intervention 2

- **E21 (révisé).** Le diff des trois vues depuis le dernier prompt. Écran unique au cœur du tweet.
- **E39.** Le diff vue *règles métier* — celui que rien d'autre ne couvre.
- **E40.** Le diff vue *endpoints* — idem.
- **E41.** Le diff vue *pages* — celui que la QA front a déjà partiellement fait.
- **E42.** L'ordre d'entrée dans le diff : par quelle vue on ouvre, et qui décide.
- **E43.** L'écran « rien n'a changé » — le non-événement P1, cas majoritaire.

#### Zone F — La nature de la tâche

La bifurcation suppose que quelqu'un sache si la tâche était front ou back.

- **E44.** L'utilisateur le dit lui-même en prompt.
- **E45.** Nuée le déduit du diff de code.
- **E46.** Nuée ne le sait pas et ouvre toujours la même vue.
- **E47.** L'écran d'une tâche mixte — front *et* back, le cas réel le plus fréquent.
- **E48.** L'écran d'une tâche qui ne touche aucune des trois vues (refacto, dépendance, config) : la vue n'a rien à dire, et doit le dire.

#### Deux points signalés à l'issue de la vague 2

- **La deuxième promesse du tweet est portée par un diff neutre.** « Ce qu'elle change ailleurs » suppose de distinguer ce qui a été demandé du reste. Nuée ne peut le faire qu'en lisant le prompt. Le 4ᵉ principe interdit d'*intervenir* sur le trajet du prompt ; il ne dit rien sur le fait de le *lire*. Angle mort, non tranché.
- **La vue *pages* est en concurrence frontale avec la QA manuelle**, et sur le front elle arrive après.

---

### Intervention 4 — L'élagage

> **E33 :** la preview est dans un navigateur à côté. L'utilisateur clique sur le lien qui l'amène sur localhost, comme sur Cursor ou VS Code.
>
> **E34, E35 :** Nuée possède un terminal classique.
>
> **E36 :** on espère que les vues soient assez faciles à comprendre pour que l'utilisateur qui se pose cette question y réponde en voyant la vue. Enjeu d'usabilité, pas de discovery.
>
> **E38 :** non.
>
> **Zone F :** personne n'a besoin de savoir si c'est du front ou du back en dehors de l'utilisateur. Il fera toujours QA + Nuée ; l'ordre est son habitude, pas une mécanique produit. On lui laisse choisir ce qu'il veut vérifier en premier. L'important c'est que preview et vue Nuée soient faciles à atteindre en un clic.
>
> **Vue pages vs QA :** oui elle est en concurrence frontale, et oui parfois elle perdra. Mais chez le vibecodeur elle perdra beaucoup moins souvent que la vue « code » des IDE ne perd face à la QA.
>
> **Jour 1 :** écran d'accueil basique. **Reprise après absence :** rien.

Le flow d'ancrage prend sa forme finale — la bifurcation disparaît comme mécanique produit et devient une habitude d'utilisateur :

```
F1 brancher l'agent → F2 prompter → F3 l'agent code → F4 la vue se recalcule
                                   │
                      F5  l'utilisateur choisit par quoi il commence
                          ├─ un clic → navigateur (localhost) : QA manuelle
                          └─ un clic → vue Nuée : lecture du diff
                          (il fait toujours les deux, l'ordre lui appartient)
                                   │
                          F6 repérer l'écart
                    F7 reprompter / accepter → F8 ship
```

Il ne reste de toute l'analyse front/back **qu'une seule exigence d'architecture** : preview et vue doivent être atteignables en un clic chacune, dans n'importe quel ordre, autant de fois que voulu.

---

### L'architecture retenue

| # | Écran | Note |
|---|---|---|
| E1 | Accueil / jour 1 | basique, assumé |
| E2 | Branchement du moteur, clé API | non discuté au cours de l'activité |
| E9 | Chat de l'agent | sollicité, pas modifié |
| E10 | Vue règles métier | |
| E11 | Vue pages | |
| E12 | Vue endpoints | |
| E13 | Bascule entre les trois vues | le geste central |
| E14 | Indicateur de fraîcheur | 3ᵉ principe |
| E16 | Détail d'une règle | |
| E21 | Le diff depuis le dernier prompt | le cœur du tweet |
| E43 | « Rien n'a changé » | le cas majoritaire |
| E20 | Terminal classique | couvre E34, E35 |
| — | Lien localhost → navigateur | **hors produit** |

Onze écrans, dont trois sont la même chose vue sous trois angles.

### Les écrans écartés

E5 (import de projet existant), E22 (effets de bord), E23 (conformité à l'intention), E28 (reprise après absence), E33 et E38 (preview embarquée, cohabitation côte à côte), E36 et E37 (navigation croisée preview ↔ vue — requalifiés en enjeu d'usabilité), E44 à E47 (détection front / back).

E32 (confrontation à un document d'intention) : hors v1, feature identifiée pour la suite.

### Les non-tranchés

Écrans produits par l'activité et sur lesquels aucun arbitrage n'a été rendu. Ils ne sont ni retenus ni écartés :

- **E24** — copier une règle de la vue vers le prompt (A44 / P3, seul canal vue → agent depuis le 4ᵉ principe).
- **E26** — prompter contre la vue : « ce n'est pas ce que je voulais » (A46).
- **E27** — marquage vu / pas vu (P6), candidat « zéro complexité, fort impact ».
- **E17** — navigation transversale règle → page → endpoint.
- **E19** — choix du modèle de dérivation exposé à l'utilisateur (A62, Damage Control).
- **E48** — la tâche qui ne touche aucune des trois vues : la vue n'a rien à dire, le dit-elle ?
- **E3, E6, E7, E8, E15, E18, E25, E29, E30, E31, E39 à E42** — produits en divergence, non repris dans les arbitrages.
- **La lecture du prompt par Nuée** — non pas un écran, mais la condition pour que le diff distingue le demandé du non-demandé, donc pour que la deuxième promesse du tweet tienne.

### Observations de structure

- **L'architecture de Nuée est plate.** Il n'y a quasiment pas de parcours : un écran d'entrée, un atelier, trois vues et un diff. Le produit est un lieu où l'on revient, pas un chemin que l'on suit.
- **La preview sort du produit.** Le seul moment de récompense visuelle du parcours — voir son app bouger — se passe dans un navigateur que Nuée ne contrôle pas.
- **Le concurrent de la vue n'est pas la QA manuelle, c'est la vue « code » des IDE classiques.** C'est le déplacement le plus net produit par l'activité : la vue pages perd parfois face à la QA, mais beaucoup moins souvent que ne perd le code affiché dans un IDE.
- **Les trois trous de la vague 1 sont toujours ouverts après élagage.** Rien ne dit à l'utilisateur qu'il devrait regarder (F4 → F5) ; la comparaison de F6 n'a qu'une seule base, le code d'avant ; et il n'y a toujours rien après F8.

## Ce que j'en retiens pour le livrable

L'activité était censée fournir des touchpoints produit. Elle en fournit peu, et **c'est son résultat principal.**

**Ce qui reste comme moment produit capable de porter une éducation**

- **E21 — le diff des trois vues.** Seul écran à porter les trois promesses du Launch Tweet à lui seul. Traversé à chaque tour de boucle.
- **E14 — l'indicateur de fraîcheur.** Coût de mise en œuvre nul, et c'est l'écran qui décide si l'utilisateur peut faire confiance à ce qu'il lit.
- **E13 — la bascule entre les trois vues.** Le geste central du produit ; c'est lui qui expose l'existence des vues que la QA ne couvre pas.
- **E1 — l'accueil du jour 1.** Assumé basique, donc faible porteur, mais c'est le seul écran à bénéficier de l'effet de primauté.
- **E43 — « rien n'a changé ».** Le cas majoritaire (P1). C'est là que la confiance se construit ou se perd, et il ne coûte rien.

**Ce que l'activité ferme**

- L'**interstitiel post-génération** est mort : il se bat contre l'excitation qui commande le retour au produit.
- La **reprise après absence** est explicitement vide : plus de touchpoint côté A8 / P12.
- Le **PLAN.md** ne peut pas servir de touchpoint en v1.
- La **preview** est hors produit : aucun touchpoint ne peut s'y loger.

**La tension à porter au livrable**

L'architecture étant plate, **les 5 Touchpoints ne peuvent pas être majoritairement produit.** Il reste au mieux deux ou trois moments produit crédibles ; les autres devront être cherchés hors du produit — X, Discord, démonstration d'une vue peuplée (A27), recrutement pour la discovery (A29). L'activité **Mapping multicanal**, qui semblait secondaire au départ, devient de ce fait la source principale des touchpoints restants.

**Non abordé**

- Le **Mapping multicanal** et la **Journey line** n'ont pas été menés.
- Le contenu exact des vues — quelles informations remplacent le code — reste ouvert, comme à l'issue de Frame et d'Avant/Après.
- La passation à un tiers (P20) et le diagnostic d'un bug remonté par un utilisateur réel (P15) ont été tenus hors du champ de cette activité.
