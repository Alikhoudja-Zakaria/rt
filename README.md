# Qrmeunu - Votre menu, en un scan 🇩🇿

Site web mobile-first pour le service de menu et commande par QR code destiné aux restaurants et cafés algériens.

## 🚀 Fonctionnalités

- **Landing Page Mobile-First (`index.html`)** :
  - Design direct inspiré des publicités mobiles / stories (simple, clair et rassurant).
  - Charte graphique Qrmeunu : Terracotta (#C75B39), Teal (#2A9D8F), typographie Poppins.
  - Slogan en français et en darja : *"حط الكود، الكليان يطلب وحدو"*.
  - 3 formules tarifaires :
    - **Basic** : 2 000 DA/mois (24 000 DA/an)
    - **Commande** : 4 000 DA/mois (48 000 DA/an)
    - **Caisse Pro** : 4 680 DA/mois au lieu de 5 200 DA/mois (-10%, 56 160 DA/an)
  - Formulaire de commande simple : Nom, Nom du restaurant, Téléphone, Email (optionnel), Wilaya (58 wilayas d'Algérie), Choix de formule.
  - Envoi instantané vers **Cloud Firestore** + redirection WhatsApp automatique vers le `+213 656 24 3117` avec les détails pré-remplis.
  - Bouton flottant WhatsApp toujours accessible.
  - Suivi Google Analytics / Firebase Analytics (`G-LCB8BJ3X0P`).

- **Tableau de Bord Admin (`admin.html`)** :
  - Synchronisation en direct avec Cloud Firestore (`leads`).
  - Statistiques en temps réel (total leads, leads aujourd'hui, répartition par formule).
  - Filtres par recherche, wilaya, formule et date.
  - Gestion du statut des commandes (Nouveau / Contacté / Confirmé) synchronisée dans Firestore.
  - Boutons d'action rapide : Appel téléphonique en 1 clic, ouverture du chat WhatsApp pré-rempli, suppression.
  - Bouton d'export CSV pour tableur (Excel / Google Sheets).
  - Générateur de données de test.
  - Mode secours hors-ligne (localStorage) en cas de coupure réseau.

## ⚙️ Configuration Firebase & Firestore

Le projet est connecté au projet Firebase `restau-dfbb2`.

### Règles de sécurité Firestore recommandées (Mode Test / Production)

Dans la [Console Firebase](https://console.firebase.google.com/project/restau-dfbb2/firestore/rules) :

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /leads/{leadId} {
      // Permet aux clients de créer une demande et à l'admin de lire/modifier
      allow read, write: if true;
    }
  }
}
```
