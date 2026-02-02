# Projet de Lab Réseau & Sécurité  
## Infrastructure réseau sécurisée et supervisée pour une PME fictive

---

## 1. Présentation du projet

Ce projet a pour objectif de concevoir et déployer une **infrastructure réseau d’entreprise sécurisée et supervisée**, destinée à une PME fictive.  
Il s’inscrit dans un cadre pédagogique visant à mettre en pratique les compétences en **administration systèmes, réseaux, sécurité et supervision**.

L’infrastructure mise en place comprend :
- un contrôleur de domaine **Windows Server** (Active Directory, DNS, DHCP),
- un **pare-feu pfSense** pour la sécurité et le routage,
- des **postes clients Windows** simulant les utilisateurs,
- une solution de **supervision Zabbix** pour le monitoring global du réseau.

---

## 2. Objectifs pédagogiques

- Comprendre l’architecture d’un réseau d’entreprise
- Mettre en œuvre une authentification centralisée
- Sécuriser les flux réseau via un pare-feu
- Superviser les équipements et services critiques
- Tester et valider le bon fonctionnement de l’infrastructure

---

## 3. Architecture du réseau

### 3.1 Schéma logique
Le schéma logique de l’infrastructure est fourni dans la documentation associée au projet.

### 3.2 Description des sous-réseaux

| Réseau | Adresse | Rôle | Équipements |
|------|--------|------|------------|
| LAN Serveurs | 10.0.0.0/24 | Infrastructure interne | Windows Server, Zabbix |
| LAN Utilisateurs | 20.0.0.0/24 | Postes clients | Windows 10 |
| WAN | DHCP | Accès Internet simulé | pfSense |

---

## 4. Composants de l’infrastructure

| Composant | Rôle | Système | Adresse IP |
|---------|------|--------|------------|
| pfSense | Pare-feu et routage | pfSense 2.7.x | WAN : 20.0.0.10 / LAN : 10.0.0.10 |
| Windows Server 2022 | AD, DNS, DHCP | Windows Server | 10.0.0.11 |
| Zabbix Server | Supervision | Ubuntu 24.04 + Zabbix 6.x | 10.0.0.12 |
| Clients Windows | Postes utilisateurs | Windows 10 | DHCP (20.0.0.x) |

---

## 5. Configuration technique

### 5.1 Pare-feu pfSense

- Interface WAN : DHCP (accès Internet simulé)
- Interface LAN : 10.0.0.10 (passerelle interne)
- Interface OPT1 : 20.0.0.10

Règles principales :
- Autorisation du trafic UDP entre OPT1 et LAN pour le DHCP Relay
- Autorisation du trafic DNS entre les clients et le serveur Windows
- Blocage de tout accès non autorisé du WAN vers le LAN
- Service DHCP désactivé (géré par Windows Server)
- Installation de l’agent Zabbix pour la supervision
- Centralisation des logs vers Zabbix ou Syslog

Principes de filtrage :
- Pare-feu stateful
- Règles appliquées en entrée sur chaque interface
- Lecture des règles de haut en bas
- Politique par défaut restrictive (deny all)

---

### 5.2 Windows Server

- Installation du rôle Active Directory Domain Services
- Création du domaine : `koma.cg`
- DNS intégré à Active Directory
- DHCP configuré pour le réseau 20.0.0.0/24
- Création de comptes utilisateurs et groupes
- Installation de l’agent Zabbix

---

### 5.3 Serveur Zabbix

- Installation d’Apache, MySQL et PHP
- Déploiement de Zabbix Server 6.x
- Création et configuration de la base de données MySQL
- Installation des agents Zabbix sur tous les hôtes
- Ajout des machines via l’interface Web Zabbix
- Application des templates adaptés (Windows et Linux)

Les tableaux de bord permettent le suivi :
- de la disponibilité des hôtes,
- de la charge CPU,
- de l’utilisation mémoire,
- de l’état des services réseau.

---

## 6. Tests de fonctionnement

| Test | Description | Résultat |
|----|------------|---------|
| Connectivité inter-réseaux | Ping entre 10.0.0.x et 20.0.0.x | Conforme |
| Accès Internet | Navigation des clients via pfSense | Conforme |
| Filtrage réseau | Blocage d’un port non autorisé | Conforme |
| Supervision | Remontée des métriques Zabbix | Conforme |
| Intégration AD | Jonction des clients au domaine | Conforme |

---

## 7. Supervision et sécurité

- Supervision de la disponibilité du pare-feu, du serveur AD, du DNS et des clients
- Surveillance des ressources système (CPU, mémoire, disque)
- Déclenchement d’alertes en cas d’incident
- Application de stratégies de sécurité Active Directory
- Centralisation des journaux pfSense

---

## 8. Conclusion

Ce projet a permis de mettre en œuvre une **infrastructure réseau complète et sécurisée**, proche d’un environnement professionnel réel.  
Il a renforcé les compétences en administration Windows Server, sécurité réseau, supervision et diagnostic.

### Perspectives d’amélioration :
- Mise en place d’un VPN
- Ajout d’un serveur de messagerie interne
- Déploiement d’un IDS/IPS (Suricata ou Snort)
- Automatisation via Ansible

---

## 9. Auteur

Nom : À compléter  
Formation : À compléter  
Année : À compléter  

---

## 10. Licence

Projet pédagogique – usage éducatif uniquement.
