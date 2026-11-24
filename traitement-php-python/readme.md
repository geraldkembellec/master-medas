# Traitement hybride
## Attention au bug PHP : faille de sécurité `shell_exec()`

| Architecture | Fonctionnement | Usage |
| --- | --- | --- |
|PHP → Python par ligne | PHP appelle Python pour chaque ligne | Prototype, petits volumes |
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
  foreach($matrice as $ligne){}
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
          +---------------+
