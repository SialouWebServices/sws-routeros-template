# Changelog - SWS RouterOs MikroTik Template

Toutes les modifications notables de ce projet seront documentées dans ce fichier.

Le format est basé sur [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/),
et ce projet adhère au [Semantic Versioning](https://semver.org/lang/fr/).

## [2.0.0] - 2024-01-15

### 🎉 Ajouté
- Interface utilisateur complètement redessinée avec design glassmorphism moderne
- Support complet pour l'authentification par tickets et comptes utilisateur
- Page de tarification dynamique avec forfaits personnalisables
- Design 100% responsive optimisé pour mobile, tablette et desktop
- Système de couleurs intelligent selon l'action (rouge=danger, vert=succès, etc.)
- Animations fluides et transitions CSS avancées
- Support des icônes Font Awesome avec tailles standardisées (25px)
- Page de contact intégrée avec liens sociaux
- Page d'informations et d'aide détaillée
- Gestion avancée des erreurs avec messages contextuels

### 🔄 Modifié
- Refonte complète de la structure HTML pour une meilleure sémantique
- Optimisation des styles CSS avec variables CSS personnalisées
- Amélioration de l'expérience utilisateur sur mobile
- Modernisation des formulaires avec validation côté client
- Mise à jour des scripts JavaScript pour plus de performance

### 🎨 Améliorations Visuelles
- Nouveau système de couleurs cohérent
- Typographie optimisée avec tailles préférées (30px instructions, 16px champs)
- Boutons modernes avec effets de survol
- Icônes unifiées à 25px selon les préférences utilisateur
- Fond d'écran moderne avec effet de flou

### 🔧 Technique
- Intégration complète avec l'authentification CHAP MikroTik
- Support des variables MikroTik natives
- Code JavaScript modulaire et maintenable
- CSS optimisé avec prefixes navigateur
- Structure de fichiers organisée et documentée

## [1.5.0] - 2023-12-01

### Ajouté
- Page de statut utilisateur
- Intégration basique avec système de paiement
- Support des forfaits multiples

### Modifié
- Amélioration de la compatibilité navigateur
- Optimisation des performances

## [1.0.0] - 2023-10-15

### Ajouté
- Version initiale du template
- Page de connexion basique
- Support MikroTik de base
- Design responsive initial

---

## Format des Versions

### Types de Changements
- **Ajouté** pour les nouvelles fonctionnalités
- **Modifié** pour les changements de fonctionnalités existantes
- **Déprécié** pour les fonctionnalités bientôt supprimées
- **Supprimé** pour les fonctionnalités supprimées
- **Corrigé** pour les corrections de bugs
- **Sécurité** pour les correctifs de sécurité

### Numérotation des Versions
- **MAJOR** : Changements incompatibles de l'API
- **MINOR** : Ajout de fonctionnalités compatible backwards
- **PATCH** : Corrections de bugs compatibles backwards

---

## Prochaines Versions

### [2.1.0] - Planifié pour Q2 2024
- [ ] Support multilingue complet (Anglais, Espagnol)
- [ ] Mode sombre automatique
- [ ] Intégration avec plus de systèmes de paiement
- [ ] Tableau de bord administrateur
- [ ] API pour statistiques temps réel

### [2.2.0] - Planifié pour Q3 2024
- [ ] PWA (Progressive Web App) support
- [ ] Notifications push
- [ ] Système de thèmes personnalisables
- [ ] Module de chat support client