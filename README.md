# Kontwa — l'assistant de commande WhatsApp pour les petits commerces

🌐 **Site :** [kontwa.app](https://kontwa.app) · 📍 Projet pilote à Douala (Cameroun)

> Le code source de production est privé (il contient des intégrations et des données de commerçants réels). Ce dépôt présente le produit, son architecture et mes choix techniques.

## Le problème

À Douala, la plupart des petits commerces vendent par WhatsApp. Le commerçant répond lui-même à chaque client, à toute heure : prix, photos, livraison, paiement. Les messages se perdent, les commandes aussi.

## La solution

Kontwa répond automatiquement aux clients **sur le numéro WhatsApp habituel du commerce**, sans application à installer :

- 🛍️ **Catalogue et prix** : le client demande, Kontwa répond avec les produits, les prix et les photos.
- 🧾 **Commande guidée** : du choix des produits jusqu'à la commande confirmée, avec un code de commande.
- 🚚 **Livraison** : zones de livraison, frais et horaires d'ouverture.
- 💳 **Paiement** : instructions Orange Money / MTN Mobile Money. Kontwa ne manipule jamais l'argent des clients.
- 📲 **Gestion depuis le téléphone** : le commerçant tape « menu » pour gérer ses commandes, prix, promotions et stock.
- 🙋 **Relais humain** : les questions que le bot ne comprend pas sont transmises au commerçant.

Kontwa est en service chez des commerçants réels (une parfumerie à Douala), dans le cadre d'un projet pilote.

## Architecture

```
Client WhatsApp
      │
      ▼
API WhatsApp Cloud (Meta) ──webhook──▶ API Node.js / TypeScript (Vercel)
                                              │
                                              ├── Logique de conversation (catalogue, commande, livraison)
                                              ├── Firebase (Firestore) : catalogues, commandes, sessions
                                              └── Notifications au commerçant
```

## Stack technique

| Domaine | Technologies |
|---|---|
| Back-end | Node.js, TypeScript, API REST, webhooks |
| Messagerie | API WhatsApp Cloud de Meta (application publiée, jeton d'accès système permanent) |
| Données | Firebase / Firestore |
| Hébergement | Vercel (serverless) |
| Site vitrine | kontwa.app |

## Ce que ce projet m'a appris

- **Mettre une intégration Meta en production** : configuration des webhooks, publication de l'application, passage d'un jeton temporaire à un jeton d'utilisateur système sans expiration.
- **Concevoir pour de vrais utilisateurs** : les commerçants ne veulent pas changer de numéro ni installer d'application. Le produit s'adapte à leurs habitudes, pas l'inverse.
- **Protéger les données** : pages de confidentialité, de suppression des données et conditions d'utilisation publiées, secrets hors du code.

## Auteur

**Yvan Kameni** — Développeur full-stack Web & Mobile, Québec
[GitHub](https://github.com/Kameni2000) · [LinkedIn](https://www.linkedin.com/in/yvan-kameni-dev)
