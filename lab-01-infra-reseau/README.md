# Projet de Lab Réseau & Sécurité

## Présentation
Ce projet consiste à concevoir et déployer une infrastructure réseau sécurisée et supervisée pour une PME fictive.

Il met en œuvre :
- un contrôleur de domaine Windows Server (AD, DNS, DHCP),
- un pare-feu pfSense pour la sécurité et le routage,
- des postes clients Windows,
- une solution de supervision Zabbix.

---

## Objectifs pédagogiques
- Comprendre l’architecture d’un réseau d’entreprise
- Mettre en place des services réseau centralisés
- Sécuriser les flux via un pare-feu
- Superviser l’infrastructure et les services critiques

---

## Architecture (vue d’ensemble)
L’infrastructure repose sur une segmentation réseau contrôlée par pfSense, avec des services centralisés sur Windows Server et une supervision globale via Zabbix.

> Le schéma détaillé et la description complète sont disponibles dans la documentation.

---

## Technologies utilisées
- Windows Server 2022 (AD, DNS, DHCP)
- pfSense 2.7.x
- Windows 10
- Ubuntu 24.04
- Zabbix 6.x
