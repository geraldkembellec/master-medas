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
          Pour chaque ligne i (ex :```php foreach($matrice as $ligne){}```)
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
