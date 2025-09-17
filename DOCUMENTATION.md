# 📖 Documentation - SWS RouterOs MikroTik Template

Guide complet d'installation, configuration et personnalisation du template SWS RouterOs pour portails captifs MikroTik.

## Table des Matières

1. [Installation](#-installation)
2. [Configuration MikroTik](#-configuration-mikrotik)
3. [Personnalisation](#-personnalisation)
4. [Variables MikroTik](#-variables-mikrotik)
5. [Structure des Fichiers](#-structure-des-fichiers)
6. [Résolution de Problèmes](#-résolution-de-problèmes)
7. [FAQ](#-faq)
8. [Support](#-support)

## 🚀 Installation

### Prérequis

- **RouterOS** : Version 6.40 ou supérieure (recommandé 7.x)
- **Accès administrateur** au routeur MikroTik
- **Espace de stockage** : Minimum 10MB disponible
- **Navigateur moderne** pour l'interface utilisateur

### Méthode 1 : Installation via Winbox

1. **Téléchargement**
   ```bash
   git clone https://github.com/SialouWebServices/sws-routeros-template.git
   cd sws-routeros-template
   ```

2. **Upload des fichiers**
   - Ouvrez Winbox et connectez-vous à votre routeur
   - Allez dans **Files**
   - Créez un dossier `hotspot` (si n'existe pas déjà)
   - Uploadez tous les fichiers en respectant la structure

3. **Configuration du profil Hotspot**
   - **IP > Hotspot > Server Profiles**
   - Sélectionnez votre profil (généralement `hsprof1`)
   - **HTML Directory** : `hotspot`
   - **Login By** : `cookie,http-chap,http-pap`

### Méthode 2 : Installation via Terminal

```bash
# Connexion SSH au routeur
ssh admin@192.168.1.1

# Upload via SCP ou FTP (exemple avec SCP)
scp -r * admin@192.168.1.1:/

# Configuration via terminal
/ip hotspot profile set hsprof1 html-directory=hotspot login-by=cookie,http-chap
```

### Méthode 3 : Installation via WebFig

1. Ouvrez votre navigateur : `http://192.168.1.1`
2. Connectez-vous avec vos identifiants administrateur
3. **Files** → Upload des fichiers du template
4. **IP** → **Hotspot** → **Server Profiles**
5. Configurez le répertoire HTML

## ⚙️ Configuration MikroTik

### Configuration Hotspot de Base

```bash
# Création d'un profil utilisateur pour les tickets
/ip hotspot user profile
add name="ticket-30min" rate-limit="1M/1M" session-timeout="00:30:00" shared-users=1

# Création d'un utilisateur test
/ip hotspot user
add name="test-ticket" password="12345" profile="ticket-30min"

# Configuration du serveur Hotspot
/ip hotspot
setup
# Suivez l'assistant de configuration

# Configuration avancée du profil
/ip hotspot profile
set hsprof1 \
  html-directory=hotspot \
  login-by=cookie,http-chap \
  use-radius=no \
  trial-uptime-limit=00:30:00 \
  trial-user-profile=default
```

### Configuration RADIUS (Optionnel)

```bash
# Configuration du client RADIUS
/radius
add address=192.168.1.100 secret="radius-secret" service=hotspot

# Activation RADIUS dans le profil Hotspot
/ip hotspot profile
set hsprof1 use-radius=yes
```

### Configuration des Réseaux

```bash
# Configuration de l'interface bridge
/interface bridge
add name=bridge-hotspot

# Ajout des interfaces au bridge
/interface bridge port
add bridge=bridge-hotspot interface=wlan1
add bridge=bridge-hotspot interface=ether2

# Configuration IP
/ip address
add address=192.168.10.1/24 interface=bridge-hotspot

# Configuration DHCP
/ip dhcp-server network
add address=192.168.10.0/24 gateway=192.168.10.1 dns-server=8.8.8.8,8.8.4.4

/ip dhcp-server
add interface=bridge-hotspot address-pool=hotspot-pool name=hotspot-dhcp
```

## 🎨 Personnalisation

### Modification du Logo et Branding

#### 1. Logo Principal

```html
<!-- Dans login.html, remplacez : -->
<img src="images/brand.png" alt="Logo de marque" class="brand-image">
```

**Spécifications recommandées :**
- Format : PNG avec transparence
- Taille Desktop : 120×80px
- Taille Mobile : 100×65px
- Poids : < 50KB

#### 2. Personnalisation des Couleurs

Modifiez les variables CSS dans `css/modern-ui.css` :

```css
:root {
  /* Couleurs principales */
  --primary-blue: #5DADE2;        /* Bleu principal */
  --primary-green: #58D68D;       /* Vert de succès */
  --primary-orange: #FF9500;      /* Orange d'accent */
  
  /* Tailles préférées */
  --instruction-size: 30px;       /* Taille du texte d'instruction */
  --input-size: 16px;             /* Taille des champs de saisie */
  --icon-size: 25px;              /* Taille des icônes */
  
  /* Couleurs des boutons selon l'action */
  --color-danger: #E74C3C;        /* Rouge - Actions critiques */
  --color-info: #3498DB;          /* Bleu - Informations */
  --color-success: #27AE60;       /* Vert - Actions positives */
  --color-warning: #F39C12;       /* Orange - Tests/Status */
  --color-premium: #8E44AD;       /* Violet - Services premium */
}
```

#### 3. Modification du Fond d'Écran

Remplacez `images/bg.jpg` par votre image :
- Résolution recommandée : 1920×1080px minimum
- Format : JPG optimisé
- Poids : < 200KB pour des performances optimales

### Personnalisation du Contenu

#### 1. Messages d'Accueil

Dans `login.html`, modifiez :

```html
<p class="instruction-text">
  Entrez vos informations de connexion !!
</p>
```

#### 2. Forfaits et Tarification

Dans `package.html`, personnalisez chaque forfait :

```html
<div class="pricing_title" data-package="30min">30 Minutes</div>
<div class="pricing_price">100 CFA<div>30 Minutes</div></div>

<!-- Lien de paiement -->
<a href="https://votre-systeme-paiement.com/forfait/30min">
  <i class="fa fa-shopping-cart"></i>Achetez
</a>
```

#### 3. Informations de Contact

Dans `contact.html` et les liens sociaux :

```html
<!-- WhatsApp -->
<a href="https://wa.me/+2250747190514" target="_blank">
  <i class="fa fa-whatsapp"></i> Contactez nous
</a>

<!-- Site web -->
<a href="https://swservice.carrd.co/" target="_blank">
  SW Service
</a>
```

### Personnalisation Avancée

#### 1. Ajout de Nouvelles Pages

Créez un nouveau fichier HTML basé sur la structure existante :

```html
<!DOCTYPE html>
<html>
<head>
  <title>$(identity) - Ma Nouvelle Page</title>
  <link rel="stylesheet" type="text/css" href="css/modern-ui.css">
</head>
<body>
  <div class="body">
    <div class="login-box">
      <!-- Votre contenu -->
    </div>
  </div>
</body>
</html>
```

#### 2. Modification des Animations

Dans `css/modern-ui.css`, personnalisez les animations :

```css
@keyframes fadeInUp {
  0% {
    opacity: 0;
    transform: translateY(30px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

/* Appliquez à vos éléments */
.mon-element {
  animation: fadeInUp 0.8s ease-out;
}
```

## 🔧 Variables MikroTik

### Variables de Base

| Variable | Description | Exemple |
|----------|-------------|---------|
| `$(identity)` | Nom du routeur | "HotSpot-Router" |
| `$(link-login-only)` | URL de connexion | "/login" |
| `$(link-orig)` | URL de destination | "http://google.com" |
| `$(link-orig-esc)` | URL échappée | "http%3A//google.com" |
| `$(mac)` | Adresse MAC client | "AA:BB:CC:DD:EE:FF" |
| `$(mac-esc)` | MAC échappée | "AA%3ABB%3ACC%3ADD%3AEE%3AFF" |
| `$(ip)` | IP du client | "192.168.1.100" |
| `$(username)` | Nom d'utilisateur | "user123" |
| `$(uptime)` | Temps de connexion | "00:15:32" |
| `$(error)` | Message d'erreur | "invalid username or password" |

### Variables de Session

| Variable | Description | Usage |
|----------|-------------|-------|
| `$(bytes-in-nice)` | Données reçues | "15.2MB" |
| `$(bytes-out-nice)` | Données envoyées | "8.7MB" |
| `$(uptime-secs)` | Temps en secondes | "1856" |
| `$(refresh-timeout)` | Timeout de rafraîchissement | "300" |
| `$(session-time-left)` | Temps restant | "01:15:30" |

### Variables Conditionnelles

```html
<!-- Affichage conditionnel selon le statut -->
$(if login-by)
  <!-- Utilisateur connecté -->
  <p>Bienvenue $(username) !</p>
  <p>Temps de connexion : $(uptime)</p>
$(else)
  <!-- Utilisateur non connecté -->
  <form method="post" action="$(link-login-only)">
    <!-- Formulaire de connexion -->
  </form>
$(endif)

<!-- Gestion des erreurs -->
$(if error)
  <div class="error-message">
    Erreur : $(error)
  </div>
$(endif)

<!-- Support du mode trial -->
$(if trial == 'yes')
  <a href="$(link-login-only)?dst=$(link-orig-esc)&username=T-$(mac-esc)">
    Essai Gratuit
  </a>
$(endif)
```

## 📁 Structure des Fichiers

```
hotspot/
├── 📄 login.html              # Page principale de connexion
├── 📄 alogin.html             # Page de connexion après authentification
├── 📄 status.html             # Page de statut utilisateur
├── 📄 logout.html             # Page de déconnexion
├── 📄 error.html              # Page d'erreur générique
├── 📄 expired.html            # Page d'expiration de session
├── 📄 package.html            # Page de tarification
├── 📄 about.html              # Page d'informations
├── 📄 contact.html            # Page de contact
├── 📄 redirect.html           # Page de redirection
├── 📄 radvert.html            # Page de publicité
├── 📄 rlogin.html             # Page de connexion RADIUS
├── 📁 css/                    # Feuilles de style
│   ├── modern-ui.css          # Styles principaux
│   ├── pricing-buttons.css    # Styles des boutons de tarification
│   ├── bootstrap.min.css      # Framework Bootstrap
│   ├── main.css               # Styles complémentaires
│   ├── util.css               # Utilitaires CSS
│   ├── extras.css             # Styles supplémentaires
│   └── responsive.css         # Styles responsive
├── 📁 js/                     # Scripts JavaScript
│   ├── main.js                # Scripts principaux
│   ├── custom.js              # Scripts personnalisés
│   ├── jquery.min.js          # Bibliothèque jQuery
│   ├── bootstrap.min.js       # Scripts Bootstrap
│   └── config.js              # Configuration JavaScript
├── 📁 images/                 # Images et ressources
│   ├── bg.jpg                 # Image de fond principale
│   ├── brand.png              # Logo de marque
│   ├── logo.png               # Logo principal
│   ├── header.png             # Image d'en-tête
│   ├── loading.gif            # Animation de chargement
│   ├── mikrotik.png           # Logo MikroTik
│   └── icons/                 # Icônes diverses
├── 📁 fonts/                  # Polices de caractères
│   └── font-awesome-4.7.0/    # Icônes Font Awesome
├── 📁 assets/                 # Ressources JavaScript
│   ├── md5.js                 # Bibliothèque de hachage MD5
│   └── config.js              # Configuration des assets
└── 📁 reload/                 # Pages de rechargement
    ├── quota.html             # Page de quota
    ├── session.html           # Page de session
    └── uptime.html            # Page de temps de connexion
```

### Rôles des Fichiers Principaux

#### Pages de Connexion
- **`login.html`** : Page principale avec formulaire moderne
- **`alogin.html`** : Page simplifiée pour authentification rapide
- **`rlogin.html`** : Page spécifique pour RADIUS

#### Pages de Statut
- **`status.html`** : Informations de session utilisateur
- **`logout.html`** : Confirmation de déconnexion
- **`expired.html`** : Notification d'expiration

#### Pages Informatives
- **`package.html`** : Tarifs et forfaits disponibles
- **`about.html`** : Informations sur le service
- **`contact.html`** : Coordonnées et support

#### Utilitaires
- **`error.html`** : Gestion d'erreurs génériques
- **`redirect.html`** : Redirection après connexion
- **`radvert.html`** : Affichage de publicités

## 🔍 Résolution de Problèmes

### Problèmes Courants

#### 1. Pages ne s'affichent pas correctement

**Symptômes :** Interface cassée, styles manquants

**Solutions :**
```bash
# Vérifiez l'arborescence des fichiers
/file print where name~"hotspot"

# Vérifiez la configuration du profil
/ip hotspot profile print detail

# Corrigez le répertoire HTML
/ip hotspot profile set hsprof1 html-directory=hotspot
```

#### 2. Authentification ne fonctionne pas

**Symptômes :** Erreur "invalid username or password"

**Solutions :**
```bash
# Vérifiez les utilisateurs
/ip hotspot user print

# Vérifiez l'authentification CHAP
/ip hotspot profile print detail

# Activez les méthodes d'authentification
/ip hotspot profile set hsprof1 login-by=cookie,http-chap,http-pap
```

#### 3. Images ne se chargent pas

**Symptômes :** Images brisées, fond manquant

**Solutions :**
- Vérifiez que les images sont dans le dossier `images/`
- Vérifiez les permissions des fichiers
- Réduisez la taille des images si nécessaire

#### 4. Responsive ne fonctionne pas sur mobile

**Symptômes :** Interface non adaptée au mobile

**Solutions :**
```html
<!-- Vérifiez la balise viewport -->
<meta name="viewport" content="width=device-width, initial-scale=1">
```

```css
/* Vérifiez les media queries */
@media (max-width: 768px) {
  .login-box {
    margin: 10px;
    padding: 20px;
  }
}
```

### Debugging

#### 1. Debug via Browser

- **F12** → Console pour les erreurs JavaScript
- **Network** pour vérifier le chargement des ressources
- **Elements** pour inspecter le DOM

#### 2. Debug MikroTik

```bash
# Logs du serveur Hotspot
/log print where topics~"hotspot"

# Status des utilisateurs connectés
/ip hotspot active print

# Statistiques de trafic
/ip hotspot user print stats
```

#### 3. Test de Variables

Créez une page de test `test.html` :

```html
<!DOCTYPE html>
<html>
<head><title>Test Variables</title></head>
<body>
<h1>Variables MikroTik</h1>
<ul>
  <li>Identity: $(identity)</li>
  <li>IP: $(ip)</li>
  <li>MAC: $(mac)</li>
  <li>Username: $(username)</li>
  <li>Error: $(error)</li>
  <li>Login-by: $(login-by)</li>
</ul>
</body>
</html>
```

## ❓ FAQ

### Questions Générales

**Q: Le template fonctionne-t-il avec tous les modèles MikroTik ?**
R: Oui, compatible avec tous les routeurs MikroTik supportant la fonctionnalité Hotspot (RouterOS 6.x+).

**Q: Puis-je modifier les couleurs et le design ?**
R: Absolument ! Modifiez les variables CSS dans `css/modern-ui.css` pour personnaliser l'apparence.

**Q: Le template est-il gratuit ?**
R: Oui, sous licence MIT. Vous pouvez l'utiliser, le modifier et le redistribuer librement.

### Questions Techniques

**Q: Comment ajouter de nouveaux forfaits ?**
R: Éditez `package.html` et dupliquez une section de forfait existante avec vos nouveaux prix.

**Q: Comment intégrer un système de paiement ?**
R: Modifiez les liens dans `package.html` pour pointer vers votre passerelle de paiement.

**Q: Le template supporte-t-il HTTPS ?**
R: Oui, mais vous devez configurer le certificat SSL sur votre routeur MikroTik.

### Problèmes de Performance

**Q: Le chargement est lent, que faire ?**
R: 
- Optimisez les images (compression, formats WebP)
- Minifiez les fichiers CSS/JS
- Utilisez un CDN pour les ressources externes

**Q: Comment réduire l'utilisation de la bande passante ?**
R:
- Utilisez des images optimisées
- Activez la compression GZIP sur MikroTik
- Cachez les ressources statiques

## 📞 Support

### Support Communautaire

- **GitHub Issues** : [Signaler un bug](https://github.com/SialouWebServices/sws-routeros-template/issues)
- **GitHub Discussions** : [Poser une question](https://github.com/SialouWebServices/sws-routeros-template/discussions)
- **Wiki** : Documentation complète

### Support Commercial

Pour un support prioritaire et des personnalisations avancées :

- **Site Web** : [SW Service](https://swservice.carrd.co/)
- **Email** : contact@swservice.com
- **WhatsApp Business** : +225 07 47 19 05 14

### Formation et Consulting

Services disponibles :
- Formation MikroTik Hotspot
- Personnalisation avancée du template  
- Intégration avec systèmes de facturation
- Optimisation de performance
- Support technique dédié

---

**Développé avec ❤️ par SW Service**

Cette documentation est maintenue par la communauté. N'hésitez pas à contribuer en proposant des améliorations !