# <span style="color:green">exercice7</span>
## <span style="color:white">1. definition thread</span>
` Un thread, également appelé fil d'exécution, est une unité d'exécution léger, plus petit qu'un processus, qui peut être planifié et exécuté par le système d'exploitation. Les threads partagent le même espace d'adressage et les mêmes ressources que le processus parent, ce qui leur permet de partager des données et de communiquer facilement entre eux. Les threads sont utilisés pour exécuter des tâches concurrentielles ou parallèles dans un programme, ce qui permet d'augmenter l'efficacité et d'exploiter pleinement les capacités de multiprocesseurs ou de multicoeurs `

## <span style="color:white">2. definition mutex</span>
``Un mutex, abréviation de "mutual exclusion" (exclusion mutuelle), est un mécanisme de synchronisation utilisé pour garantir que seulement un thread à la fois peut accéder à une ressource partagée ou une section critique d'un programme. Un mutex agit comme un verrou qui peut être verrouillé par un thread pour empêcher d'autres threads d'accéder à la ressource protégée simultanément. Lorsqu'un thread a fini d'utiliser la ressource, il déverrouille le mutex, ce qui permet à d'autres threads d'y accéder. Les mutex sont couramment utilisés pour éviter les conditions de concurrence et garantir la cohérence des données partagées entre plusieurs threads dans un programme multithreadé.``
Voici une explication détaillée du code :

**1. Inclusions de bibliothèques :**

<stdio.h> : Inclusion de la bibliothèque standard pour les opérations d'entrée/sortie.
<unistd.h> : Inclusion de la bibliothèque pour la fonction sleep().
<pthread.h> : Inclusion de la bibliothèque pour la programmation multithread en utilisant des threads POSIX.

**2. Définition des verrous :**

pthread_mutex_t lock1 = PTHREAD_MUTEX_INITIALIZER; : Définition du verrou lock1 avec l'initialiseur statique PTHREAD_MUTEX_INITIALIZER.
pthread_mutex_t lock2 = PTHREAD_MUTEX_INITIALIZER; : Définition du verrou lock2 avec l'initialiseur statique PTHREAD_MUTEX_INITIALIZER.

**Définition des fonctions de threads :**

void *thread1(void *arg) : Cette fonction est exécutée par le premier thread. Elle tente d'acquérir lock2, puis lock1, et libère ensuite les verrous dans l'ordre inverse.
void *thread2(void *arg) : Cette fonction est exécutée par le deuxième thread. Elle tente d'acquérir lock1, puis lock2, et libère ensuite les verrous dans l'ordre inverse.

**Fonction main() :**

Création de deux threads en appelant pthread_create(), chacun exécutant l'une des fonctions de thread définies.
Attente de la fin des threads en utilisant pthread_join().
Le bloc main() se termine.

 ``Ce programme en langage C crée deux threads qui tentent d'acquérir deux verrous dans un ordre différent. Cette situation peut entraîner un blocage mutuel où les threads se bloquent indéfiniment en attendant que l'autre thread libère le verrou qu'il détient. Ce scénario est appelé deadlock.``