# TP 8 : Spring @RestController

Petite API REST pour gérer des comptes bancaires, faite avec Spring Boot.
On peut ajouter, lister, modifier et supprimer des comptes, et les données sont renvoyées en JSON ou en XML.

## Ce qu'on a utilisé

- Java 17
- Spring Boot 3.1.5 (Web, Data JPA, DevTools)
- Base de données H2 en mémoire
- Lombok
- Swagger (springdoc-openapi) pour la documentation

## Lancer le projet

1. Ouvrir le dossier `ms-banque` dans IntelliJ IDEA ou Eclipse (projet Maven).
2. Attendre que Maven télécharge les dépendances.
3. Lancer la classe `MsBanqueApplication`, ou taper dans un terminal :

```
mvn spring-boot:run
```

L'application démarre sur le port **8082**. Au démarrage, 3 comptes sont créés automatiquement avec un solde aléatoire.

## Les liens utiles

| Quoi | Lien |
|---|---|
| Liste des comptes | http://localhost:8082/banque/comptes |
| Swagger | http://localhost:8082/swagger-ui.html |
| Console H2 | http://localhost:8082/h2-console |

## Les endpoints

| Méthode | URL | Ce que ça fait |
|---|---|---|
| GET | `/banque/comptes` | Récupère tous les comptes |
| GET | `/banque/comptes/{id}` | Récupère un compte |
| POST | `/banque/comptes` | Crée un compte |
| PUT | `/banque/comptes/{id}` | Modifie un compte |
| DELETE | `/banque/comptes/{id}` | Supprime un compte |

Exemple pour créer un compte :

```
curl -X POST "http://localhost:8082/banque/comptes" \
  -H "Content-Type: application/json" \
  -d '{"solde": 1500.0, "dateCreation": "2024-11-01", "type": "COURANT"}'
```

## Captures d'écran

### Base de données H2

Pour se connecter à la console H2 : JDBC URL `jdbc:h2:mem:banque`, utilisateur `sa`, mot de passe vide.
On voit bien la table `COMPTE` avec les 3 comptes créés au démarrage.

<img width="1278" height="642" alt="WhatsApp Image 2026-11-02 at 11 42 19" src="https://github.com/user-attachments/assets/151a8cf1-aba0-4b5a-9f5e-4af738f8c8a4" />


### Swagger

L'interface Swagger permet de tester les endpoints directement dans le navigateur.

<img width="1600" height="636" alt="WhatsApp Image 2026-11-02 at 11 45 39" src="https://github.com/user-attachments/assets/7a8eb7c2-c67a-48a9-85c7-17518634d69c" />


### Réponse en XML

En demandant `Accept: application/xml`, l'API renvoie la liste des comptes en XML.

<img width="678" height="302" alt="Capture d&#39;écran 2026-11-02 114019" src="https://github.com/user-attachments/assets/a48257e1-5436-4e6d-8636-c582c72e5dee" />


