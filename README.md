# La Boutique du Coin

Logiciel de caisse de la Boutique du Coin, assaini lors de la revue du J8 : règles métier, sécurité, tests.

---

## Règles métier

1. **Livraison** : 4,90 €, **offerte** à partir de **50 € d'achats** (50 € inclus).
2. **Fidélité** : 1 point = 1 % de remise, plafonnée à **20 %**.
3. La remise s'applique sur les **articles**, pas sur les frais de port.
4. **L'argent ne peut jamais devenir négatif** (total, remise, stock).
5. **Stock** : impossible de vendre plus que le stock disponible.
6. **Aucun secret en dur** dans le code (clé API dans l'environnement uniquement).
7. **Aucune entrée utilisateur collée** dans une requête SQL (toujours paramétrée).

---

## Les robots de ce repo

Trois agents GitHub Actions (dans `.github/workflows/`, à copier depuis `../robots/`) :

- **Le garde** — lance `pytest -v` à chaque push et sur chaque Pull Request. Il interdit la fusion si un test rouge.
- **Le relecteur** — sur chaque Pull Request, lit les changements, les juge selon `CONVENTIONS.md`, et poste son verdict en commentaire. Lecture seule + droit de commenter.
- **Le veilleur de nuit** — chaque nuit à 3h (heure de Paris), fait la ronde du repo via un agent OpenCode et ouvre une issue-rapport.

Règle de la maison : **les robots proposent, l'humain merge.**

---

## Lancer les tests

```
python -m pytest -v
```
