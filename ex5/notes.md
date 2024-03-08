# <span style="color:blue">exercice5</span>
<span style="color:green">explication code </span>

a) Pourquoi ce code est vulnérable ?
Le code est vulnérable en raison de l'utilisation de scanf pour lire une chaîne de caractères dans un tableau (buffer) sans spécifier de limite de taille. Cela signifie que l'utilisateur peut entrer plus de caractères que la taille allouée pour buffer, ce qui peut entraîner un débordement de tampon. Dans ce cas, si l'utilisateur entre suffisamment de caractères pour dépasser la taille de buffer, il écrasera les autres données stockées en mémoire, y compris les variables locales et potentiellement le pointeur de retour de la fonction.

![alt text](image.png)

b) État de la pile lors de l'appel à vulnerable_function
La pile contiendra les éléments suivants (hypothétiquement) lors de l'appel à vulnerable_function :


``resultat``
```bash
|      buffer (8 octets)       | password_is_good (4 octets) | EBP (4 octets) | Adresse de retour (4 octets) |
|------------------------------|------------------------------|----------------|-----------------------------|
| [  ][  ][  ][  ][  ][  ][  ]|          (non initialisé)    |      ...       |        (adresse de retour)  |

```

Le contenu de buffer sera rempli par les caractères entrés par l'utilisateur.

c) Comment déclencher l'erreur ?
Vous pouvez déclencher l'erreur en entrant plus de 8 caractères lors de la saisie de la chaîne de caractères. Cela provoquera un dépassement de tampon et écrasera les données situées dans la pile après le tableau buffer, y compris password_is_good, l'adresse de retour et éventuellement d'autres variables.

d) Pour changer la valeur de password_is_good afin d'afficher "Vous avez cassé le MDP!"
Pour changer la valeur de password_is_good et afficher "Vous avez cassé le MDP!", vous devriez entrer suffisamment de caractères pour remplir buffer et écrire sur password_is_good. La valeur ASCII de 'a' est 97. Donc, si vous entrez "aaaaaaaaX" (où 'X' est un caractère quelconque), vous écraserez password_is_good avec 97, ce qui déclenchera la condition if et affichera "Vous avez cassé le MDP!".