# Site AFMS — Association Française des Métiers Scéniques

Site institutionnel statique (HTML / CSS / JS, sans dépendance de build), basé sur le
template **Halcyonic** (HTML5 UP) recoloré en thème sombre théâtre, hébergé gratuitement
sur **GitHub Pages** sous le compte **AssoAFMS**, avec le domaine personnalisé `afms.info`.

## Contenu

- `index.html` — Accueil
- `actualites.html` — Actualités
- `nos-metiers.html` — Nos métiers
- `qui-sommes-nous.html` — Qui sommes nous ?
- `nos-missions.html` — Nos missions
- `adherer.html` — Adhérer
- `contact.html` — Nous contacter
- `assets/css/main.css` — Feuille de style (grille + thème sombre théâtre : noir, bordeaux, doré)
- `assets/js/` — jQuery + scripts du template (menu mobile "tiroir" natif)
- `assets/images/logo.png` — Logo AFMS
- `images/` — Photos du bureau, logos des entreprises membres, illustrations SVG
- `CNAME` — domaine personnalisé (`afms.info`)

## 1. Créer le dépôt sous le compte AssoAFMS

1. Connecte-toi sur GitHub avec le compte **AssoAFMS**.
2. Va sur https://github.com/new
3. Nom du dépôt : `afms-website` (ou le nom de ton choix — sans impact car un domaine
   personnalisé est utilisé).
4. Visibilité : **Public** (obligatoire pour GitHub Pages gratuit sur un compte non-Pro,
   sauf si le compte AssoAFMS a GitHub Pro/Team).
5. Ne coche **aucune** case d'initialisation (pas de README/gitignore/licence) : le dépôt
   local en a déjà.
6. Clique **Create repository**.

## 2. Pousser le code depuis cette machine

Le dépôt local est déjà initialisé et commité. Il ne reste qu'à le relier au dépôt distant
et pousser — à exécuter depuis ce dossier :

```bash
git remote add origin https://github.com/AssoAFMS/afms-website.git
git push -u origin main
```

Si `git push` demande une authentification : GitHub n'accepte plus les mots de passe en
ligne de commande. Deux options :

- **Le plus simple** : installer `gh` (GitHub CLI) puis `gh auth login`, en te connectant
  avec le compte AssoAFMS. Ensuite `git push -u origin main` fonctionnera normalement.
- **Alternative** : créer un *Personal Access Token* (Settings → Developer settings →
  Personal access tokens sur le compte AssoAFMS) et l'utiliser comme mot de passe quand
  Git le demande.

## 3. Activer GitHub Pages

1. Sur le dépôt GitHub : **Settings → Pages**.
2. Source : **Deploy from a branch**.
3. Branche : `main`, dossier `/ (root)`.
4. Dans le champ **Custom domain**, entre `afms.info` puis **Save**
   (GitHub met à jour le fichier `CNAME` automatiquement si besoin — il existe déjà ici).
5. Coche **Enforce HTTPS** dès que la case devient disponible (le certificat SSL est
   généré automatiquement par GitHub après validation du domaine, ça peut prendre
   quelques minutes à quelques heures).

## 4. Configurer le DNS chez le registrar du domaine afms.info

Domaine choisi : **apex `afms.info`** (recommandé par GitHub). Chez le registrar/DNS
actuel du domaine (là où sont gérés les enregistrements DNS d'afms.info), remplace les
enregistrements existants (ceux pointant vers WordPress.com) par :

**4 enregistrements A sur `@` / racine (`afms.info`) :**

| Type | Nom | Valeur           |
|------|-----|-------------------|
| A    | @   | 185.199.108.153   |
| A    | @   | 185.199.109.153   |
| A    | @   | 185.199.110.153   |
| A    | @   | 185.199.111.153   |

**Optionnel (IPv6) — 4 enregistrements AAAA sur `@` :**

| Type | Nom | Valeur                    |
|------|-----|----------------------------|
| AAAA | @   | 2606:50c0:8000::153        |
| AAAA | @   | 2606:50c0:8001::153        |
| AAAA | @   | 2606:50c0:8002::153        |
| AAAA | @   | 2606:50c0:8003::153        |

**1 enregistrement CNAME pour `www` (pour que `www.afms.info` redirige aussi vers le site) :**

| Type  | Nom | Valeur                |
|-------|-----|------------------------|
| CNAME | www | AssoAFMS.github.io     |

Supprime tout enregistrement A/CNAME/MX-conflictuel existant pointant vers l'ancien
hébergeur WordPress.com pour `@` et `www` (garde les enregistrements liés aux emails,
type MX/TXT, si l'association utilise des adresses @afms.info par ailleurs — à vérifier
avant de tout supprimer).

La propagation DNS peut prendre de quelques minutes à 24-48h. Une fois propagée, GitHub
détecte automatiquement le domaine et délivre le certificat HTTPS.

## Formulaire de contact

Le site est 100% statique (pas de serveur). Le formulaire de la page « Nous contacter »
ouvre le client mail de l'utilisateur (lien `mailto:`) pré-rempli vers `contact@afms.info`.
Pour un vrai formulaire avec envoi direct, il faudra brancher un service tiers gratuit
(ex. Formspree, Getform) — non fait par défaut pour rester sans dépendance externe.

## Contenu source

Le contenu (textes, organigramme, photos du bureau, logos des adhérents) a été repris du
site existant `afms.info` (WordPress.com) à des fins de migration.
