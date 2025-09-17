# 📸 Screenshots - SWS RouterOs Template

Ce dossier contient les captures d'écran du template SWS RouterOs pour documentation et présentation.

## 📋 Liste des Captures Nécessaires

### Pages Principales
- [ ] `login.png` - Page de connexion principale (desktop)
- [ ] `login-mobile.png` - Page de connexion (mobile)
- [ ] `pricing.png` - Page de tarification (desktop)
- [ ] `pricing-mobile.png` - Page de tarification (mobile)
- [ ] `status.png` - Page de statut utilisateur
- [ ] `about.png` - Page d'informations

### Fonctionnalités
- [ ] `ticket-mode.png` - Mode connexion par ticket
- [ ] `account-mode.png` - Mode connexion par compte
- [ ] `error-handling.png` - Gestion d'erreurs
- [ ] `responsive-demo.png` - Démonstration responsive

### Thèmes et Variations
- [ ] `light-theme.png` - Thème clair
- [ ] `dark-theme.png` - Thème sombre (futur)
- [ ] `custom-branding.png` - Exemple de personnalisation

## 📱 Guidelines pour les Screenshots

### Dimensions Recommandées
- **Desktop** : 1920×1080px ou 1440×900px
- **Mobile** : 375×667px (iPhone) ou 360×640px (Android)
- **Tablet** : 768×1024px

### Format et Qualité
- Format : PNG (pour la transparence) ou JPG (pour la taille)
- Qualité : 90% pour JPG
- Compression : Optimisée pour le web

### Contenu
- Utilisez des données réalistes mais anonymisées
- Montrez l'interface dans un état propre et attractif
- Incluez différents états (normal, hover, focus)

## 🔧 Outils Recommandés

### Capture d'Écran
- **macOS** : Capture d'écran native (Cmd+Shift+4)
- **Windows** : Outil Capture d'écran ou Snipping Tool
- **Browser DevTools** : Pour les captures responsive précises
- **Extensions** : Full Page Screen Capture, Awesome Screenshot

### Édition d'Images
- **Gratuits** : GIMP, Paint.NET, Canva
- **Payants** : Photoshop, Sketch, Figma
- **En ligne** : Photopea, Remove.bg

### Optimisation
- **TinyPNG** : Compression PNG
- **ImageOptim** : Optimisation macOS
- **Squoosh** : Outil Google d'optimisation

## 📐 Template pour Screenshots

### Desktop (1920×1080)
```
┌─────────────────────────────────────┐
│              Header/Nav             │
├─────────────────────────────────────┤
│                                     │
│         Contenu Principal           │
│                                     │
├─────────────────────────────────────┤
│              Footer                 │
└─────────────────────────────────────┘
```

### Mobile (375×667)
```
┌───────────────┐
│    Header     │
├───────────────┤
│               │
│   Contenu     │
│  Principal    │
│               │
│               │
├───────────────┤
│    Footer     │
└───────────────┘
```

## 🎨 Guide de Style pour Screenshots

### Cohérence Visuelle
- Utilisez les mêmes données de test dans toutes les captures
- Gardez le même niveau de zoom
- Alignez les éléments correctement

### Annotations
- Utilisez des flèches et textes pour expliquer les fonctionnalités
- Couleurs d'annotation : Rouge (#E74C3C) pour l'attention, Bleu (#3498DB) pour l'information

### Mise en Contexte
- Montrez l'interface dans un environnement réaliste
- Incluez la barre d'adresse du navigateur si pertinent
- Montrez les états interactifs (hover, active)

## 📝 Nommage des Fichiers

### Convention
```
[page]-[device]-[state].png

Exemples :
- login-desktop-default.png
- login-mobile-error.png
- pricing-tablet-hover.png
- status-desktop-connected.png
```

### États Possibles
- `default` : État normal
- `hover` : Survol d'élément
- `active` : Élément actif/sélectionné
- `error` : État d'erreur
- `loading` : État de chargement
- `empty` : État vide
- `success` : État de succès

## 🚀 Utilisation dans le README

### Exemple d'Intégration
```markdown
## 🖼️ Aperçu

### Interface Desktop
![Page de Connexion](screenshots/login-desktop-default.png)

### Interface Mobile
<img src="screenshots/login-mobile-default.png" alt="Mobile Login" width="300">

### Comparaison Responsive
| Desktop | Mobile |
|---------|--------|
| ![Desktop](screenshots/login-desktop-default.png) | ![Mobile](screenshots/login-mobile-default.png) |
```

## 📊 Checklist de Qualité

### Avant Publication
- [ ] Images optimisées (< 500KB chacune)
- [ ] Alt text descriptifs définis
- [ ] Cohérence visuelle vérifiée
- [ ] Données sensibles masquées
- [ ] Qualité et netteté vérifiées
- [ ] Responsive testé sur vrais appareils

### Maintenance
- [ ] Mise à jour après changements UI
- [ ] Vérification de la pertinence
- [ ] Suppression des captures obsolètes

---

**Note :** Les captures d'écran sont essentielles pour présenter le projet sur GitHub. Prenez le temps de créer des images de qualité qui mettent en valeur le travail accompli.

Pour contribuer des screenshots, suivez ce guide et soumettez une Pull Request avec vos images optimisées.