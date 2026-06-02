# Script court pour l'exposé - Iris Paris Hub

## Répartition conseillée

**Personne maquette / design**
- Présente le besoin utilisateur, l'identité visuelle, la page publique et le parcours.
- Explique les choix : bleu nuit, accent or, images campus, cartes, sidebar, responsive.

**Personne code**
- Présente l'organisation des fichiers, le JavaScript, le stockage local, l'authentification, le chat, l'IA et le quiz.
- Explique aussi les limites techniques et les améliorations possibles.

## Plan oral simple

1. **Introduction**
   - "Notre projet s'appelle Iris Paris Hub. C'est un espace étudiant pour IRIS Paris."
   - "Le but est de centraliser les informations utiles : services, événements, bons plans, chat de promo, assistant IA et profil."

2. **Utilité**
   - "Le problème, c'est que les informations étudiantes peuvent être dispersées."
   - "Notre solution est une plateforme unique, claire et rapide à utiliser."
   - "Elle aide l'étudiant à s'intégrer, à trouver les bonnes informations et à échanger avec sa promo."

3. **Design**
   - "On a choisi une ambiance bleu nuit et or pour rappeler l'identité IRIS et le domaine numérique."
   - "La page publique fonctionne comme une vitrine : hero, photos, services, événements, bons plans, témoignages, FAQ et contact."
   - "Le dashboard est plus pratique : sidebar fixe, statistiques, widgets et accès rapide aux fonctionnalités."

4. **Code**
   - "Le projet est en HTML, CSS et JavaScript pur, donc il peut s'ouvrir directement dans un navigateur."
   - "`index.html` contient la structure, la configuration et le JavaScript principal."
   - "`style.css` contient les variables CSS, les thèmes, les composants et le responsive."
   - "Le dossier `img` contient les images utilisées pour donner une identité visuelle au site."

5. **Fonctionnalités techniques**
   - "L'objet `DB` utilise `localStorage` pour sauvegarder utilisateurs, session et préférences."
   - "Les fonctions `openAuth`, `emailRegister`, `emailLogin` et `openDash` gèrent la connexion et l'ouverture du dashboard."
   - "Le chat fonctionne avec Firebase si c'est configuré, sinon il utilise un mode local de secours."
   - "La fonction `esc()` protège l'affichage des messages en empêchant l'injection de HTML."
   - "L'assistant IA a une base de connaissances locale et peut utiliser une API externe si une clé est configurée."
   - "Le quiz utilise un tableau de questions avec score, réponse correcte et explication."

6. **Conclusion**
   - "Iris Paris Hub est plus qu'une simple page web : c'est une application interactive pour la vie étudiante."
   - "Le projet est déjà démontrable, mais on pourrait l'améliorer avec un backend sécurisé, une vraie administration des événements et des notifications dynamiques."

## Questions possibles

**Pourquoi utiliser `localStorage` ?**
Pour garder une session et des préférences côté navigateur sans serveur. C'est adapté à un prototype scolaire, mais pas suffisant pour une vraie production sécurisée.

**Pourquoi Firebase ?**
Firebase Realtime Database permet de synchroniser les messages du chat en temps réel entre plusieurs utilisateurs.

**Pourquoi un fallback local ?**
Si Firebase ou une clé API n'est pas disponible, le site continue de fonctionner en mode dégradé. C'est plus fiable pour une démonstration.

**Quel est le rôle du CSS ?**
Le CSS crée le design system : couleurs, thèmes, cartes, grilles, animations, responsive et dashboard.

**Quelle amélioration serait prioritaire ?**
Ajouter un vrai backend d'authentification pour sécuriser les comptes et éviter de stocker des mots de passe dans le navigateur.
