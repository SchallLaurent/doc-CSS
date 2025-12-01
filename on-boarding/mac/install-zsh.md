# 🐚 Installation de Oh My Zsh sur macOS

> Guide complet pour installer et configurer Oh My Zsh avec plugins et thèmes personnalisés

## 📋 À propos

Oh My Zsh est un framework open-source pour gérer votre configuration Zsh. Il est livré avec des milliers de fonctions utiles, d'helpers, de plugins et de thèmes qui améliorent considérablement votre expérience en ligne de commande.

### ✨ Avantages de Oh My Zsh

- 🎨 **300+ thèmes** : Personnalisez l'apparence de votre terminal
- 🔌 **280+ plugins** : Git, Docker, Node, et bien plus
- ⚡ **Auto-complétion** : Suggestions intelligentes lors de la frappe
- 🎯 **Syntax Highlighting** : Coloration syntaxique des commandes
- 🔍 **Historique amélioré** : Navigation et recherche puissante
- 🛠️ **Aliases** : Raccourcis pour vos commandes fréquentes
- 📦 **Mises à jour faciles** : Système de mise à jour intégré

## 🎯 Prérequis

- macOS 10.15 (Catalina) ou supérieur
- Homebrew installé ([instructions](https://brew.sh/))
- Terminal par défaut ou iTerm2
- Zsh installé (inclus par défaut depuis macOS Catalina)

## 🚀 Installation

### Étape 1 : Installer Oh My Zsh

Oh My Zsh s'installe via un script automatisé qui configure tout pour vous.

```bash
# Installation avec curl
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

**Ce que fait le script :**

- ✅ Installe Oh My Zsh dans `~/.oh-my-zsh`
- ✅ Crée un backup de votre ancien `.zshrc`
- ✅ Configure Zsh comme shell par défaut
- ✅ Applique le thème `robbyrussell` par défaut
- ✅ Active les plugins de base (git)

### Étape 2 : Installer les plugins essentiels

```bash
# zsh-autosuggestions : Suggestions basées sur l'historique
brew install zsh-autosuggestions

# zsh-syntax-highlighting : Coloration syntaxique en temps réel
brew install zsh-syntax-highlighting
```

**Plugins installés :**

| Plugin                    | Fonction                                     | Exemple                                  |
| ------------------------- | -------------------------------------------- | ---------------------------------------- |
| `zsh-autosuggestions`     | Suggestions de commandes depuis l'historique | Tape `git`, voir suggestions en gris     |
| `zsh-syntax-highlighting` | Colore les commandes valides/invalides       | Commande valide = vert, invalide = rouge |

### Étape 3 : Configurer le .zshrc

Le fichier `.zshrc` est le fichier de configuration principal de Zsh. Il se trouve dans votre répertoire home.

```bash
# Ouvrir le fichier de configuration
nano ~/.zshrc
```

**Configuration complète à ajouter :**

```bash
# =====================================
# OH MY ZSH CONFIGURATION
# =====================================

# Path vers Oh My Zsh installation
export ZSH="$HOME/.oh-my-zsh"

# Thème à utiliser (voir liste : https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)
ZSH_THEME="robbyrussell"

# Plugins à activer
plugins=(
  git                      # Aliases Git
  zsh-autosuggestions     # Suggestions automatiques
  zsh-syntax-highlighting # Coloration syntaxique
  docker                  # Aliases Docker (optionnel)
  npm                     # Complétion npm (optionnel)
  node                    # Complétion node (optionnel)
)

# Charger Oh My Zsh
source $ZSH/oh-my-zsh.sh

# =====================================
# PLUGINS HOMEBREW
# =====================================

# zsh-syntax-highlighting
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# zsh-autosuggestions
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh

# =====================================
# ALIASES PERSONNALISÉS
# =====================================

# Navigation
alias ..="cd .."
alias ...="cd ../.."
alias ll="ls -lah"

# Git shortcuts
alias gs="git status"
alias ga="git add"
alias gc="git commit"
alias gp="git push"

# Développement
alias dev="npm run dev"
alias start="npm start"
alias build="npm run build"

# =====================================
# VARIABLES D'ENVIRONNEMENT
# =====================================

# NVM (Node Version Manager)
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"

# Homebrew
export PATH="/opt/homebrew/bin:$PATH"
```

**Sauvegarder et quitter :**

- Appuyez sur `Ctrl + X`
- Appuyez sur `Y` pour confirmer
- Appuyez sur `Entrée` pour valider

### Étape 4 : Recharger la configuration

```bash
# Recharger le terminal avec la nouvelle configuration
source ~/.zshrc
```

Votre terminal devrait maintenant afficher le nouveau thème et activer toutes les fonctionnalités !

## 🎨 Personnalisation

### Changer de thème

Oh My Zsh propose plus de 300 thèmes. Voici les plus populaires :

| Thème           | Aperçu                               | Niveau        |
| --------------- | ------------------------------------ | ------------- |
| `robbyrussell`  | Minimaliste, informations Git        | Débutant      |
| `agnoster`      | Powerline, nécessite police spéciale | Intermédiaire |
| `powerlevel10k` | Très customisable, ultra-rapide      | Avancé        |
| `spaceship`     | Moderne, affiche versions tools      | Intermédiaire |
| `awesomepanda`  | Coloré, emoji friendly               | Débutant      |
| `af-magic`      | Deux lignes, propre                  | Débutant      |

**Changer de thème :**

```bash
# 1. Éditer le .zshrc
nano ~/.zshrc

# 2. Modifier la ligne ZSH_THEME
ZSH_THEME="agnoster"  # Remplacer par votre choix

# 3. Recharger
source ~/.zshrc
```

**Voir tous les thèmes disponibles :**

```bash
ls ~/.oh-my-zsh/themes/
```

**Tester un thème temporairement :**

```bash
# Sans modifier le .zshrc
omz theme set agnoster
```

### Installer Powerlevel10k (recommandé)

Powerlevel10k est le thème le plus populaire et performant.

```bash
# 1. Cloner le repository
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# 2. Modifier le .zshrc
nano ~/.zshrc

# 3. Changer le thème
ZSH_THEME="powerlevel10k/powerlevel10k"

# 4. Recharger
source ~/.zshrc

# 5. Suivre le wizard de configuration
# Un assistant interactif vous guidera
```

### Plugins recommandés

**Plugins intégrés (déjà inclus dans Oh My Zsh) :**

```bash
plugins=(
  git                 # Aliases git (gs, ga, gc, gp, etc.)
  docker              # Complétion docker
  docker-compose      # Complétion docker-compose
  npm                 # Complétion npm
  node                # Complétion node
  yarn                # Complétion yarn
  vscode              # Raccourcis VS Code (code .)
  macos               # Commandes macOS (trash, man-preview)
  sudo                # Double ESC pour ajouter sudo
  web-search          # Recherche Google depuis terminal (google query)
  z                   # Navigation intelligente (apprentissage)
  extract             # Extraction universelle (extract file.*)
  history             # Historique amélioré
  colored-man-pages   # Pages man colorées
)
```

**Plugins externes à installer :**

```bash
# zsh-completions : Complétions additionnelles
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions

# zsh-history-substring-search : Recherche dans l'historique
git clone https://github.com/zsh-users/zsh-history-substring-search ${ZSH_CUSTOM:-~/.oh-my-zsh}/custom}/plugins/zsh-history-substring-search

# Ajouter dans .zshrc
plugins=(... zsh-completions zsh-history-substring-search)
```

### Aliases personnalisés avancés

```bash
# Dans votre .zshrc, section aliases

# Développement
alias nrd="npm run dev"
alias nrs="npm run start"
alias nrb="npm run build"
alias nrt="npm run test"
alias nrl="npm run lint"

# Git avancé
alias gaa="git add ."
alias gcm="git commit -m"
alias gpl="git pull"
alias gps="git push"
alias gst="git stash"
alias gco="git checkout"
alias gbr="git branch"
alias glog="git log --oneline --graph --all"

# Docker
alias dps="docker ps"
alias dimg="docker images"
alias dstop="docker stop $(docker ps -aq)"
alias drm="docker rm $(docker ps -aq)"
alias dprune="docker system prune -af"

# Système
alias ip="curl ifconfig.me"
alias ports="lsof -i -P | grep LISTEN"
alias cleanup="brew cleanup && npm cache clean --force"

# Navigation rapide
alias projects="cd ~/Projects"
alias downloads="cd ~/Downloads"
alias desktop="cd ~/Desktop"
```

## 🔧 Résolution de problèmes

### Problème : Source des plugins introuvable

**Erreur :**

```
zsh: command not found: /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```

**Solution :**

```bash
# 1. Vérifier l'emplacement d'installation
brew info zsh-autosuggestions
brew info zsh-syntax-highlighting

# 2. La commande retourne :
# Installed
# /opt/homebrew/Cellar/zsh-autosuggestions/0.7.0 (7 files, 47.6KB)

# 3. Copier le bon chemin dans le .zshrc
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh
source /opt/homebrew/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# 4. Recharger
source ~/.zshrc
```

### Problème : Thème ne s'affiche pas correctement

**Symptômes :**

- Caractères bizarres (□, ?, etc.)
- Flèches cassées
- Symboles manquants

**Solution : Installer une Nerd Font**

```bash
# 1. Installer une police compatible
brew tap homebrew/cask-fonts
brew install --cask font-meslo-lg-nerd-font

# 2. Configurer iTerm2 / Terminal
# iTerm2 : Preferences → Profiles → Text → Font
# Terminal : Preferences → Profiles → Text → Change

# 3. Sélectionner "MesloLGS NF"
```

**Polices recommandées :**

- MesloLGS NF (recommandée pour Powerlevel10k)
- Fira Code Nerd Font
- JetBrains Mono Nerd Font
- Hack Nerd Font

### Problème : Lenteur du terminal

**Solutions :**

```bash
# 1. Désactiver les plugins inutilisés
# Dans .zshrc, ne garder que les plugins essentiels
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

# 2. Optimiser NVM (si installé)
# Remplacer le chargement normal par un lazy load
export NVM_DIR="$HOME/.nvm"
alias nvm="unalias nvm; [ -s '$NVM_DIR/nvm.sh' ] && . '$NVM_DIR/nvm.sh'; nvm $@"

# 3. Utiliser Powerlevel10k au lieu d'autres thèmes
# Il est optimisé pour la performance

# 4. Profiler le temps de chargement
time zsh -i -c exit
```

### Problème : Autosuggestions ne fonctionnent pas

**Solutions :**

```bash
# 1. Vérifier l'installation
brew list zsh-autosuggestions

# 2. Réinstaller si nécessaire
brew reinstall zsh-autosuggestions

# 3. Vérifier le source dans .zshrc
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh

# 4. Tester la couleur (peut-être trop claire)
echo $ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE

# 5. Changer la couleur si nécessaire
# Ajouter dans .zshrc
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=240'
```

## 💡 Astuces et raccourcis

### Raccourcis clavier essentiels

| Raccourci           | Action                      |
| ------------------- | --------------------------- |
| `Ctrl + A`          | Aller au début de la ligne  |
| `Ctrl + E`          | Aller à la fin de la ligne  |
| `Ctrl + U`          | Effacer toute la ligne      |
| `Ctrl + K`          | Effacer jusqu'à la fin      |
| `Ctrl + W`          | Effacer le mot précédent    |
| `Ctrl + R`          | Recherche dans l'historique |
| `Ctrl + L`          | Clear screen                |
| `→` (flèche droite) | Accepter la suggestion      |
| `Tab`               | Auto-complétion             |
| `Option + →`        | Avancer d'un mot            |
| `Option + ←`        | Reculer d'un mot            |

### Fonctions utiles de Oh My Zsh

```bash
# Recherche dans l'historique
# Taper quelques lettres puis ↑/↓

# Expansion d'alias
# Taper un alias puis Ctrl+X puis A

# Kill processus sur port
killport 3000

# Copier le répertoire courant
copypath      # Copie dans le presse-papier

# Ouvrir le répertoire dans Finder
ofd           # Open Finder Directory

# Recherche Google depuis le terminal
google "css grid layout"

# Extraction universelle
extract archive.zip
extract file.tar.gz
extract document.rar
```

### Commandes Oh My Zsh

```bash
# Mettre à jour Oh My Zsh
omz update

# Recharger la config
omz reload

# Liste des plugins disponibles
omz plugin list

# Activer un plugin
omz plugin enable docker

# Changer de thème temporairement
omz theme set agnoster

# Diagnostic
omz doctor
```

## 📊 Comparaison avec Bash

| Fonctionnalité         | Bash     | Zsh + Oh My Zsh            |
| ---------------------- | -------- | -------------------------- |
| Auto-complétion        | Basique  | Intelligente, contextuelle |
| Syntax highlighting    | ❌       | ✅                         |
| Suggestions            | ❌       | ✅                         |
| Thèmes                 | Limités  | 300+                       |
| Plugins                | Manuels  | 280+ prêts à l'emploi      |
| Navigation             | Standard | Avec apprentissage (z)     |
| Correction orthographe | ❌       | ✅                         |
| Glob patterns          | Basiques | Avancés                    |
| Historique partagé     | Non      | Oui                        |

## 🎓 Bonnes pratiques

### ✅ À faire

- **Sauvegarder votre .zshrc** : `cp ~/.zshrc ~/.zshrc.backup`
- **Mettre à jour régulièrement** : `omz update` (mensuel)
- **Garder les plugins essentiels** : N'activez que ce que vous utilisez
- **Documenter vos aliases** : Ajoutez des commentaires
- **Tester les thèmes** : Trouvez celui qui vous convient
- **Utiliser .zshrc.local** : Pour config machine-spécifique
- **Versionner votre config** : Git repository de dotfiles

### ❌ À éviter

- **Trop de plugins** : Ralentit le démarrage du terminal
- **Modifier les fichiers Oh My Zsh** : Utilisez `~/.zshrc`
- **Ignorer les mises à jour** : Nouvelles fonctionnalités et fixes
- **Copier-coller sans comprendre** : Prenez le temps de lire
- **Désactiver la sécurité** : Ne pas faire `ZSH_DISABLE_COMPFIX=true` sans raison

## 📚 Ressources complémentaires

### Documentation officielle

- [Oh My Zsh GitHub](https://github.com/ohmyzsh/ohmyzsh)
- [Wiki Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki)
- [Liste des thèmes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)
- [Liste des plugins](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)

### Thèmes populaires

- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- [Spaceship](https://github.com/spaceship-prompt/spaceship-prompt)
- [Starship](https://starship.rs/) (alternative cross-shell)

### Plugins externes recommandés

- [fzf](https://github.com/junegunn/fzf) - Fuzzy finder puissant
- [thefuck](https://github.com/nvbn/thefuck) - Correction de commandes
- [bat](https://github.com/sharkdp/bat) - Cat amélioré
- [exa](https://github.com/ogham/exa) - ls moderne

### Tutorials vidéo

- [Oh My Zsh Tutorial - Traversy Media](https://www.youtube.com/watch?v=MSPu-lYF-A8)
- [Zsh Configuration - ThePrimeagen](https://www.youtube.com/watch?v=ud7YxC33Z3w)

## 🔄 Changelog

### Version 1.0.0 - 2025-12-01

- ✨ Documentation initiale complète
- 📝 Installation pas à pas avec Oh My Zsh
- 🔌 Configuration des plugins essentiels
- 🎨 Guide des thèmes et personnalisation
- 🔧 Section troubleshooting détaillée
- 💡 Astuces et bonnes pratiques
- 📚 Ressources complémentaires

---

**Made with ❤️ for terminal enthusiasts**

> 💡 **Astuce finale** : Prenez le temps d'explorer les plugins et thèmes. Votre terminal deviendra rapidement votre outil préféré !
