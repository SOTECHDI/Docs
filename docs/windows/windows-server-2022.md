# Windows Server 2022 Standard — guide d'activation

!!! danger "Guide destiné aux administrateurs système"

    Contrairement aux autres guides de ce site, celui-ci suppose que vous
    savez ce qu'est une invite de commande en mode administrateur et que vous
    intervenez sur un serveur en connaissance de cause.

    En cas de doute, **ne tentez rien sur un serveur en production**.
    Écrivez-nous : l'intervention est possible à distance ou sur site.

## Informations produit

| Champ | Valeur |
|---|---|
| **Type de licence** | Clé de produit |
| **Durée** | Perpétuelle |
| **Portée** | 1 serveur — 16 cœurs, extensible par paliers de 2 |
| **Machines virtuelles** | 2 environnements virtuels inclus |
| **Compatibilité** | Windows Server 2022 Standard |
| **Livraison** | Par courriel, sous 24 h ouvrées après confirmation du paiement |
| **Garantie** | Clé remplacée si elle ne fonctionne pas ; remboursée si le remplacement échoue |

!!! warning "Vérifiez l'édition avant toute chose"

    Cette clé active l'édition **Standard**. Elle ne fonctionnera ni sur
    **Datacenter**, ni sur **Essentials**.

    Pour connaître l'édition installée, dans PowerShell :

    ```powershell
    Get-ComputerInfo -Property WindowsProductName
    ```

    Une **connexion internet** est nécessaire pour l'activation en ligne. Si
    le serveur n'en a pas — ce qui est fréquent en salle machine — voyez
    l'activation par téléphone plus bas.

!!! success "À la fin de ce guide"

    - `slmgr /xpr` répond **« Le poste est activé de façon permanente »**
    - Plus aucun avertissement d'expiration de licence
    - Le serveur redémarre sans réclamer d'activation

---

## Méthode 1 — Par l'interface graphique

**Paramètres** → **Système** → **Activation** → **Modifier la clé de produit**

Saisissez les 25 caractères, puis validez. Windows contacte les serveurs de
Microsoft et active la licence.

C'est la méthode la plus simple, et elle suffit dans la plupart des cas.

## Méthode 2 — En ligne de commande

Utile sur une installation **Server Core**, sans interface graphique, ou pour
scripter un déploiement.

Ouvrez une invite de commandes **en tant qu'administrateur** :

```batch
slmgr /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
slmgr /ato
```

- `/ipk` installe la clé de produit
- `/ato` déclenche l'activation auprès de Microsoft

Chaque commande ouvre une fenêtre de confirmation. Comptez quelques secondes
entre les deux.

---

## Vérifier l'activation

```batch
slmgr /xpr
```

La réponse attendue :

> **Le poste est activé de façon permanente.**

Pour le détail complet — édition, canal de licence, derniers chiffres de la
clé :

```batch
slmgr /dlv
```

---

## Si le serveur n'a pas d'accès internet

L'activation par téléphone reste disponible :

```batch
slui 4
```

Windows affiche un identifiant d'installation et le numéro à appeler pour
votre pays. Vous dictez l'identifiant, un identifiant de confirmation vous est
donné en retour, et vous le saisissez à l'écran.

C'est long mais fiable. Prévoyez de quoi noter : les identifiants font une
cinquantaine de chiffres.

---

## Questions fréquentes

??? question "Mon serveur a plus de 16 cœurs. Que faire ?"

    La licence Standard couvre **16 cœurs**. Au-delà, il faut des licences
    complémentaires par paliers de 2 cœurs.

    Comptez vos cœurs physiques — pas les threads — puis écrivez-nous avec ce
    chiffre : nous vous dirons ce qu'il faut ajouter.

??? question "Combien de machines virtuelles puis-je exécuter ?"

    Standard inclut **deux** environnements Windows Server virtualisés. Au
    delà, il faut soit des licences Standard supplémentaires, soit une licence
    Datacenter, qui autorise un nombre illimité de machines virtuelles.

??? question "Erreur 0xC004F050 — clé refusée"

    Presque toujours une **erreur d'édition** : clé Standard saisie sur
    Datacenter ou Essentials, ou l'inverse. Vérifiez avec
    `Get-ComputerInfo -Property WindowsProductName`.

    Vient ensuite l'erreur de saisie : copiez-collez plutôt que de recopier.

??? question "Puis-je transférer la licence sur un autre serveur ?"

    Cela dépend du canal de licence. Écrivez-nous avec votre numéro de
    commande et le résultat de `slmgr /dlv` : nous vous dirons ce que permet
    votre licence.

---

## Assistance

Écrivez-nous avec votre **numéro de commande**, le résultat de `slmgr /dlv` et
le code d'erreur s'il y en a un.

- **WhatsApp** — [+226 46 83 83 57](https://wa.me/22646838357)
- **Courriel** — [contact@sotechdi.com](mailto:contact@sotechdi.com)
- **Boutique** — [sotechdi.com](https://sotechdi.com)

SOTECHDI propose également l'**installation et la configuration sur site**
pour les serveurs et le matériel réseau — demandez un devis.
