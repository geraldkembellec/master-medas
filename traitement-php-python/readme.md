# Traitement hybride
## Attention au bug PHP d'octobre 2026 : faille de sécurité [`shell_exec()`](https://www.cybermalveillance.gouv.fr/tous-nos-contenus/actualites/alerte-cyber-failles-de-securite-critiques-dans-php-202610)

| Architecture | Fonctionnement | Usage |
| --- | --- | --- |
|PHP → Python par ligne | PHP appelle Python pour chaque ligne avec [`shell_exec()`](https://www.php.net/manual/fr/function.shell-exec.php)| Prototype, petits volumes |
| PHP → Python une seule fois | PHP transmet toute la matrice ; Python effectue les calculs et renvoie les résultats | Interface de visualisation pour moyens et gros volumes |


```text

             FICHIER CSV
                  |
                  v
          +---------------+
          |      PHP      |
          | Lecture CSV   |
          +---------------+
                  |
           Boucle principale
                  |
          Pour chaque ligne i on boucle un traitement en python
```

```php
  foreach($matrice as $ligne){
    // On prépare la commande externe à envoyer à Python
    // C'est à dire comparer la ligne en cours (l'utilisateur), avec la matrice (tous les utilisateurs)
    $command = "echo " . escapeshellarg($ligne,$matrice) . " | python3 Pearson-ligne-matrice.py";
    // on récupère un tableau qui contient toutes les valeurs de corrélations pour tous les autres usagers
    $resultat = shell_exec($command);
  }
```
                  |
                  v
          +---------------+
          |    Python     |
          |               |
          | Ligne i       |
          |      vs       |
          | Toutes les    |
          | autres lignes |
          |               |
          | Calculs       |
          +---------------+
                  |
           Retour des résultats
                  |
                  v
          +---------------+
          |      PHP      |
          | Stockage      |
          | des résultats |
          | et affichage. |
          +---------------+
