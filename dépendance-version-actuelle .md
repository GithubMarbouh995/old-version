# Dépendances entre connecteurs et plateforme - Version actuelle

## 1. Dépendances de configuration
**Problèmes identifiés :**
- Configuration partagée entre tous les connecteurs
- Un changement pour un connecteur peut affecter toute la plateforme
- Impossible d'extraire un connecteur spécifique avec sa configuration

## 2. Dépendances d'instanciation des clients SOAP
**Problèmes identifiés :**
- Création centralisée des clients pour tous les systèmes externes
- Modification d'un client impacte potentiellement tous les autres
- Impossibilité d'extraire un connecteur individuel sans sa dépendance à cette configuration

## 3. Dépendances au niveau des services d'implémentation
**Problèmes identifiés :**
- Injection directe entre services de domaines différents
- Appels de méthodes directs entre domaines fonctionnels distincts
- Impossibilité d'extraire un service sans entraîner ses dépendances

## 4. Dépendances de modèles de données partagés
**Problèmes identifiés :**
- Modèles utilisés à travers différents connecteurs
- Modification d'un modèle peut impacter plusieurs services
- Absence de limites claires entre les contextes de domaine

## 5. Dépendances liées aux exceptions et à la gestion d'erreurs
**Problèmes identifiés :**
- Gestionnaire d'exceptions unique pour tous les domaines
- Couplage entre les types d'exceptions de différents domaines
- Traitement personnalisé par domaine difficile à mettre en œuvre

## 6. Dépendances liées aux utilitaires partagés
**Problèmes identifiés :**
- Utilitaires disséminés dans le code et partagés implicitement
- Dépendances non documentées difficiles à identifier
- Difficultés à faire évoluer ces utilitaires sans impacter plusieurs connecteurs

## 7. Dépendances liées à la sécurité et l'authentification
**Problèmes identifiés :**
- Un seul système d'authentification pour tous les connecteurs
- Couplage fort entre les services et le contexte de sécurité
- Difficile d'adapter la sécurité pour des besoins spécifiques à un connecteur

## 8. Dépendances de packaging et déploiement
**Problèmes identifiés :**
- Déploiement monolithique de tous les connecteurs ensemble
- Impossibilité de mettre à jour un seul connecteur
- Pas de versionnement indépendant des différents connecteurs

## Conclusion
L'architecture actuelle présente un couplage fort entre les différents connecteurs et la plateforme, rendant difficile :
- L'extraction d'un connecteur pour réutilisation dans un autre contexte
- L'évolution indépendante de chaque connecteur
- La maintenance ciblée d'un connecteur spécifique
- Le test isolé des fonctionnalités d'un connecteur
- L'adaptation aux besoins spécifiques de différents clients
