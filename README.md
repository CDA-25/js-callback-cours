# Les Callbacks en JavaScript

Un **callback** est une **fonction passée en paramètre à une autre fonction**, qui sera **appelée plus tard**,  
souvent après une action (ex: clic, chargement, etc.).

---

## Syntaxe de base

```js
function saluer(nom) {
  console.log("Bonjour, " + nom);
}

function traiterUtilisateur(callback) {
  const nom = "Alice";
  callback(nom); // appel du callback
}

traiterUtilisateur(saluer);
// Affiche : Bonjour, Alice
```

* `saluer` est une fonction callback.
* Elle est passée à `traiterUtilisateur` et exécutée à l’intérieur.

---

## Callback anonyme (fonction directe)

```js
function traiterUtilisateur(callback) {
  const nom = "Alice";
  callback(nom);
}

traiterUtilisateur(function(nom) {
  console.log("Salut, " + nom);
});
```

➡️ Pas besoin de nommer la fonction si elle est utilisée une seule fois.

---

## Exemple courant avec les événements

```js
const btn = document.getElementById("monBtn");

btn.addEventListener("click", function() {
  alert("Tu as cliqué !");
});
```

* `addEventListener` prend un **callback** comme 2ème argument.
* Cette fonction sera exécutée **au moment du clic**.

---

## Avec une fonction flèche

```js
btn.addEventListener("click", () => {
  console.log("Callback avec flèche !");
});
```

➡️ Même principe, mais plus court.

---

## ⚠️ Différence : appeler une fonction VS passer une fonction

```js
// Faux : saluer() est exécuté tout de suite !
btn.addEventListener("click", saluer());

// Correct : on passe la fonction, sans parenthèses
btn.addEventListener("click", saluer);
```

---

## 🔁 Exemple personnalisé

```js
function faireOperation(a, b, operation) {
  const resultat = operation(a, b);
  console.log("Résultat :", resultat);
}

faireOperation(4, 2, function(x, y) {
  return x + y;
});

// Affiche : Résultat : 6
```

➡️ `operation` est un callback. On peut le changer : addition, multiplication, etc.  
on peut faire ce que l'on veut, on sait juste qu'on reçoit deux parametres  
et qu'on peut faire quelque chose avec.  

---

## 🧠 Rappel : à quoi ça sert ?

* Rendre le code plus **flexible**
* **Reporter l’exécution** d’une fonction à plus tard (clic, chargement, etc.)
* Utilisé partout : **événements**, **timers**, **requêtes AJAX**, etc.

---

## ✅ Exemple complet

```html
<button id="demo">Clique moi</button>

<script>
  const btn = document.getElementById("demo");

  function afficherMessage() {
    alert("Message depuis un callback !");
  }

  btn.addEventListener("click", afficherMessage);
</script>
```

---

> Le **callback** est la base de toute la programmation **asynchrone** en JavaScript.

Souvent utilisé avec `setTimeout`, `addEventListener`, ou les `fetch`, etc.

```js
setTimeout(() => {
  console.log("Exécuté après 1 seconde");
}, 1000);

// setTimeout une fonction native à JS, prends un callback en parametre
```

---
