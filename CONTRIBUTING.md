# Guide de Contribution - SWS RouterOs MikroTik Template

Merci de votre intérêt pour contribuer au projet SWS RouterOs ! Ce guide vous aidera à comprendre comment participer efficacement au développement.

## 🤝 Comment Contribuer

### Types de Contributions Acceptées

- 🐛 **Corrections de bugs**
- ✨ **Nouvelles fonctionnalités**
- 📚 **Amélioration de la documentation**
- 🌍 **Traductions**
- 🎨 **Améliorations UI/UX**
- ⚡ **Optimisations de performance**
- 🔒 **Améliorations de sécurité**

## 🚀 Démarrage Rapide

### 1. Fork et Clone

```bash
# Fork le projet sur GitHub, puis :
git clone https://github.com/SialouWebServices/sws-routeros-template.git
cd sws-routeros-template
```

### 2. Configuration de l'Environnement

```bash
# Créez une branche pour votre fonctionnalité
git checkout -b feature/ma-nouvelle-fonctionnalite

# ou pour un bugfix
git checkout -b fix/correction-du-bug
```

### 3. Développement Local

Pour tester vos modifications localement :

```bash
# Avec Python
python -m http.server 8000

# Avec Node.js
npx serve .

# Avec PHP
php -S localhost:8000
```

Puis ouvrez http://localhost:8000 dans votre navigateur.

## 📋 Guidelines de Développement

### Standards de Code

#### HTML
- Utilisez l'indentation de 2 espaces
- Toujours fermer les balises
- Utilisez des attributs `alt` pour les images
- Structure sémantique HTML5

```html
<!-- Bon -->
<div class="login-box">
  <img src="images/logo.png" alt="Logo de l'entreprise">
  <form class="modern-form">
    <!-- contenu -->
  </form>
</div>

<!-- Évitez -->
<div class="login-box"><img src="images/logo.png"><form class="modern-form"><!-- contenu --></form></div>
```

#### CSS
- Utilisez les variables CSS pour la cohérence
- Préfixez les classes spécifiques au projet
- Mobile-first approche pour le responsive

```css
/* Bon */
:root {
  --primary-color: #5DADE2;
  --icon-size: 25px;
}

.login-box {
  background: var(--primary-color);
}

.action-btn i {
  font-size: var(--icon-size) !important;
}

/* Mobile first */
@media (min-width: 768px) {
  .login-box {
    max-width: 450px;
  }
}
```

#### JavaScript
- Utilisez des noms de fonctions descriptifs
- Commentez les parties complexes
- Gérez les erreurs appropriément

```javascript
// Bon
function authenticateUser(credentials) {
  try {
    // Logique d'authentification
    return processAuthentication(credentials);
  } catch (error) {
    console.error('Erreur d\'authentification:', error);
    showErrorMessage('Échec de la connexion');
  }
}

// Évitez
function auth(c) {
  return processAuth(c);
}
```

### Conformité aux Préférences Utilisateur

Respectez impérativement ces préférences (stockées dans la mémoire utilisateur) :

- **Icônes** : Taille uniforme de 25px
- **Image de marque (brand.png)** : 120×80px (desktop), 100×65px (mobile)
- **Texte d'instruction** : Taille de 30px
- **Champs de saisie** : Taille de 16px
- **Couleurs des boutons** : Rouge (danger), Bleu (info), Vert (succès), Orange (test/status), Violet (premium)

## 🧪 Tests

### Tests Requis

Avant de soumettre une PR, testez sur :

- **Navigateurs** : Chrome, Firefox, Safari, Edge
- **Appareils** : Mobile, Tablette, Desktop
- **Résolutions** : 320px, 768px, 1200px minimum
- **MikroTik** : Si possible, testez sur un vrai routeur

### Checklist de Test

- [ ] Interface responsive sur tous les écrans
- [ ] Animations fluides sans lag
- [ ] Formulaires fonctionnels
- [ ] Boutons et liens actifs
- [ ] Images et ressources chargées
- [ ] Compatibilité avec variables MikroTik
- [ ] Performance acceptable (< 3s de chargement)

## 📝 Process de Soumission

### 1. Préparation

```bash
# Synchronisez avec la branche principale
git fetch upstream
git checkout main
git merge upstream/main

# Rebasez votre branche
git checkout feature/ma-fonctionnalite
git rebase main
```

