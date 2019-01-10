# Paradigmas de programación 
----------------------------

Existen 4 grandes paradigmas: busqueda completa, programación dinámica, enfoque condicioso y 
divide & vencerás. La gran mayoría de los problemas de computer science son solucionables 
eficientemente con alguna combinación de estos paradigmas, disjunta o no.

## Busqueda completa

Este paradigma de busqueda completa se basa, como su nombre lo dice, en realizar una exploración total
sobre la estructura de la solución de un problema. Para ello se procede desde enfoques simples como
_fuerza bruta_, algo más refinado como _backtracking_ hasta métodos heurísticos que involucran conceptos
de inteligencia artificial.

### ejemplo:

sean n enteros, n menor o igual a 1000, en el rango de \[-1000, 1000\]. verificar que existan 4 números a, b, c, d, no
necesariamente distintos, tal que a + b + c = d.

### construyendo una solución eficiente 

#### primera solución

Para dar solución a este problema podemos empezar con una idea simple de fuerza bruta llamada __fijación__. Empezamos fijando
los 4 parametros libres tal que podemos tener algo como:

```cpp
#include <bits/stdc++.h>
using namespace std;
int a[1005];

int main() {
  int n;
  scanf("%d", &n);
  for (int i = 1; i <= n; ++i) {
    scanf("%d", a+i);
  } 
  bool ok = false;  
  for (int i = 1; i <= n; ++i) {
    for (int j = 1; j <= n; ++j) {
      for (int k = 1; k <= n; ++k) { 
        for (int l = 1; l <= n; ++l) {
          ok = ok | (a[i] + a[j] + a[k] == a[l]);
        }}}}
  puts(ok ? "YES" : "NO");
  return 0; 
}
```
Intuitivamente podemos ver que este algoritmo tiene una complejidad de O(n^4). que se traduce en 10000 segundos maquina.

#### segunda solución

Ahora podemos incluir el rango de las variables. Como dice el enunciado las variables están en el rango \[-1000, 1000\], esto es bueno porque puede ser mapeado fácilemente con un array de 2000 elementos, entonces, podriamos reducir la cantidad de variables fijadas a solo 3 y verificar en O(1) que la suma se encuentre.


```cpp
#include <bits/stdc++.h>
using namespace std;
int a[1005];
bool inSet[2005];

int main() {
  int n;
  scanf("%d", &n);
  for (int i = 1; i <= n; ++i) {
    scanf("%d", a+i);
    inSet[a[i] + 1000] = true;
  } 
  bool ok = false;  
  for (int i = 1; i <= n; ++i) {
    for (int j = 1; j <= n; ++j) {
      for (int k = 1; k <= n; ++k) { 
        if (a[i] + a[j] + a[k] < -1000 or a[i] + a[j] + a[k] > 1000) {
          continue;
        }
        ok = ok | inSet[a[i] + a[j] + a[k] + 1000];
      }}}
  puts(ok ? "YES" : "NO");
  return 0; 
}
```

Note que usamos un + 1000 al guardar en el vector. 

Esta solución es mucho mejor con O(n^3). que seria alrededo de 10 segundos máquina.

#### Tercera solución 

Como último, para este problema podemos manipular sutilmente el enunciado, tal que en vez de pedir si existe a + b + c = d podemos pedir a + b = d - c. esto es muy útil ya que para ambos lados de la igualdad solo tenemos una operación entre dos elementos que solo tiene n^2 posibilidades.


```cpp
#include <bits/stdc++.h>
using namespace std;
int a[1005];
bool sum[4005];
bool diff[4005];

int main() {
  int n;
  scanf("%d", &n);
  for (int i = 1; i <= n; ++i) {
    scanf("%d", a+i);
  } 
  for (int i = 1; i <= n; ++i) {
    for (int j = 1; j <= n; ++j) {
      sum[a[i] + a[j] + 2000] = 1;
      diff[a[i] - a[j] + 2000] = 1;
    }
  } 
  bool ok = false;  
  for (int i = 0; i <= 4000; ++i) {
    ok = ok | (sum[i] == diff[i]);
  }
  puts(ok ? "YES" : "NO");
  return 0; 
}
```
Esta es una eficiente solución con fuerza bruta que solo toma O(n^2). Note como hemos cambiado memoria por complejidad.
Para esto definiremos complejidad de memoria como la mayor cantidad de memoria que usas a la vez en un programa.

#### Cuarta solución

No implementaremos esta solución, pero esta solución incluye algo más de conocimientos en teoría de números sobretodo funciones generadoras y algo de cálculo complejo. para ello usaremos la función generadora de un dado P(x) tal que tenga n lados y cada uno tenga a\[i\] puntos. por ultimo la soluci\'on consta de revisar que P(x)^3 y P(x) tengan un coeficiente distintos de 0 a la vez. como hallar P(x)^3 necesitamos saber que para dos polinomos la conv(P x Q) = conv(P) . conv(Q).
Y solo faltaria hacer P x Q = inv(conv(P x Q)) = inv(conv(P) . conv(Q)). y esto se puede hacer con la transformada de fourier rápida en O((n+1000) log (n + 1000)).   

