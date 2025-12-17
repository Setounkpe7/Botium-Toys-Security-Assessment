# Botium Toys – Security Program Assessment & Controls  
Projet issu du Google Cybersecurity Professional Certificate

## Objectif du projet

Ce projet, réalisé dans le cadre du **Google Cybersecurity Professional Certificate**, consiste à évaluer le programme de sécurité de l’entreprise fictive **Botium Toys**.  
Les objectifs principaux étaient :

- Définir le **scope** et les **goals** de l’audit de sécurité  
- Identifier les **risques majeurs** liés aux actifs de l’entreprise  
- Évaluer les **contrôles existants** et les manques à combler  
- Analyser le niveau de **conformité** aux bonnes pratiques (PCI DSS, GDPR, SOC 1/2)  
- Formuler des **recommandations** concrètes pour améliorer la posture de sécurité  


---

## Contexte

**Botium Toys** est une entreprise qui vend des jouets en magasin et en ligne.  
L’audit couvre :

- L’ensemble du **programme de sécurité** de l’organisation  
- Les **actifs IT** : équipements on-premises, postes utilisateurs, systèmes, bases de données, e-commerce, réseau interne, accès Internet, données stockées et systèmes legacy
- Les **processus** et **contrôles** liés à la protection des données et à la conformité réglementaire  

Le rapport initial de risque indique :

- Une **gestion des actifs insuffisante**  
- Un **manque de contrôles** et de conformité aux réglementations US et internationales  
- Un **score de risque de 8/10**, jugé élevé :contentReference[oaicite:4]{index=4}  

---

## Actifs principaux

Actifs gérés par l’IT : 

- Équipements on-premises (bureaux, magasin, entrepôt)  
- Équipements utilisateurs (PC, laptops, smartphones, périphériques)  
- Systèmes métiers : comptabilité, télécoms, base de données, sécurité, e-commerce, gestion d’inventaire  
- Réseau interne & accès Internet  
- Systèmes legacy nécessitant de la supervision manuelle  
- Données clients, y compris **données de carte bancaire** et **PII/SPII**  

---

## Risques identifiés

Le rapport souligne plusieurs risques critiques : 

- **Accès trop large aux données internes** : tous les employés peuvent accéder aux données stockées, y compris aux données de cartes bancaires et PII/SPII  
- **Absence d’encryption** des données de carte bancaire stockées localement  
- **Absence ou faiblesse des contrôles d’accès** :
  - Pas de **least privilege**
  - Pas de **séparation des tâches**  
- **Manque de sauvegardes et de plan de reprise d’activité** (DRP inexistants)  
- **Absence d’IDS** (Intrusion Detection System)  
- Politique de mots de passe trop faible et pas de gestion centralisée des mots de passe  

Conséquences potentielles :

- Non-conformité aux réglementations (PCI DSS, GDPR, SOC)  
- Risques élevés de fuite de données, amendes, et impact réputationnel  
- Risques d’interruption d’activité (disponibilité non garantie)

---

## Évaluation des contrôles

### Contrôles existants
D’après la checklist et les documents de contrôle : 

- Pare-feu en place, avec règles de filtrage définies  
- Antivirus installé et monitoré  
- Disponibilité et intégrité partiellement assurées  
- Procédure pour notifier les clients EU sous 72h en cas de breach (GDPR)  
- Politiques de mot de passe existantes mais insuffisantes

### Contrôles manquants ou insuffisants

- **Least privilege** : non implémenté  
- **Séparation des tâches** : non implémentée  
- **IDS / IPS** : absent  
- **Backups & Disaster Recovery Plans** : inexistants  
- **Encryption** des données sensibles (dont cartes bancaires) : non utilisée  
- **Gestion centralisée des mots de passe** : absente  
- **Gestion des systèmes legacy** : pas de planning régulier structuré 

Les documents de “control categories” précisent les types et objectifs de chaque contrôle (administratif, technique, physique) ainsi que leur rôle (préventif, détectif, correctif, dissuasif). 

---

## Conformité (PCI DSS, GDPR, SOC)

D’après la checklist de conformité : 

### PCI DSS
- Accès aux données carte bancaire non suffisamment restreint  
- Données carte bancaire non chiffrées dans l’environnement interne  
- Politiques de mots de passe et gestion non alignées sur les bonnes pratiques

### GDPR
- Des mécanismes existent pour notifier les clients EU en cas de breach sous 72h  
- Besoin de renforcer la classification, l’inventaire et la documentation des données et processus

### SOC 1 / SOC 2
- Politiques d’accès utilisateur insuffisantes  
- Confidentialité et intégrité des données sensibles non entièrement garanties  
- Disponibilité partiellement couverte, mais pas de stratégie de reprise validée  

---

## Recommandations prioritaires

### 1. Contrôles d’accès & identité

- Implémenter **Least Privilege** et **séparation des tâches**  
- Déployer un **système de gestion des identités et des accès (IAM)**  
- Mettre en place un **password manager** centralisé, avec :
  - politiques de complexité
  - rotation des mots de passe
  - interdiction de réutilisation des anciens mots de passe  


### 2. Protection des données sensibles

- Chiffrer les données de carte bancaire en transit et au repos (TLS, encryption à jour) 
- Restreindre l’accès aux PII/SPII aux seules fonctions qui en ont besoin  
- Mettre en place des mécanismes de classification et d’étiquetage des données  

### 3. Détection et réponse

- Déployer un **IDS/IPS** pour détecter le trafic anormal et les intrusions 
- Implémenter des **logs centralisés** et un SIEM pour la corrélation  
- Définir des **playbooks d’incident** (processus de réponse documentés)

### 4. Continuité d’activité

- Mettre en place des **sauvegardes régulières** des données critiques  
- Établir un **Disaster Recovery Plan** (DRP) formel et testé 
- Définir des RTO/RPO pour les services critiques

### 5. Conformité & gouvernance

- Mettre à jour les politiques pour alignement avec :
  - **PCI DSS** (stockage/traitement des cartes)  
  - **GDPR** (données clients EU)  
  - **SOC 2** (sécurité, disponibilité, confidentialité, intégrité, vie privée)  
- Documenter et suivre une feuille de route de mise en conformité

---

## Compétences développées

- Réalisation d’un **audit de sécurité** basé sur un scope défini  
- Analyse de risques (identification, estimation, scoring)  
- Cartographie des **contrôles** (administratifs, techniques, physiques)  
- Utilisation de **checklists de contrôle & conformité**  
- Application de frameworks et bonnes pratiques (NIST CSF, PCI DSS, GDPR, SOC)  
- Rédaction de recommandations concrètes pour un management non technique  

---

## Outils et références conceptuelles

- **NIST Cybersecurity Framework (CSF)** – fonction *Identify* pour la gestion des actifs et des risques :contentReference[oaicite:18]{index=18}  
- Documentation interne :  
  - Scope, goals, risk report (Botium Toys)  
  - Controls & Compliance Checklist  
  - Control Categories (administratif, technique, physique)  

---

## Résultats

- Évaluation structurée du niveau de maturité sécurité de Botium Toys  
- Identification des principaux **gaps de contrôle** (least privilege, DRP, encryption, IDS, etc.)  
- Mise en évidence des **risques de non-conformité** aux normes PCI/GDPR/SOC  
- Production d’un **plan de recommandations** orienté vers l’action pour améliorer la posture de sécurité

---

