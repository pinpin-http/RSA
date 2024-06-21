# RSA Encryption Module

## Description

Ce projet implémente un module de cryptographie RSA en PHP. Il comprend des scripts pour générer des clés RSA, chiffrer et déchiffrer des messages, ainsi que des fonctions mathématiques nécessaires au fonctionnement de l'algorithme RSA.

## Fichiers

### `RSAmodule.php`

Ce fichier contient les principales fonctions pour le chiffrement et le déchiffrement RSA :

- **Chiffrement** : La fonction `rsa_encrypt($message, $publicKey)` prend un message en texte clair et une clé publique, et retourne le message chiffré.
- **Déchiffrement** : La fonction `rsa_decrypt($encryptedMessage, $privateKey)` prend un message chiffré et une clé privée, et retourne le message en texte clair.

### `keys.php`

Ce fichier gère le chargement des clés RSA à partir de fichiers :

- **Chargement de la clé publique** : La fonction `load_public_key($filename)` charge une clé publique stockée dans un fichier spécifié.
- **Chargement de la clé privée** : La fonction `load_private_key($filename)` charge une clé privée stockée dans un fichier spécifié.

### `genKeys.php`

Ce fichier est utilisé pour générer une paire de clés RSA :

- **Génération des clés** : La fonction `generate_keys($bits)` génère une paire de clés RSA (publique et privée) avec une longueur spécifiée en bits. Les clés générées sont ensuite enregistrées dans des fichiers.

### `RSAmaths.php`

Ce fichier contient les fonctions mathématiques nécessaires pour les opérations RSA :

- **PGCD (Plus Grand Commun Diviseur)** : La fonction `gcd($a, $b)` calcule le plus grand commun diviseur de deux nombres, ce qui est utilisé pour vérifier la coprimalité.
- **Inverse Modulaire** : La fonction `mod_inverse($a, $m)` calcule l'inverse modulaire d'un nombre, ce qui est crucial pour la génération des clés RSA.

## Utilisation Générale

1. **Génération de Clés** :
   - Utilisez `genKeys.php` pour générer une paire de clés. Vous pouvez spécifier la taille des clés en bits.

2. **Chargement de Clés** :
   - Utilisez `keys.php` pour charger les clés générées à partir de fichiers.

3. **Chiffrement et Déchiffrement** :
   - Utilisez `RSAmodule.php` pour chiffrer et déchiffrer des messages avec les clés chargées.

### Exemple de Flux de Travail

1. **Générer une paire de clés** :
   ```php
   include 'genKeys.php';
   generate_keys(2048); // Génère une paire de clés de 2048 bits
   ```
2. **Charger les clés** :
```php
include 'keys.php';
$publicKey = load_public_key('public_key.pem');
$privateKey = load_private_key('private_key.pem');
```
3. **Chiffrer un message** :
```php
include 'RSAmodule.php';
$message = "Hello, world!";
$encryptedMessage = rsa_encrypt($message, $publicKey);
```
4. **Déchiffrer un message** :
```php
$decryptedMessage = rsa_decrypt($encryptedMessage, $privateKey);
echo $decryptedMessage; // Affiche "Hello, world!"

```
