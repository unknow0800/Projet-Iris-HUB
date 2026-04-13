# 🎓 Iris Paris Hub — Espace Étudiant

> Plateforme étudiante officielle de l'école **IRIS Paris** (Groupe MediaSchool).  
> Projet pédagogique **BTS SIO option SLAM** — Développement Web Front-End.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-222?style=flat-square&logo=github&logoColor=white)

---

## 📋 Présentation du projet

**Iris Paris Hub** est un site web statique qui centralise la vie étudiante de l'école IRIS Paris.  
Il s'adresse aux étudiants en BTS SIO, Bachelor et Mastère et propose :

- Une **page d'accueil publique** avec les informations clés du campus
- Un **espace étudiant connecté** (dashboard) accessible après inscription
- Un **chat de promo en temps réel** avec protection d'accès par promotion
- Un **assistant IA** propulsé par l'API Claude (Anthropic)
- Des **mini-jeux** (quiz culture générale + tech)
- Une **météo Paris** en direct et un **compte à rebours** vers le prochain événement
- Un système de **thèmes** (sombre / clair / couleur d'accent)

---

## 🗂️ Structure du dépôt

```
iris-paris-hub/
│
├── index.html                  ← Site complet (HTML + CSS + JS en un seul fichier)
├── README.md                   ← Ce fichier
├── SETUP.md                    ← Guide de configuration Firebase / OAuth
├── .gitignore
├── LICENSE
│
├── docs/                       ← Livrables scolaires
│   ├── cahier-des-charges.md   ← CDC complet du projet BTS SIO
│   ├── wireframe-iris-paris.pdf← Wireframe lo-fi 6 pages (style sketch)
│   └── presentation.md         ← Plan de la présentation orale
│
├── assets/                     ← Ressources statiques
│   └── img/
│       ├── logo-iris.svg        ← Logo Iris (cartouche jaune sur fond bleu marine)
│       ├── og-image.png         ← Image Open Graph pour le partage sur les réseaux
│       └── favicon.ico          ← Icône onglet navigateur
│
└── .github/
    ├── workflows/
    │   └── deploy.yml           ← Déploiement automatique sur GitHub Pages
    └── ISSUE_TEMPLATE.md        ← Template pour les rapports de bug
```

---

## ✨ Fonctionnalités

### Page publique (sans connexion)
| Fonctionnalité | Description |
|---|---|
| 🏠 Hero animé | Titre plein écran, photos flottantes, boutons CTA |
| 📊 Marquee stats | Chiffres clés de l'école en défilement infini |
| 🖼️ Grille photos | 5 photos campus en CSS Grid asymétrique |
| 🗂️ Cards services | 6 services avec effet lumière au survol |
| 📅 Agenda | 6 événements avec date, lieu et badge catégorie |
| 💡 Bons plans | 6 catégories : transport, logement, resto, tech, culture, sport |
| 💬 Témoignages | 3 avis étudiants + FAQ accordéon |
| 📬 Contact | Formulaire → `mailto:marcdmr79@gmail.com` |

### Dashboard (après connexion)
| Fonctionnalité | Description |
|---|---|
| 🔐 Authentification | Google OAuth, Microsoft MSAL, ou email/mot de passe |
| 🏠 Accueil | Stats personnelles, feed actualités, météo Paris, compte à rebours |
| 💬 Chat de promo | Messagerie temps réel Firebase, verrou par promo, réactions emoji |
| 🤖 Assistant IA | API Claude (Anthropic) + fallback base de connaissances locale |
| 📅 Événements | Cartes avec photos, inscription en un clic |
| 🧠 Quiz | 10 questions tech + vie étudiante, score et explications |
| 👤 Profil | 5 avatars par défaut + upload photo, thèmes, bio |
| 🔔 Notifications | Centre de notifications avec badge |

---

## 🚀 Déploiement rapide (GitHub Pages)

### 1. Cloner le dépôt
```bash
git clone https://github.com/ton-username/iris-paris-hub.git
cd iris-paris-hub
```

### 2. Ouvrir localement
```bash
# Aucun serveur requis — ouvrir directement dans le navigateur
open index.html
# ou sur Linux :
xdg-open index.html
```

### 3. Déployer sur GitHub Pages
1. Va dans **Settings → Pages** de ton dépôt GitHub
2. Source : `Deploy from a branch`
3. Branch : `main` / dossier : `/ (root)`
4. Ton site sera disponible sur :  
   `https://ton-username.github.io/iris-paris-hub`

---

## ⚙️ Configuration des services externes

Le site fonctionne **immédiatement sans aucune clé** en mode dégradé.  
Pour activer toutes les fonctionnalités, remplis les constantes dans la section `CFG` en haut de `index.html` :

```javascript
const CFG = {
  GOOGLE_CLIENT_ID: "TON_ID.apps.googleusercontent.com",  // Google Cloud Console
  MSFT_CLIENT_ID:   "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX", // Azure Portal
  FB_API_KEY:       "...",         // Firebase Console
  FB_AUTH_DOMAIN:   "...",
  FB_DB_URL:        "...",
  FB_PROJECT_ID:    "...",
  FB_APP_ID:        "...",
  CONTACT_EMAIL:    "marcdmr79@gmail.com",
};
```

> 📖 Voir **[SETUP.md](./SETUP.md)** pour le guide détaillé étape par étape.

### Ce qui fonctionne sans configuration
| Service | Sans clés | Avec clés |
|---|---|---|
| Inscription / connexion email | ✅ localStorage | ✅ localStorage |
| Connexion Google | ⚠️ Bouton affiché (popup Google bloquée) | ✅ Popup Google réelle |
| Connexion Microsoft | ⚠️ Bouton affiché (popup MSAL bloquée) | ✅ Popup Microsoft réelle |
| Chat de promo | ✅ localStorage (même navigateur) | ✅ Firebase Realtime DB (tous membres) |
| Assistant IA | ✅ Base de connaissances locale | ✅ API Claude Anthropic |
| Météo Paris | ✅ API Open-Meteo (gratuit, sans clé) | ✅ idem |
| Avatars | ✅ DiceBear (gratuit, sans clé) | ✅ idem |

---

## 🧩 Architecture technique

Le projet est volontairement conçu en **fichier unique** (`index.html`) pour :
- Faciliter le déploiement sur GitHub Pages sans build tool
- Respecter les contraintes du BTS SIO (HTML / CSS / JS purs)
- Permettre une lecture et une modification directe du code

### Organisation interne du code JavaScript (20 sections commentées)

```
1.  Constantes & données statiques   (avatars, promos, quiz, KB IA)
2.  Base de données localStorage     (users, session, chat, prefs)
3.  État global                      (currentUser, activePromo...)
4.  Loader de démarrage              (barre de progression animée)
5.  Curseur personnalisé             (point doré + anneau)
6.  Navigation & scroll              (IntersectionObserver reveal)
7.  Utilitaires                      (glowCard, toast, esc HTML)
8.  Thèmes                           (sombre/clair, 3 accents)
9.  Formulaire de contact            (mailto: construction)
10. Authentification                 (modal, OAuth, email)
11. Dashboard                        (ouverture, panels, stats)
12. Avatars                          (sélection, upload, base64)
13. Chat de promo                    (verrou promo, Firebase/local)
14. Assistant IA                     (API Claude + fallback KB)
15. Événements                       (inscription, compteur)
16. Quiz étudiant                    (10 questions, score)
17. Météo Paris                      (Open-Meteo API)
18. Compte à rebours                 (setInterval 1s)
19. Profil                           (sauvegarde préférences)
20. Auto-login                       (session persistante)
```

### Technologies utilisées

| Catégorie | Technologie | Usage |
|---|---|---|
| Structure | HTML5 sémantique | Pages et composants |
| Style | CSS3 (variables, grid, animations) | Design système |
| Logique | Vanilla JavaScript ES6+ | Toute l'interactivité |
| Auth | Google GSI + Microsoft MSAL | Connexion OAuth réelle |
| Base de données | Firebase Realtime Database | Chat temps réel |
| IA | Anthropic Claude API | Assistant campus |
| Météo | Open-Meteo API | Météo Paris gratuite |
| Avatars | DiceBear API | Avatars par défaut |
| Polices | Google Fonts (Bebas Neue, DM Sans, Space Grotesk) | Typographie |
| Hébergement | GitHub Pages | Déploiement gratuit |

---

## 🎨 Design System

### Palette couleurs (identité Iris Paris)
| Variable | Valeur | Rôle |
|---|---|---|
| `--bg` | `#080E1C` | Fond principal (bleu marine très foncé) |
| `--bg2` | `#0E1828` | Fond cartes et sidebar |
| `--bg3` | `#162035` | Fond inputs et champs |
| `--ac` | `#F5C842` | Couleur accent (or Iris) |
| `--acl` | `#FDE97A` | Accent clair (hover) |
| `--blue` | `#1A3A6B` | Bleu Iris profond |
| `--text` | `#DCE5F5` | Texte principal |
| `--muted` | `#6A7D9E` | Texte secondaire |

### Typographie
- **Bebas Neue** — Titres et éléments display (logo, sections)
- **Space Grotesk** — Titres de cartes et composants UI
- **DM Sans** — Corps de texte, formulaires, navigation

### Thèmes disponibles
- 🌙 **Sombre** (défaut) — Navy + or
- ☀️ **Clair** — Blanc + bleu + or
- 🖥️ **Système** — Suit les préférences OS

### Couleurs d'accent
- ⭐ **Or Iris** `#F5C842` (défaut)
- 🔵 **Bleu** `#378ADD`
- 🟢 **Teal** `#1D9E75`

---

## 📸 Captures d'écran

> Les captures sont disponibles dans `docs/wireframe-iris-paris.pdf`

| Page | Description |
|---|---|
| Landing page | Hero animé + photos campus + services |
| Modal auth | Connexion Google / Microsoft / email |
| Dashboard accueil | Stats + météo + compte à rebours |
| Chat de promo | Messagerie temps réel + réactions emoji |
| Assistant IA | Chatbot + base de connaissances |
| Quiz | 10 questions avec score et explications |
| Profil | Avatars + thèmes + paramètres |

---

## 🗺️ Wireframe

Le wireframe lo-fi complet (6 pages, style sketch professionnel) est disponible dans :

```
docs/wireframe-iris-paris.pdf
```

Il couvre toutes les pages et flux utilisateur :
- Page d'accueil publique
- Modal d'authentification
- Dashboard accueil (météo, stats, feed)
- Chat de promo (verrou, réactions)
- Assistant IA + Quiz
- Profil (avatars, thèmes)

---

## 📦 Livrables BTS SIO

Ce projet constitue un livrable complet pour le BTS SIO SLAM :

- [x] **Cahier des charges** → `docs/cahier-des-charges.md`
- [x] **Wireframes** → `docs/wireframe-iris-paris.pdf`
- [x] **Code source commenté** → `index.html` (20 sections)
- [x] **Site en ligne** → GitHub Pages
- [ ] **Présentation orale** → `docs/presentation.md` (à compléter)

---

## 👥 Équipe projet

| Nom | Rôle |
|---|---|
| Dowe Marc Rene | Développeur Front-End |
|  | Designer UI/UX |
| Dowe Marc | Chef de projet |

**Promotion :** BTS SIO SLAM — Iris Paris  
**Année scolaire :** 2024–2025

---

## 📄 Licence

Ce projet est sous licence **MIT**.  
Voir le fichier [LICENSE](./LICENSE) pour plus de détails.

---

## 🙏 Remerciements

- [IRIS Paris](https://ecoleiris.fr) — École et cadre pédagogique
- [MediaSchool](https://www.mediaschool.fr) — Groupe
- [Anthropic](https://www.anthropic.com) — API Claude pour l'assistant IA
- [Firebase](https://firebase.google.com) — Base de données temps réel
- [Open-Meteo](https://open-meteo.com) — API météo gratuite
- [DiceBear](https://www.dicebear.com) — Avatars par défaut
- [Unsplash](https://unsplash.com) — Photos libres de droits

---

<p align="center">
  Fait avec ❤️ par les étudiants BTS SIO SLAM d'Iris Paris
</p>
