# Affectation de matrices en Java

## Question

Peut-on affecter une matrice à une autre en Java avec `mat1 = mat2` ?

## Réponse

En Java, **oui**, vous pouvez écrire `mat1 = mat2`, mais cela effectue une **copie de référence**, pas une copie profonde des données. Les deux variables pointeront vers le **même tableau** en mémoire.

![Java reference vs copy](https://docs.github.com/assets/cb-600/mw-1440/images/help/repository/branching.webp)

### Exemple 1 : Copie de référence (affectation simple)

```java
int[][] mat1 = {{1, 2}, {3, 4}};
int[][] mat2 = mat1; // mat2 pointe vers le même objet que mat1

mat2[0][0] = 99;

System.out.println(mat1[0][0]); // Affiche 99 (mat1 est aussi modifié !)
```

### Exemple 2 : Copie profonde (deep copy) d'une matrice 2D

Pour copier les valeurs sans partager la référence, il faut copier chaque ligne :

```java
int[][] mat1 = {{1, 2}, {3, 4}};
int[][] mat2 = new int[mat1.length][];

for (int i = 0; i < mat1.length; i++) {
    mat2[i] = mat1[i].clone(); // Copie chaque ligne indépendamment
}

mat2[0][0] = 99;

System.out.println(mat1[0][0]); // Affiche 1 (mat1 n'est pas modifié)
```

### Exemple 3 : Utiliser `Arrays.copyOf` pour un tableau 1D

```java
import java.util.Arrays;

int[] arr1 = {1, 2, 3, 4};
int[] arr2 = Arrays.copyOf(arr1, arr1.length);

arr2[0] = 99;
System.out.println(arr1[0]); // Affiche 1 (arr1 n'est pas modifié)
```

## Résumé

| Méthode | Copie les valeurs ? | Indépendant ? |
|---|---|---|
| `mat1 = mat2` | Non (copie de référence) | Non |
| `clone()` sur chaque ligne | Oui | Oui (pour chaque ligne) |
| `Arrays.copyOf` | Oui | Oui (tableau 1D) |

## Liste de vérification

- [x] Comprendre la différence entre copie de référence et copie profonde
- [x] Utiliser `clone()` pour copier les lignes d'une matrice 2D
- [x] Utiliser `Arrays.copyOf()` pour les tableaux 1D
- [ ] Pratiquer avec des exercices sur les tableaux Java
