# 🚀 Déploiement sur GitHub Pages

Cette documentation utilise Docsify avec CDN directement, prête pour GitHub Pages.

## 📋 Prérequis

- Un repository GitHub
- GitHub Pages activé

## ⚙️ Configuration GitHub Pages

1. **Activez GitHub Pages** dans les paramètres de votre repository :
   - Allez dans `Settings` > `Pages`
   - Sous `Source`, sélectionnez la branche `main` (ou `master`)
   - Sélectionnez le dossier `/` (root)
   - Cliquez sur `Save`

2. **Attendez quelques minutes** pour que GitHub déploie votre site

3. **Votre documentation sera accessible** sur :
   ```
   https://[votre-username].github.io/[nom-du-repo]/
   ```

## 📁 Fichiers Requis

Les fichiers suivants sont nécessaires pour que Docsify fonctionne sur GitHub Pages :

- ✅ `index.html` - Point d'entrée avec configuration Docsify
- ✅ `_sidebar.md` - Navigation latérale
- ✅ `README.md` - Page d'accueil
- ✅ `.nojekyll` - Désactive Jekyll (important !)

## 🔧 Structure Recommandée

```
votre-repo/
├── index.html          # Point d'entrée Docsify
├── _sidebar.md         # Navigation
├── README.md           # Page d'accueil
├── .nojekyll           # Important pour GitHub Pages
├── api/
│   └── *.md
├── guide/
│   └── *.md
└── ... (autres dossiers)
```

## ✨ Fonctionnalités

- ✅ **Recherche** - Recherche dans toute la documentation
- ✅ **Navigation** - Sidebar automatique
- ✅ **Pagination** - Navigation entre pages
- ✅ **Copie de code** - Bouton pour copier les blocs de code
- ✅ **Zoom images** - Zoom sur les images
- ✅ **Coloration syntaxique** - Support de plusieurs langages
- ✅ **Responsive** - Fonctionne sur mobile et desktop

## 🔗 Domaine Personnalisé (Optionnel)

Si vous avez un fichier `CNAME`, GitHub Pages utilisera automatiquement votre domaine personnalisé.

## 📝 Notes

- Tous les fichiers sont servis via CDN (jsDelivr)
- Aucune installation locale nécessaire
- Fonctionne directement après activation de GitHub Pages
- Les modifications sont automatiquement déployées après chaque push

## 🐛 Dépannage

### La page ne se charge pas

1. Vérifiez que `.nojekyll` existe à la racine
2. Vérifiez que `index.html` est à la racine
3. Attendez quelques minutes après activation de GitHub Pages

### Les liens ne fonctionnent pas

- Assurez-vous que `relativePath: true` est dans la configuration
- Vérifiez que les chemins dans `_sidebar.md` sont corrects

### La recherche ne fonctionne pas

- Attendez quelques secondes après le chargement de la page
- Vérifiez la console du navigateur pour les erreurs

