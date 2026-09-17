# Guides SOTECHDI

Documentation publique des licences vendues par [SOTECHDI](https://sotechdi.com) :
guides d'activation Windows, Office, Kaspersky.

Site statique **MkDocs Material**, publié par GitHub Pages. Aucun serveur à
maintenir, et aucun hit consommé sur l'hébergement de sotechdi.com — ce qui
compte, sotechdi.com étant limité en nombre de visites par jour.

## Travailler dessus

```bash
py -m pip install -r requirements.txt
mkdocs serve      # aperçu sur http://127.0.0.1:8000, rechargement automatique
mkdocs build --strict
```

`--strict` fait échouer la construction au moindre avertissement — lien mort,
fichier absent. C'est ce que lance GitHub Actions : un lien cassé ne peut pas
atteindre le site.

## Ajouter un guide

1. Créer `docs/<rubrique>/<produit>.md`
2. L'ajouter à `nav:` dans `mkdocs.yml`
3. Pousser sur `main` — la publication est automatique

Reprendre la trame d'un guide existant : tableau produit, ce que le client
reçoit, prérequis, résultat attendu, étapes numérotées, vérification, FAQ,
assistance. Cette structure répond aux questions dans l'ordre où elles se
posent.

## Règles de fond

- **Ne jamais inventer une condition commerciale.** Les délais de livraison et
  la garantie viennent de
  [livraison-et-remboursement](https://sotechdi.com/livraison-et-remboursement/).
  Une documentation qui contredit la page de vente crée un litige.
- **Écrire pour quelqu'un qui n'y connaît rien**, sur un téléphone, en 3G.
- **Donner la cause avant la solution** : « les erreurs de saisie viennent de
  la confusion entre 0 et O » vaut mieux que « saisissez correctement ».

## Mise en ligne

GitHub → Settings → Pages → Source : **GitHub Actions**.
Le dépôt doit être **public** : Pages n'est gratuit qu'à cette condition.

Pour `docs.sotechdi.com` : ajouter un enregistrement CNAME chez le registrar
vers `sotechdi.github.io`, puis renseigner le domaine dans Settings → Pages.
