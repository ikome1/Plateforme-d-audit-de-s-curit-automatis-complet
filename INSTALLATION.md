# 🚀 Guide d'Installation Rapide

## Installation Complète en 3 Étapes

### 1. Installer Nmap (Obligatoire)

**macOS :**
```bash
brew install nmap
```

**Linux (Debian/Ubuntu) :**
```bash
sudo apt-get update
sudo apt-get install nmap
```

**Linux (RedHat/CentOS/Fedora) :**
```bash
sudo yum install nmap
# ou
sudo dnf install nmap
```

**Windows :**
- Télécharger depuis : https://nmap.org/download.html
- Installer et ajouter au PATH

**Vérifier l'installation :**
```bash
nmap --version
```

### 2. Installer les Dépendances Python

```bash
cd "Plateforme d'audit de sécurité automatisé"
pip install -r requirements.txt
```

Ou avec pip3 :
```bash
pip3 install -r requirements.txt
```

**Dépendances installées :**
- requests
- beautifulsoup4
- lxml

### 3. Vérifier l'Installation

```bash
python3 pentest_platform.py --help
```

Vous devriez voir le message d'aide s'afficher.

## Test Rapide

Testez sur un site de test public (légal) :

```bash
python3 pentest_platform.py scanme.nmap.org --scan-type quick
```

## Problèmes Courants

### ModuleNotFoundError: No module named 'requests'

**Solution :**
```bash
pip install -r requirements.txt
```

### Nmap n'est pas installé

**Solution :**
- Installez Nmap selon votre système (voir étape 1)
- Vérifiez avec : `which nmap` ou `nmap --version`

### Permission denied (Linux)

**Solution :**
Certains scans nécessitent des privilèges root :
```bash
sudo python3 pentest_platform.py 192.168.1.1
```

### Timeout lors du scan

**Solution :**
- Utilisez `--scan-type quick` pour un scan plus rapide
- Le scan `comprehensive` peut prendre plusieurs heures
- Augmentez le timeout avec `--timeout 600`

## Prêt à Utiliser !

Une fois l'installation terminée, vous pouvez commencer à utiliser la plateforme :

```bash
python3 pentest_platform.py <cible> --html
```

