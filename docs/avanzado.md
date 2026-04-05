# Nivel avanzado

---

## 7. Funciones

Una funcion es un pedazo de codigo que le pones un nombre y lo puedes usar las veces que quieras. Puede recibir datos y devolver un resultado con `return`. Si no devuelve nada, se pone `void`.

```cpp
#include <iostream>
#include <string>
using namespace std;

int doble(int n) {
    return n * 2;
}

void saludar(string nombre) {
    cout << "Hola " << nombre << ", bienvenido!" << "\n";
}

int main() {
    cout << "El doble de 7 es " << doble(7) << "\n";
    saludar("Carlos");
    return 0;
}
```

---

## 8. Recursion

Una funcion recursiva es una funcion que se llama a si misma. Sirve para problemas donde la solucion depende de una version mas pequena del mismo problema.

La clave es que siempre necesitas un **caso base**: una condicion que haga que la funcion deje de llamarse a si misma. Sin eso, el programa nunca termina.

### Fibonacci

La secuencia de Fibonacci es: 0, 1, 1, 2, 3, 5, 8, 13, 21...

Cada numero es la suma de los dos anteriores. Los primeros dos son fijos: `fibonacci(0) = 0` y `fibonacci(1) = 1`.

```cpp
#include <iostream>
using namespace std;

int fibonacci(int n) {
    // Caso base: los dos primeros numeros son fijos
    if (n == 0) return 0;
    if (n == 1) return 1;

    // Caso recursivo: la suma de los dos anteriores
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    cout << "fibonacci(6) = " << fibonacci(6) << "\n";
    return 0;
}
```

Que pasa cuando llamas `fibonacci(4)`? Mira esta presentacion paso a paso:

<iframe src="../slides/fibonacci.html" width="100%" height="420" style="border: 1px solid #ccc; border-radius: 8px;"></iframe>

!!! tip "🧠 Desafio: ¿notaste algo raro?"

    En la presentacion, `fibonacci(2)` se calculo **dos veces** 🤯. Imagina con numeros mas grandes... `fibonacci(30)` repite millones de calculos!

    Hay una forma mas rapida: **recordar** los resultados que ya calculaste para no repetirlos. Esto se llama **memorizacion** 🗒️.

    ¿Se te ocurre como solucionarlo? 🤔

---

## 9. Structs

Un struct es como inventar tu propio tipo de variable que tiene varios datos adentro. Por ejemplo, un alumno tiene nombre, edad y promedio.

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Alumno {
    string nombre;
    int edad;
    double promedio;
};

int main() {
    Alumno a;
    a.nombre = "Sofia";
    a.edad = 14;
    a.promedio = 6.2;

    cout << a.nombre << " tiene " << a.edad << " anos" << "\n";
    cout << "Promedio: " << a.promedio << "\n";
    return 0;
}
```
