# 🔥 Plateforme d'Audit de Sécurité Automatisé (Network & Web)

**Outil de pentest automatisé de bout en bout : reconnaissance → analyse → priorisation → reporting**

Plateforme professionnelle Python qui automatise un mini pentest complet avec reconnaissance multi-cibles, analyse intelligente des services, audit de sécurité web, scoring des risques et génération de rapports professionnels.

## ✨ Vision Globale

Cet outil n'est **pas juste un script**, c'est une **plateforme complète** qui intègre :

1. ✅ **Reconnaissance multi-cibles** - Scan de plusieurs IPs/domaines avec Nmap
2. 🔍 **Analyse intelligente des services** - Identification et évaluation des services détectés
3. 🌐 **Audit de sécurité web automatisé** - Tests XSS, SQLi, vérification des headers
4. 🎯 **Corrélation & scoring des risques** - Priorisation professionnelle des vulnérabilités
5. 📊 **Reporting professionnel** - Rapports structurés en TXT, JSON et HTML

## 🎯 Fonctionnalités Détaillées

### 1️⃣ Reconnaissance Multi-Cibles

- Scan de plusieurs IPs ou domaines simultanément
- Découverte automatique des ports et services ouverts
- Identification des services web (HTTP/HTTPS)
- Détection du système d'exploitation
- Utilisation de Nmap via Python avec différents types de scans :
  - **Quick** : Scan rapide (ports les plus communs)
  - **Normal** : Scan standard (ports 1-1000) - **recommandé**
  - **Comprehensive** : Scan complet (tous les ports)

### 2️⃣ Analyse Intelligente des Services

Pour chaque service détecté, l'outil :

- Identifie le type de service (SSH, FTP, HTTP, SMB, MySQL, etc.)
- Vérifie les configurations faibles
- Repère les services obsolètes (versions vulnérables)
- Détecte les services non sécurisés (Telnet, FTP, etc.)
- Identifie les ports sensibles (SSH, RDP, SMB, bases de données)

**Logique pentest > simple scan** : Analyse contextuelle et évaluation des risques.

### 3️⃣ Audit de Sécurité Web Automatisé

Pour chaque service HTTP/HTTPS détecté :

- ✅ **Vérification des headers de sécurité** :
  - Content-Security-Policy (CSP)
  - Strict-Transport-Security (HSTS)
  - X-Frame-Options
  - X-Content-Type-Options
  - X-XSS-Protection
  
- 🔍 **Détection de formulaires** :
  - Identification automatique de tous les formulaires
  - Extraction des champs d'input
  
- ⚠️ **Tests XSS / SQLi basiques** :
  - Tests de vulnérabilités Cross-Site Scripting (XSS)
  - Tests de vulnérabilités SQL Injection (SQLi)
  - Détection des erreurs SQL dans les réponses
  
- 🎯 **Enumération d'endpoints sensibles** :
  - Scan de chemins communément ciblés (/admin, /phpmyadmin, /.env, etc.)
  - Détection d'endpoints accessibles

**Pentest web crédible** avec des tests réels et des résultats exploitables.

### 4️⃣ Corrélation & Scoring des Risques

L'outil :

- Classe les failles par sévérité (CRITIQUE / ÉLEVÉ / MOYEN / FAIBLE)
- Priorise les risques avec un système de scoring intelligent
- Évite les faux positifs simples (déduplication)
- Corrèle les findings pour une vue d'ensemble
- Génère un résumé statistique

**Scoring des risques** :
- **CRITIQUE** (score 10+) : SQL Injection, services non sécurisés critiques
- **ÉLEVÉ** (score 7+) : XSS, versions obsolètes, services non sécurisés
- **MOYEN** (score 4+) : Headers manquants, ports sensibles
- **FAIBLE** (score 1+) : Configurations mineures

**Passage junior → pro** : Priorisation intelligente et évitement des faux positifs.

### 5️⃣ Reporting Professionnel Automatique

Génération de rapports structurés avec :

- **Résumé exécutif** : Vue d'ensemble pour la direction
- **Détails techniques** : Informations complètes pour les équipes techniques
- **Recommandations concrètes** : Actions à entreprendre pour chaque finding

**Formats disponibles** :
- 📄 **TXT** : Rapport texte structuré et lisible
- 📊 **JSON** : Données structurées pour traitement automatisé
- 🌐 **HTML** : Rapport visuel professionnel avec style CSS

## 📋 Prérequis

### Python
- Python 3.6 ou supérieur

