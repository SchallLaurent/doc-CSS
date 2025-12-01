# 🚀 On-Boarding

> Guides d'installation et de configuration pour préparer votre environnement de développement

## 📋 À propos

Ce dossier contient des guides complets pour installer et configurer les outils essentiels du développement web moderne. Chaque guide est conçu pour être suivi étape par étape, avec des solutions aux problèmes courants et des bonnes pratiques.

## 🎯 Objectifs

- **Rapidité** : Passer de zéro à un environnement fonctionnel en moins d'une heure
- **Complétude** : Tous les outils nécessaires pour un développement professionnel
- **Reproductibilité** : Guides testés et mis à jour régulièrement
- **Troubleshooting** : Solutions aux erreurs courantes incluses
- **Bonnes pratiques** : Configuration optimale dès le départ

## 🖥️ Plateformes supportées

### macOS

- [**Installation de Oh My Zsh**](./mac/install-zsh.md) - Terminal amélioré avec plugins et thèmes

### Windows _(à venir)_

- Installation de WSL2
- Configuration de Windows Terminal
- PowerShell personnalisé

## 📦 Guides disponibles

### 🍎 macOS

#### Terminal & Shell

- ✅ **[Oh My Zsh](./mac/install-zsh.md)**
  - Installation complète avec plugins
  - Configuration Powerlevel10k
  - Troubleshooting détaillé
  - Aliases et raccourcis essentiels

## 🎓 Ordre d'installation recommandé

### Pour macOS

```
1. Homebrew           (gestionnaire de paquets)
   ↓
2. Oh My Zsh          (terminal amélioré)
   ↓
3. Git + GitHub       (versionning)
   ↓
4. Node.js + NVM      (JavaScript runtime)
   ↓
5. VS Code            (éditeur de code)
   ↓
6. Docker Desktop     (containerisation)

```

### Pour Windows

```
1. WSL2               (environnement Linux)
   ↓
2. Windows Terminal   (terminal moderne)
   ↓
3. Git for Windows    (versionning)
   ↓
4. Node.js + nvm      (JavaScript runtime)
   ↓
5. VS Code            (éditeur de code)
   ↓
6. Docker Desktop     (containerisation)
```

## 📖 Structure des guides

Chaque guide suit cette structure standardisée :

```markdown
# Titre de l'outil

## À propos

- Description
- Avantages
- Prérequis

## Installation

- Étapes détaillées
- Code à copier-coller
- Explications

## Configuration

- Fichiers de config
- Personnalisation
- Variables d'environnement

## Résolution de problèmes

- Erreurs courantes
- Solutions testées

## Bonnes pratiques

- À faire / À éviter
- Astuces
- Optimisations

## Ressources

- Documentation officielle
- Liens utiles
```

## 🛠️ Stack de développement complète

Une fois tous les guides suivis, vous aurez un environnement comprenant :

### Essentiels

- ✅ **Terminal** : Oh My Zsh / PowerShell / Zsh
- 🔜 **Gestionnaire de paquets** : Homebrew / apt / Chocolatey
- 🔜 **Versionning** : Git + GitHub CLI
- 🔜 **Runtime** : Node.js + NVM
- 🔜 **Éditeur** : VS Code configuré
- 🔜 **Containerisation** : Docker + Docker Compose
