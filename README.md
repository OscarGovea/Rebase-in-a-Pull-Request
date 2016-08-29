#¿Qué es *REBASE*?

Para entender como funciona *REBASE*, necesitamos entender como funciona Git. Un repositorio Git es una estructura de árbol, donde los nodos del árbol son *commits*. He aquí un ejemplo de un repositorio muy simple: tiene cuatro *commits* en la rama principal, y cada uno tiene un ID de *commit* (en este caso a, b, c, y d ). Se dará cuenta de que **d** es actualmente el último *commit* (o la cabeza) de la rama principal.
![alt text](https://github.com/OscarGovea/Rebase-in-a-Pull-Request/blob/master/1.png)


Para este caso, tenemos dos ramas: *master* y *my_branch*. Ambas ramas contienen los *commits a y b*, pero despues se separan: *master* contiene **C y D**, mientras que *my_branch* contiene **E y F**. El commit en **B** se dice que es la base para hacer un **merge**. Se puede ver que *my_branch* se basa en una versión anterior de *master* 

Ahora digamos que *my_branch* ha quedado atras, y que queremos actualizarlo a la última versión de *master*. En otras palabras, queremos que *my_branch* contenga los nodos (*commits*) **C y D**. Una opción sería hacer un **merge**, pero eso causaria que la rama a contener ramas "extranjeras" tuviera conflictos de extracción. En su lugar haremos un **REBASE**. 

![alt text](https://github.com/OscarGovea/Rebase-in-a-Pull-Request/blob/master/2.png)

Cuando se hace un **REBASE**, Git encuentra la base de su rama (en este caso **B**) encuentra todos los *commits* entre esta base y la cabeza (**E y F**) y reinterpreta los *commits* sobre la cabeza de la rama (*master*). Lo que sucede es que Git crea nuevos *commits* que representan como se ven los cambios en la parte superior de la rama *master*, en la imagen, estos *commits*son **E' y F'**. Git tampoco borra sus *commits* sobre las previas: **E y F** siguen sin tocarse y si algo sale mal con el **REBASE** puede volver de nuevo a donde las cosas iban bien.  