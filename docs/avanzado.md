# Nivel avanzado

---

## 8. Structs

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
