## graphs and trees.
 
### conceptos claros
 
* Diseñe un algoritmo para verificar si un grafo es un tree.
 
* Como usarias lo anterior para probar que un *grafo* no tenga ciclos.
 
* Test bipartito: Supongamos que tengo un grafo bipartito e inicio de un nodo
cualesquiera, y voy marcando a los nodos vecinos con colores opuestos (rojo y azul). Cuando 
el algoritmo termina yo se que los nodos pintados de rojo y azul pueden formar un grafo bipartito 
(no necesriamente el mismo que mi grafo inicial). Se puede usar este algoritmo para verificar
que un grafo no es bipartito? Como se usaria?
 
* Note que el test anterior se puede usar para verificar si un grafo no tiene un ciclo impar.
 
* imagina que dado un conjunto S de vertices en un tree y un nodo v del mismo, deseamos
hallar la distancia al nodo mas cercano en S desde el vertice v. solucione esto usando un bfs.
Explique el proceso
 
 
### afianzamiento
 
* Pruebe que un grafo simple, con todos los grados de sus vertices >= 2, contiene
un ciclo simple \(hint: como podrias construir ese ciclo, siempre se forma desde cualquier nodo? \).
 
* Diseñe un algoritmo que encuentre un ciclo simple, con la restriccion de la pregunta 5.
 
* Pruebe que un grafo simple, con todos los grados de sus vertices multiplo de dos,
puede ser particionado en ciclos disjuntos, por aristas \( use hint de 6\).
 
* Use el punto anterior para probar que un *ciclo* euleriano se puede particionar en ciclos
simples \( Algun teorema conocido con ciclos eulerianos? \).
 
 
### intermedio
 
* Cuando mandamos un dfs sobre un grafo genera un arbol inducido. A ese arbol inducido
le llamamos dfs tree, y a las aristas tree - edges.
 
* imagina que dado un conjunto S de vertices en un tree y un conjunto V del mismo, deseamos
hallar las distancias a los nodos mas cercano en S desde cada vertice en V. solucione esto usando un bfs.
Explique el proceos \(hitn1: Como podria ayudar crear un nodo ficticio en este proceso\). 
\(hint2: quizas con distancia -1\). \(hint3: quizas enlazado a los nodos en S o de V?\).
 
### un poco mas claro
 
* Un bridge se define como una arista que al ser eliminada, aumenta la cantidad de componentes del grafo.
(pruebe que al mandar un dfs un bridge solo puede ser un tree-edge).
 
* Pruebe que un grafo que no contenga triangulos \( ciclos simples de orden 3 \) tiene
cantidad de aristas <= floor(n*n/4) \( Primer teorema de teoria extremal de grafos\).
\(hint1: vea que al no existir triangulos la suma de grados de dos vecinos no puede
ser mayor a n\) \(hint2: sume el grado de cada nodo para toda arista existente, luego use la
desigualdad de cauchy\).
 
* De lo anterior de una cota de la cantidad de aristas tal que todo nodo tenga degree <= k.
 
* se define el excentro de un nodo v como el nodo mas alejado a este, y lo denotamos
como ex(v), pruebe que no existe dos nodos a y b en un tree tal que distance(a, b) > distance(ex(ex(v)), ex(v))
para todo nodo v en el tree. (note que distance(ex(ex(v)), ex(v)) es igual al diametro del tree).
 
* pruebe que un tree no puede tener mas de dos centros.
 
* pruebe que un tree no puede tener mas de dos centroides.
 
 
 
(Retome esta seccion cuando crea necesario. No se frustre, esto puede demorar)
 
### avanzado
 
* Usando el lema de la interseccion de conjuntos como puedes contar la cantidad 
de triangulos que tiene un grafo. \(D division 1. Complejidad esperada O\(m sqrt(n)\)\)
 
* Suponamos que tenemos el conjunto de  puntos \(x_i, y_i\) en el plano, y que por cada 
triangulo que se pueda formar con sus aristas paralelas a los ejes tal que sus 3 vertices 
esten en el conjunto; creamos la reflexion de los 3 puntos segun la hipotenusa (estos
puntos pueden servir para generar nuevos puntos). muestre que el resultado despues
de crear todos los puntos posibles se puede ver como la union de grafos bipartitos completos
tal que sus nodos son los x_i y y_i.
 
 
### experto 
 
	The universe is basically an animal. It grazes on the ordinary. It creates 
	infinite idiots just to eat them. Smart people get a chance to climb on top, 
	take reality for a ride, but it will never stop trying to throw you and 
	eventually it will, there’s no other way off. - Rick Sanchez -
 
* del punto anterior concluya que si los puntos tienen coordenadas en el rango [0, n]. y quiero agregar la
menor cantidad de puntos tal que al final obtengo todos los puntos de [0, n] x [0, n]. entonces
esta cantidad es igual la cantidad de componentes que pueda formar con los puntos - 1 (los puntos
son las aristas, vea que tienen que aparecer todos los nodos [0, n] para x_i y [0, n] para y_i) 
 
* oriente las aristas de un grafo simple (en una de las dos posibles direcciones) para
que haya la maxima cantidad de nodos con out degree == in degree (use el lema del apreton de manos).
 
* como puede verificar que existe un ciclo par? (requisitos: dp on trees, greedy and a lot of creativity)
 