### Système
- **Nmap** installé et accessible via ligne de commande
  - macOS : `brew install nmap`
  - Linux (Debian/Ubuntu) : `sudo apt-get install nmap`
  - Linux (RedHat/CentOS) : `sudo yum install nmap`
  - Windows : Télécharger depuis [nmap.org](https://nmap.org/download.html)

### Dépendances Python
Installer avec : `pip install -r requirements.txt`

## 🚀 Installation

1. **Clonez ou téléchargez le projet**

2. **Installez les dépendances Python** :
```bash
pip install -r requirements.txt
```

3. **Vérifiez que Nmap est installé** :
```bash
nmap --version
```

4. **Rendez le script exécutable (optionnel)** :
```bash
chmod +x pentest_platform.py
```

## 📖 Utilisation

### Utilisation de base

```bash
python3 pentest_platform.py <cible1> [cible2] [cible3] ...
```

**Exemple :**
```bash
python3 pentest_platform.py 192.168.1.1
python3 pentest_platform.py example.com test.com
python3 pentest_platform.py 192.168.1.1 192.168.1.2 192.168.1.3
```

### Options disponibles

```bash
python3 pentest_platform.py <cibles> [options]
```

**Options :**

- `--scan-type, -t TYPE` : Type de scan Nmap
  - `quick` : Scan rapide (ports communs)
  - `normal` : Scan normal (ports 1-1000) - **défaut**
  - `comprehensive` : Scan complet (tous les ports)

- `--timeout SECONDS` : Timeout pour les scans Nmap (défaut: 300 secondes)

- `--output-dir, -o DIR` : Répertoire de sortie pour les rapports (défaut: `reports`)

- `--html` : Générer également le rapport HTML

- `--txt-only` : Générer uniquement le rapport TXT

- `--json-only` : Générer uniquement le rapport JSON

- `--verify-ssl` : Vérifier les certificats SSL (désactivé par défaut pour les tests)

### Exemples d'utilisation avancés

**Scan rapide de plusieurs cibles :**
```bash
python3 pentest_platform.py 192.168.1.1 192.168.1.2 --scan-type quick
```

**Scan complet avec rapport HTML :**
```bash
python3 pentest_platform.py example.com --scan-type comprehensive --html
```

**Sauvegarder dans un répertoire personnalisé :**
```bash
python3 pentest_platform.py target.com --output-dir mes_rapports
```

**Scan avec vérification SSL :**
```bash
python3 pentest_platform.py https://example.com --verify-ssl
```

**Uniquement rapport JSON pour traitement automatisé :**
```bash
python3 pentest_platform.py 192.168.1.1 --json-only
```

## 🔄 Flux de Travail Complet

Le processus d'audit suit ces phases :

```
1. RECONNAISSANCE
   ↓ Scan Nmap multi-cibles
   ↓ Découverte ports/services
   ↓ Identification services web

2. ANALYSE DES SERVICES
   ↓ Évaluation de chaque service
   ↓ Détection configurations faibles
   ↓ Identification versions obsolètes

3. AUDIT WEB
   ↓ Tests sur services HTTP/HTTPS
   ↓ Vérification headers sécurité
   ↓ Tests XSS/SQLi
   ↓ Enumération endpoints

4. SCORING & PRIORISATION
   ↓ Calcul scores de risque
   ↓ Déduplication findings
   ↓ Classification par sévérité

5. REPORTING
   ↓ Génération rapports TXT/JSON/HTML
   ↓ Résumé exécutif
   ↓ Recommandations concrètes
```

## 📊 Exemple de Sortie

```
================================================================================
  PLATEFORME D'AUDIT DE SÉCURITÉ AUTOMATISÉ
  Network & Web Pentest - Version 1.0
================================================================================

================================================================================
PHASE 1: RECONNAISSANCE
================================================================================

[*] Cibles à scanner: 1
[*] Type de scan: normal

[1/1] Scan de 192.168.1.1...
  [+] 22 port(s) ouvert(s), 2 service(s) web

================================================================================
PHASE 2: ANALYSE DES SERVICES
================================================================================

[*] Analyse de 192.168.1.1 (22 port(s))
  [HIGH] Port 21: FTP non sécurisé - FTP non sécurisé
  [MEDIUM] Port 22: Port sensible 22 (SSH) ouvert - Accès à distance

================================================================================
PHASE 3: AUDIT WEB
================================================================================

  [*] Audit de http://192.168.1.1:80...
    [!] 3 problème(s) détecté(s)

================================================================================
PHASE 4: SCORING & PRIORISATION DES RISQUES
================================================================================

[*] Findings totaux: 8
[*] Findings uniques: 6

  [CRITICAL] 1 finding(s)
  [HIGH] 2 finding(s)
  [MEDIUM] 3 finding(s)
  [LOW] 0 finding(s)

================================================================================
PHASE 5: GÉNÉRATION DE RAPPORTS
================================================================================

[+] Rapport TXT généré: reports/rapport_pentest_20240115_103000.txt
[+] Rapport JSON généré: reports/rapport_pentest_20240115_103000.json
[+] Rapport HTML généré: reports/rapport_pentest_20240115_103000.html

[+] Audit terminé avec succès!
[*] 3 rapport(s) généré(s)
```

## 📁 Structure des Rapports

### Rapport TXT

Rapport texte structuré avec :
- Résumé exécutif
- Findings détaillés par sévérité
- Recommandations pour chaque problème
- Recommandations générales

### Rapport JSON

Données structurées JSON avec :
- Métadonnées (date, version)
- Résultats complets de reconnaissance
- Analyse de risques détaillée
- Résumé statistique

**Structure JSON :**
```json
{
  "metadata": {
    "report_date": "2024-01-15T10:30:00",
    "report_version": "1.0",
    "tool": "Plateforme d'Audit de Sécurité Automatisé"
  },
  "reconnaissance": [...],
  "risk_analysis": {
    "prioritized": {
      "critical": [...],
      "high": [...],
      "medium": [...],
      "low": [...]
    },
    "all_findings": [...],
    "summary": {...}
  }
}
```

### Rapport HTML

Rapport visuel professionnel avec :
- Design moderne et responsive
- Tableaux colorés par sévérité
- Formatage professionnel
- Facilement partageable

## ⚠️ Avertissements Légaux & Éthiques

### ⚠️ Utilisation Légale Uniquement

- **N'utilisez cet outil QUE sur des systèmes que vous autorisez**
- Le pentest non autorisé est **ILLÉGAL** dans la plupart des juridictions
- Assurez-vous d'avoir une **autorisation écrite** avant tout test
- Respectez les conditions d'utilisation des systèmes testés

### 🔒 Usage Responsable

- Utilisez cet outil à des fins **éducatives** et **d'audit légitime**
- Pour **votre propre infrastructure** ou avec **autorisation explicite**
- Ne scannez **PAS** des systèmes publics sans permission
- Suivez les **bonnes pratiques de sécurité** et les **règles éthiques**

### 📚 Sites de Test Légaux

Pour tester de manière légale :

- **scanme.nmap.org** - Site de test officiel de Nmap
- **testphp.vulnweb.com** - Site de test avec vulnérabilités intentionnelles
- Votre propre infrastructure de test
- Serveurs avec autorisation explicite

## 🔧 Dépannage

### Nmap non installé

**Erreur :** `Nmap n'est pas installé`

**Solution :**
```bash
# macOS
brew install nmap

# Linux (Debian/Ubuntu)
sudo apt-get update && sudo apt-get install nmap

# Linux (RedHat/CentOS)
sudo yum install nmap

# Vérifier
nmap --version
```

### Module Python manquant

**Erreur :** `ModuleNotFoundError: No module named 'requests'`

**Solution :**
```bash
pip install -r requirements.txt
```

### Scan très lent

**Solution :**
- Utilisez `--scan-type quick` pour un scan plus rapide
- Le scan `comprehensive` peut prendre plusieurs heures
- Réduisez le nombre de cibles simultanées

### Aucun résultat de reconnaissance

**Solution :**
- Vérifiez que les cibles sont accessibles
- Vérifiez vos permissions réseau
- Certains scans nécessitent des privilèges root (Linux)
- Utilisez `sudo` si nécessaire : `sudo python3 pentest_platform.py ...`

### Erreurs SSL

**Solution :**
- Utilisez `--verify-ssl` seulement si vous avez confiance dans le certificat
- Par défaut, la vérification SSL est désactivée pour les tests

## 🎓 Cas d'Usage

### 1. Audit de Sécurité Initial

Premier audit d'une infrastructure :
```bash
python3 pentest_platform.py infra.example.com --scan-type comprehensive --html
```

### 2. Scan Rapide de Routine

Scan rapide régulier :
```bash
python3 pentest_platform.py 192.168.1.1 192.168.1.2 --scan-type quick
```

### 3. Audit Web Spécifique

Focus sur les services web :
```bash
python3 pentest_platform.py webapp.example.com --html
```

### 4. Reporting Automatisé

Intégration dans un pipeline CI/CD :
```bash
python3 pentest_platform.py staging.example.com --json-only --output-dir reports/$(date +%Y%m%d)
```

## 📚 Ressources

- [Nmap Documentation](https://nmap.org/book/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/)

## 🔄 Évolutions Futures

Fonctionnalités prévues :

- [ ] Support de plages d'IPs (CIDR notation)
- [ ] Intégration avec des bases de données CVE
- [ ] Export vers des formats supplémentaires (PDF, XML)
- [ ] Dashboard web interactif
- [ ] Comparaison entre scans (différenciation temporelle)
- [ ] Support de plugins personnalisés
- [ ] Intégration avec des outils SIEM

## 📄 Licence

Ce projet est fourni tel quel, à des fins éducatives.

## 👤 Auteur

Plateforme d'Audit de Sécurité Automatisé - Projet Python Complexe

## 🙏 Remerciements

- Nmap Project pour l'outil de référence
- OWASP pour les bonnes pratiques
- La communauté de sécurité open-source

---

**Note** : Utilisez cet outil de manière responsable et éthique. Le pentest non autorisé est illégal. Cet outil est destiné à l'éducation et aux audits légitimes uniquement.

**🔥 Plateforme Professionnelle - Junior → Pro 🚀**

