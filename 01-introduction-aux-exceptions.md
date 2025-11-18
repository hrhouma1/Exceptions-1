# 1. C’est quoi une exception ?

En Java, une **exception**, c’est une **erreur qui arrive pendant l’exécution** du programme.

Exemples classiques :

* Division par zéro
* Accès à un index de tableau invalide
* Utilisation d’une variable à `null`
* Fichier introuvable

Si l’exception n’est pas gérée → le programme s’arrête avec un message d’erreur.

<br/>­

# 2. `try` / `catch` : le cœur de la gestion d’exception

On met le code qui peut provoquer une erreur dans un bloc `try`.
Si une erreur arrive, Java exécute le bloc `catch`.

```java
public class TestExceptions {
    public static void main(String[] args) {
        try {
            int a = 10;
            int b = 0;
            int resultat = a / b;   // Erreur ici : division par zéro
            System.out.println(resultat);
        } catch (ArithmeticException e) {
            System.out.println("Erreur : division par zéro.");
        }

        System.out.println("Fin du programme.");
    }
}
```

Idée simple :

* `try` → “j’essaie ce code”
* `catch` → “si ça plante, je réagis ici”

<br/>­

## 3. Exemple avec `NullPointerException`

```java
public class TestNull {
    public static void main(String[] args) {
        String nom = null;

        try {
            System.out.println(nom.length()); // Provoque NullPointerException
        } catch (NullPointerException e) {
            System.out.println("Erreur : la variable 'nom' vaut null.");
        }
    }
}
```

<br/>­

## 4. `finally` : ce qui s’exécute toujours

Le bloc `finally` est optionnel, mais s’exécute **dans tous les cas** :
– qu’il y ait une exception ou non.

```java
public class TestFinally {
    public static void main(String[] args) {
        try {
            int[] tab = {1, 2, 3};
            System.out.println(tab[5]); // Index invalide
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Erreur : index du tableau invalide.");
        } finally {
            System.out.println("Bloc finally exécuté (nettoyage, fermeture, etc.).");
        }
    }
}
```

<br/>­

## 5. Résumé ultra court

* Une **exception** = erreur à l’exécution.
* `try` contient le code “à risque”.
* `catch` gère l’erreur et évite le crash brutal.
* `finally` s’exécute quoi qu’il arrive (facultatif).

Forme générale :

```java
try {
    // Code qui peut provoquer une exception
} catch (TypeException e) {
    // Réaction si erreur
} finally {
    // (Optionnel) Toujours exécuté
}
```

<br/>­

## 6. Exemple à tester soi-même

```java
public class DivisionSafe {
    public static void main(String[] args) {
        int a = 5;
        int b = 0;

        try {
            int resultat = a / b;
            System.out.println("Résultat = " + resultat);
        } catch (ArithmeticException e) {
            System.out.println("On ne peut pas diviser par zéro.");
        }

        System.out.println("Programme terminé.");
    }
}
```
