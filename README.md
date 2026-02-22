# 🧮 Test DAO avec PDO, Logger et Transactions
## Description
Ce projet PHP démontre l’utilisation des DAO (Data Access Object) pour gérer les entités Etudiant et Filiere avec PDO,
tout en intégrant un Logger pour tracer les erreurs et une gestion robuste des transactions.
Le fichier test_dao.php sert de script de test complet pour valider les opérations CRUD et la journalisation.
## Project Structure
```
projet/
├── config/
│   └── db.php
├── logs/
│   └── pdo_errors.log
├── src/
│   ├── Dao/
│   │   ├── EtudiantDao.php
│   │   └── FiliereDao.php
│   ├── Database/
│   │   └── DBConnection.php
│   ├── Entity/
│   │   ├── Etudiant.php
│   │   └── Filiere.php
│   └── Log/
│       └── Logger.php
└── test_dao.php
└── README.md
```
# ⚙️ Features
## 1. Autoloading

- spl_autoload_register pour charger automatiquement les classes du namespace App.

## 2. Logger

- Logger écrit les erreurs dans logs/pdo_errors.log avec horodatage et contexte JSON.

## 3. DBConnection

- Singleton pour gérer la connexion PDO.

- Charge la configuration depuis config/db.php.

- Journalise les erreurs de connexion.

## 4. DAO Étudiant et Filiere

- Méthodes CRUD (insert, update, delete, findById, findAll).

- Gestion des exceptions avec Logger.

## 5. Entités

- Etudiant : attributs id, cne, nom, prenom, email, filiereId avec validation stricte.

- Filiere : attributs id, code, libelle avec validation stricte.

## 6. Script test_dao.php

- Teste toutes les opérations CRUD sur Filiere et Etudiant.

- Provoque une erreur de duplication d’email pour vérifier la journalisation.

- Démonstration de transaction avec commit et rollback.

# 🖥️ Example Execution
- <img width="323" height="146" alt="image" src="https://github.com/user-attachments/assets/507c182b-3576-41d6-8fa1-c8d53529036d" />
- <img width="480" height="504" alt="image" src="https://github.com/user-attachments/assets/ec7105e9-fa6c-47f9-91dc-088f46fcc8a6" />
- <img width="480" height="504" alt="image" src="https://github.com/user-attachments/assets/57a2bde2-5932-4b27-959c-b38768704ba2" />
```php
[2026-02-22 18:27:17] ERREUR: Test error message | context={"x":1}
[2026-02-22 19:39:29] ERREUR: PDO connection failed | context={"method":"App\\Database\\DBConnection::get","dsn":"mysql:host=127.0.0.1;port=3306;dbname=gestion_etudiants_pdo;charset=utf8mb4","error":"could not find driver"}
[2026-02-22 19:39:29] ERREUR: Test error message | context={"x":1}
[2026-02-22 19:44:25] ERREUR: PDO connection failed | context={"method":"App\\Database\\DBConnection::get","dsn":"mysql:host=127.0.0.1;port=3306;dbname=gestion_etudiants_pdo;charset=utf8mb4","error":"could not find driver"}
[2026-02-22 19:44:25] ERREUR: Test error message | context={"x":1}
[2026-02-22 19:53:13] ERREUR: PDO connection failed | context={"method":"App\\Database\\DBConnection::get","dsn":"mysql:host=127.0.0.1;port=3306;dbname=gestion_etudiants_pdo;charset=utf8mb4","error":"could not find driver"}
[2026-02-22 19:53:13] ERREUR: Test error message | context={"x":1}
[2026-02-22 20:58:57] ERREUR: PDO connection failed | context={"method":"App\\Database\\DBConnection::get","dsn":"mysql:host=127.0.0.1;port=3306;dbname=gestion_etudiants_pdo;charset=utf8mb4","error":"SQLSTATE[HY000] [2002] No connection could be made because the target machine actively refused it"}
[2026-02-22 20:58:57] ERREUR: Test error message | context={"x":1}
[2026-02-22 20:59:56] ERREUR: Test error message | context={"x":1}
[2026-02-22 23:04:56] ERREUR: SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry 'alice@example.com' for key 'uq_etudiant_email' | context={"method":"App\\Dao\\EtudiantDao::insert","sql":"INSERT INTO etudiant(cne, nom, prenom, email, filiere_id) VALUES(:cne, :nom, :prenom, :email, :filiere_id)","cne":"CNE1234","email":"alice@example.com"}
[2026-02-22 23:04:56] ERREUR: Transaction rolled back: SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry 'alice@example.com' for key 'uq_etudiant_email' | context={"method":"C:\\xampp\\htdocs\\projet5\\test_dao.php:transaction"}
[2026-02-22 23:07:58] ERREUR: SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry 'alice@example.com' for key 'uq_etudiant_email' | context={"method":"App\\Dao\\EtudiantDao::insert","sql":"INSERT INTO etudiant(cne, nom, prenom, email, filiere_id) VALUES(:cne, :nom, :prenom, :email, :filiere_id)","cne":"CNE8001","email":"alice@example.com"}
```
# 💡 Concepts Practiced

- Architecture DAO avec séparation des responsabilités.

- Utilisation de PDO avec requêtes préparées.

- Gestion des exceptions et journalisation.

- Validation stricte des entités.

- Transactions avec commit et rollback.

# 🧑‍💻 Author

- 👤 Agouram Hassan
- 🏫 Programmation orientée objet et fonctionnelle : PHP
- 🎓 Instructor : Mr. LACHGAR
- 📅 22 février 2026
