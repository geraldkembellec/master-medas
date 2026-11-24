# Traitement hybride
## Attention au bug PHP : faille de sécurité exec()
```ascii

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
          ```php foreach($matrice as $ligne){}```
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