### 2. Commit

Utilisez des messages de commit descriptifs :

```bash
# Format recommandé
git commit -m "feat: ajoute support pour thème sombre

- Implémente le mode sombre automatique
- Ajoute toggle pour changer de thème
- Respecte les préférences système
- Compatible avec tous les navigateurs

Fixes #123"
```

### Types de Commit

- `feat:` Nouvelle fonctionnalité
- `fix:` Correction de bug
- `docs:` Modification de documentation
- `style:` Modification de style/formatage
- `refactor:` Refactoring de code
- `test:` Ajout/modification de tests
- `chore:` Maintenance du projet

### 3. Pull Request

#### Template de PR

```markdown
## Description
Brève description des changements apportés.

## Type de Changement
- [ ] Bug fix (correction qui résout un problème)
- [ ] New feature (ajout de fonctionnalité)
- [ ] Breaking change (changement qui casse la compatibilité)
- [ ] Documentation update (mise à jour de documentation)

## Tests Effectués
- [ ] Tests navigateurs (Chrome, Firefox, Safari, Edge)
- [ ] Tests responsive (Mobile, Tablette, Desktop)
- [ ] Tests fonctionnels
- [ ] Tests avec MikroTik (si applicable)

## Captures d'Écran
<!-- Ajoutez des captures avant/après si applicable -->

## Checklist
- [ ] Mon code suit les guidelines du projet
- [ ] J'ai effectué une revue de mon propre code
- [ ] J'ai commenté les parties complexes
- [ ] Mes changements ne génèrent pas de nouveaux warnings
- [ ] J'ai testé sur différents navigateurs et appareils
```

## 🌍 Traductions

### Ajouter une Nouvelle Langue

1. Dupliquez `login.html` → `login-[code_langue].html`
2. Traduisez tous les textes visibles
3. Mettez à jour la navigation
4. Testez l'affichage sur différents écrans

### Langues Prioritaires

- Anglais (en cours)
- Espagnol (planifié)
- Arabe (demandé)

## 🐛 Signalement de Bugs

### Template d'Issue

```markdown
**Description du Bug**
Description claire et concise du problème.

**Reproduction**
Étapes pour reproduire le comportement :
1. Allez à '...'
2. Cliquez sur '....'
3. Scrollez jusqu'à '....'
4. Observez l'erreur

**Comportement Attendu**
Description claire de ce qui devrait se passer.

**Captures d'Écran**
Si applicable, ajoutez des captures d'écran pour aider à expliquer le problème.

**Environnement (complétez les informations suivantes) :**
- OS: [ex. iOS]
- Navigateur [ex. chrome, safari]
- Version [ex. 22]
- RouterOS Version [ex. 6.47.10]
- Type d'appareil [ex. iPhone6, Desktop]

**Contexte Additionnel**
Ajoutez tout autre contexte sur le problème ici.
```

## ✨ Fonctionnalités Demandées

### Roadmap Communautaire

Votez et proposez des fonctionnalités via les Issues GitHub avec le label `enhancement`.

#### Fonctionnalités Populaires

1. **Mode Sombre** (en cours)
2. **Support PWA** (planifié)
3. **Dashboard Admin** (demandé)
4. **Multi-thèmes** (étudié)

## 📞 Support

### Canaux de Communication

- **Issues GitHub** : Pour bugs et fonctionnalités
- **Discussions GitHub** : Pour questions générales
- **Site Web** : [SW Service](https://swservice.carrd.co/)

### Temps de Réponse

- Issues critiques : 24-48h
- Nouvelles fonctionnalités : 1-2 semaines
- Questions générales : 3-5 jours

## 🎖️ Reconnaissance

### Contributeurs

Tous les contributeurs seront mentionnés dans :
- README.md
- Page About du template
- CONTRIBUTORS.md (à venir)

### Niveaux de Contribution

- **Bronze** : 1-5 commits acceptés
- **Silver** : 6-15 commits acceptés
- **Gold** : 16+ commits acceptés
- **Core** : Contributeurs réguliers avec accès maintainer

---

**Merci de contribuer à SWS RouterOs ! 🚀**

Chaque contribution, petite ou grande, aide à améliorer l'expérience de milliers d'utilisateurs de hotspots WiFi à travers le monde.