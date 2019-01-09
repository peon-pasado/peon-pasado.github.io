# Paradigmas de programación 
----------------------------

Existen 4 grandes paradigmas: busqueda completa, programación dinámica, enfoque condicioso y 
divide & vencerás. La gran mayoría de los problemas de computer science son solucionables 
eficientemente con alguna combinación de estos paradigmas, disjunta o no.

# Busqueda completa

Este paradigma de busqueda completa se basa, como su nombre lo dice, en realizar una exploración total
sobre la estructura de la solución de un problema. Para ello se procede desde enfoques simples como
_fuerza bruta_, algo más refinado como _backtracking_ hasta métodos heurísticos que involucran conceptos
de inteligencia artificial.

## ejemplo:

sean n enteros, n menor o igual a 1000, en el rango de \[-1000, 1000\]. verificar que existan 4 números a, b, c, d, no
necesariamente distintos, tal que a + b + c = d.

## construyendo una solución 

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
