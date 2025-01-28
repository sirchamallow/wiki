---
icon: file-code
---

# SQL cheatsheet

## Conventions

Si vous voulez en savoir plus sur SQL, le mieux est de vous rendre sur [SQL.sh](https://sql.sh/) et [LearnSQL](https://learnsql.com/blog/sql-basics-cheat-sheet/)

### snake\_case&#x20;

Le choix entre `camelCase`, `PascalCase` et `snake_case` pour les noms de colonnes en SQL dépend principalement des conventions de votre équipe et du système que vous utilisez.&#x20;

Cependant, la pratique la plus répandue et recommandée est d'utiliser le `snake_case` **pour les noms de colonnes** en SQL.&#x20;

Voici les raisons pour lesquelles le `snake_case` est souvent préféré :

1. Lisibilité : il permet une meilleure lisibilité des noms de colonnes, surtout lorsqu'ils contiennent plusieurs mots.
2. Compatibilité : Certains systèmes de gestion de bases de données sont **sensibles à la casse**, et **le snake\_case évite les problèmes potentiels liés à cette sensibilité.**
3. Cohérence avec les conventions SQL : Les mots-clés SQL sont généralement écrits en majuscules, tandis que les noms de tables et de colonnes sont en minuscules. Ainsi le snake\_case s'intègre bien dans cette convention

Exemple d'utilisation du `snake_case` pour **les noms de colonnes** :

```sql
SELECT 
    user_id, 
    first_name, 
    last_name, 
    date_of_birth
FROM 
    users
WHERE 
    account_status = 'active';
```

