# Mix'Menu · V1 de test

Les enfants composent les dîners de la semaine à tour de rôle : trois « tapis du chef » mélangent une protéine, un légume et un féculent, le repas part dans le jour choisi, puis on ajuste par échanges ou jokers.

## Contenu

| Fichier | Rôle |
|---|---|
| `index.html` | L'application complète (une seule page, aucune installation) |
| `modele-mixmenu.csv` | Modèle du tableur des aliments, à importer dans Google Sheets |

## Mettre en ligne sur GitHub Pages

1. Crée un dépôt public sur GitHub (ex. `mixmenu`).
2. Dépose `index.html` à la racine (bouton **Add file → Upload files**).
3. **Settings → Pages** → Source : *Deploy from a branch*, branche `main`, dossier `/ (root)` → **Save**.
4. Après une à deux minutes, l'adresse `https://<ton-pseudo>.github.io/mixmenu/` est active.
5. Sur la tablette : ouvre l'adresse puis **Ajouter à l'écran d'accueil** pour l'avoir comme une appli.

## Brancher le Google Sheet (facultatif)

L'application fonctionne sans tableur grâce aux données intégrées. Pour gérer les aliments toi-même :

1. Google Sheets → **Fichier → Importer** → `modele-mixmenu.csv`.
2. **Fichier → Partager → Publier sur le web** → choisir l'onglet → format **CSV** → Publier → copier le lien.
3. Dans l'appli : ⚙️ → code parent → onglet **Données** → coller le lien → **Charger**.

L'appli relit le tableur à chaque ouverture et garde la dernière version en mémoire si le réseau manque.

### Colonnes du tableur

| Colonne | Contenu |
|---|---|
| `categorie` | `proteine`, `legume`, `feculent` ou `joker` |
| `nom` | Nom affiché |
| `emoji` | Pictogramme affiché |
| `tags` | Étiquettes séparées par `|` (ex. `poisson`, `viande-rouge`, `porc`, `volaille`, `oeuf`, `vegetarien`). Une limite par semaine se règle ensuite pour chaque étiquette dans l'onglet Règles. |
| `couleur` | Pour les légumes : `rouge`, `orange`, `jaune`, `vert`, `violet`, `blanc`, `marron` (sert au badge Arc-en-ciel) |
| `incompatible_avec` | Noms d'aliments à ne jamais associer, séparés par `|` (ex. `Petits pois`) |
| `actif` | `oui` / `non` |

## Ce que fait la V1

- **Mixeur** : trois tapis qui s'arrêtent l'un après l'autre. Un seul mélange par jour (pas de relance à volonté), pour rester sur un choix et non sur un jeu de hasard.
- **Tour de rôle** : chaque enfant compose ses jours, l'avatar du « chef du jour » est affiché.
- **Règles appliquées au tirage** : limites par étiquette (poisson ≤ 2 par défaut…), pas de protéine ni de légume répétés, pas le même féculent deux jours de suite, associations interdites.
- **Goûts par enfant** : ❤️ revient plus souvent quand c'est son tour, 🚫 jamais quand c'est son tour.
- **Échanges** : toucher un aliment puis un autre de la même catégorie, ou appui long et glisser. Un échange qui casse une règle est refusé avec un message.
- **Jokers** : touche le jour (colonne de gauche) → choix du joker. 2 par semaine par défaut.
- **Étoiles** : +5 par jour composé, +5 par légume différent, +10 pour un légume jamais choisi avant, +10 semaine complète, +15 badge Arc-en-ciel (4 couleurs de légumes). Rien n'est lié à ce qui est mangé. Niveaux : Apprenti marmiton → Commis → Cuistot → Second → Chef → Grand chef.
- **Fin de semaine** : confettis, bilan et étoiles gagnées.
- **Impression / PDF** : bouton Imprimer (A4 paysage). Pour un PDF : *Enregistrer en PDF* dans la fenêtre d'impression.
- **Espace parent** (code par défaut `0000`) : enfants (4 max), aliments, goûts, jours actifs, limites, thème (Cuisine, Océan, Espace), code, source de données.

## Limites connues de la V1

- Les données (enfants, étoiles, semaine) sont enregistrées **dans le navigateur de l'appareil** : la tablette et le téléphone ne partagent pas la même semaine.
- Le tableur est en lecture seule : l'appli n'y écrit rien.

## Pistes V2

- Synchronisation entre appareils (Google Apps Script, gratuit) et historique des menus.
- Liste de courses générée à partir du menu.
- Application installable hors ligne (PWA).
- Thèmes par enfant. Pour une version commerciale, des univers originaux sont libres ; des personnages sous licence (One Piece, Fortnite, Reine des neiges) demandent un accord des ayants droit.
