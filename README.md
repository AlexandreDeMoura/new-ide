# new-ide — Discovery FOCUSED

Ce repo héberge la réflexion produit d'un projet mené avec la méthodologie **FOCUSED** 

Il n'y a pas de code ici. Le livrable de ce repo, c'est la pensée : les activités qui l'ont produite, les livrables qui la figent, et l'historique git qui garde la trace des arbitrages.

**Sujet du projet :** L'objectif de ce projet est de réfléchir à la place de l'IDE dans un monde où l'IA écrit 100% du code et où l'arborescence de fichier d'une codebase où le code source d'un fichier ne sont probablement plus les bonnes informations à montrer aux builders. 

---

## Les 7 étapes

| # | Étape | Livrable | Question à laquelle il répond |
|---|-------|----------|-------------------------------|
| 1 | **F**rame | Project Ambition | Qu'est-ce qui nous ferait dire que ce projet est un succès ? |
| 2 | **O**bserve | First Use Case | Quel problème utilisateur précis résout-on en premier ? |
| 3 | **C**laim | Launch Tweet | Quelle promesse engage-t-on, en moins de 280 signes ? |
| 4 | **U**nfold | 5 Touchpoints | Par quels 5 points de contact clés cette promesse atteint-elle l'utilisateur ? |
| 5 | **S**teal | Gold Nuggets | Quelles 5 idées existantes réutilise-t-on comme socle de la solution ? |
| 6 | **E**xecute | Happy Path | À quoi ressemble le parcours clé, et quelles 3 hypothèses le valident ? |
| 7 | **D**ecide | Go / No Go | La solution est-elle prête à passer en delivery ? |

Chaque étape suit le même rythme : **divergence** (activités : explorer, accumuler, ne pas trancher) puis **convergence** (livrable : choisir, renoncer, figer). Le livrable d'une étape sert de filtre de décision pour les suivantes.

---

## Structure

```
methodology/     Présentation, template de livrable, erreur courante et exemple
                 pour chacune des 7 étapes. Contenu de référence, réutilisable
                 d'un projet à l'autre. On n'y écrit pas de contenu projet.

activities/      Phase divergente. Un fichier daté par activité menée, rangé
                 dans le sous-dossier de son étape. Immuable une fois écrit.

deliverables/    Phase convergente. Un fichier par livrable, vivant : il évolue
                 jusqu'à être figé. C'est git qui en suit l'évolution.
```

---

## Conventions

**Fichiers d'activité** — `activities/<n>-<etape>/AAAA-MM-JJ-NN-nom-activite.md`

```
activities/2-observe/2026-08-17-01-guerilla-interviews.md
activities/2-observe/2026-08-17-02-analyse-verbatims.md
```

Le `NN` permet plusieurs activités le même jour tout en gardant un tri lexicographique stable. La date est celle de la réalisation de l'activité, pas celle de la mise au propre.

**Règle d'immuabilité :** un fichier d'activité ne se modifie plus une fois écrit. C'est ce qui garde l'historique honnête — ce qu'on croyait ce jour-là, pas ce qu'on aurait aimé croire. Une conclusion qui évolue donne lieu à une nouvelle activité datée, pas à une réécriture. Seule exception : corriger une coquille.

**Fichiers de livrable** — `deliverables/<n>-<nom-livrable>.md`

```
deliverables/1-project-ambition.md
deliverables/2-first-use-case.md
```

Ceux-là sont mutables et le resteront jusqu'à ce que l'étape soit figée.

**Commits** — format `<type>(<étape>): <l'arbitrage rendu>`, avec des types propres à la discovery plutôt que `feat`/`fix`/`chore` :

| Type | Événement |
|------|-----------|
| `act` | Une activité divergente a été menée et consignée |
| `liv` | Le livrable évolue — convergence en cours |
| `fig` | Le livrable est figé, l'étape est close |
| `iter` | On rouvre une étape déjà figée |
| `docs` | Méthodologie, README, CLAUDE.md, structure du repo |

```
liv(frame): on retient le taux de complétion du profil comme critère de succès

Renoncé: rétention à 30 jours — donnée indisponible avant Q3, hors timebox
```

Le message porte l'arbitrage, pas l'action. C'est le seul endroit du repo où vit le *pourquoi* d'un renoncement : `git log deliverables/1-project-ambition.md` doit se lire comme l'historique des choix, `git log --oneline --grep='^fig'` comme la colonne vertébrale du projet.

Le détail de la convention (trailer `Renoncé:`, usage de chaque type) est dans [CLAUDE.md](CLAUDE.md).

**Tags** — un tag par livrable figé : `frame-v1`, `observe-v1`, etc. Point de retour propre vers l'état de la pensée au moment où l'étape a été close.

**Branches** — on reste sur `main`. La divergence vit dans les fichiers d'activité, pas dans des branches. Une branche ne se justifie que pour mener en parallèle deux directions produit réellement incompatibles qu'on veut comparer.

---

## État d'avancement

| Étape | Activités | Livrable | Statut |
|-------|-----------|----------|--------|
| 1. Frame | 2 | figé (`frame-v1`) | close |
| 2. Observe | 0 | figé (`observe-v1`) | close |
| 3. Claim | 0 | figé (`claim-v1`) | close |
| 4. Unfold | 1 | — | en cours |
| 5. Steal | — | — | à démarrer |
| 6. Execute | — | — | à démarrer |
| 7. Decide | — | — | à démarrer |

_Ce tableau est mis à jour à chaque fin d'étape._
