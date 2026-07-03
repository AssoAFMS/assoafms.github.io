# Site AFMS — Association Française des Métiers Scéniques

Site institutionnel statique (HTML / CSS / JS, sans dépendance de build), basé sur le
template **Halcyonic** (HTML5 UP) recoloré en thème sombre théâtre, hébergé gratuitement
sur **GitHub Pages** sous le compte **AssoAFMS**.

Dépôt : https://github.com/AssoAFMS/assoafms.github.io — nommé `<compte>.github.io`,
ce qui en fait le site GitHub Pages principal du compte, servi nativement à
`https://assoafms.github.io/`.

**Domaine personnalisé (`afms.info`) : pas encore activé.** Le champ "Custom domain" a
été volontairement laissé vide dans Settings → Pages pour l'instant. Le site reste donc
uniquement accessible via `assoafms.github.io` tant que ce choix n'est pas revu (voir
section « Activer le domaine personnalisé plus tard » ci-dessous).

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

## 1. Dépôt — fait ✅

Le dépôt `AssoAFMS/assoafms.github.io` est créé, le code est poussé sur `main`, et le
remote local est configuré :

```bash
git remote -v
# origin  https://github.com/AssoAFMS/assoafms.github.io.git (fetch)
# origin  https://github.com/AssoAFMS/assoafms.github.io.git (push)
```

Pour un futur `git push` depuis cette machine, une authentification sera redemandée
(GitHub n'accepte plus les mots de passe classiques) : soit `gh auth login` (compte
AssoAFMS), soit un *Personal Access Token* utilisé comme mot de passe.

## 2. Activer le domaine personnalisé plus tard (optionnel)

Le site tourne pour l'instant uniquement sur `assoafms.github.io`. Quand la décision sera
prise de basculer `afms.info` dessus :

1. Recréer le fichier `CNAME` à la racine du dépôt avec `afms.info` dedans (ou le remettre
   directement depuis **Settings → Pages → Custom domain**, GitHub le recrée pour toi).
2. Chez le registrar/DNS du domaine `afms.info`, remplacer les enregistrements existants
   (ceux pointant vers WordPress.com) par les 4 enregistrements A GitHub Pages sur `@` :
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, plus un
   CNAME `www` → `AssoAFMS.github.io` pour que `www.afms.info` fonctionne aussi.
3. Cocher **Enforce HTTPS** dans Settings → Pages une fois le domaine validé (le certificat
   SSL est généré automatiquement par GitHub, ça peut prendre de quelques minutes à
   quelques heures après la propagation DNS).

⚠️ Si l'association utilise des adresses email @afms.info, ne pas toucher aux
enregistrements MX/TXT existants — seuls les A/CNAME pointant vers l'hébergement web
doivent être remplacés.

## Formulaire de contact

Le site est 100% statique (pas de serveur). Le formulaire de la page « Nous contacter »
ouvre le client mail de l'utilisateur (lien `mailto:`) pré-rempli vers `contact@afms.info`.
Pour un vrai formulaire avec envoi direct, il faudra brancher un service tiers gratuit
(ex. Formspree, Getform) — non fait par défaut pour rester sans dépendance externe.

## Contenu source

Le contenu (textes, organigramme, photos du bureau, logos des adhérents) a été repris du
site existant `afms.info` (WordPress.com) à des fins de migration.
