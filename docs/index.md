# Referencia rapida de C++

*Tu hoja de ayuda para cuando no te acuerdes como se escribia algo.*

---

## 0. Tu primer programa

Todo programa en C++ arranca con estas tres lineas: `#include <iostream>` para poder mostrar texto y leer datos, `using namespace std;` para no tener que escribir `std::` todo el tiempo, y `int main()` que es donde empieza tu programa.

```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hola mundo!" << "\n";
    return 0;
}
```

---

## 1. Variables

Una variable es un nombre que le pones a un dato para guardarlo y usarlo despues.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int edad = 14;             // numeros enteros
    double nota = 6.5;         // numeros con decimales
    char inicial = 'A';        // un solo caracter (con comillas simples)
    bool aprobado = true;      // verdadero o falso
    string nombre = "Ana";     // texto (con comillas dobles)

    cout << nombre << " tiene " << edad << " anos" << "\n";
    cout << "Su nota es " << nota << "\n";
    cout << "Inicial: " << inicial << "\n";
    cout << "Aprobo? " << aprobado << "\n";
    return 0;
}
```

| Tipo | Para que sirve | Ejemplo |
| --- | --- | --- |
| `int` | Numeros enteros | `int edad = 14;` |
| `double` | Numeros con decimales | `double nota = 6.5;` |
| `char` | Un solo caracter | `char letra = 'A';` |
| `bool` | Verdadero o falso | `bool ok = true;` |
| `string` | Texto | `string nombre = "Ana";` |

> Para usar `string` necesitas agregar `#include <string>` arriba del programa.

---

## 2. Entrada y salida

- `cout` — muestra texto en pantalla. Las flechitas `<<` apuntan hacia afuera (la pantalla).
- `cin` — lee lo que el usuario escribe. Las flechitas `>>` apuntan hacia el computador (la variable) donde se guarda el dato.
- `"\n"` o `endl` — bajan un renglon (salto de linea).

```cpp
#include <iostream>
using namespace std;

int main() {
    int edad;
    cout << "Cuantos anos tienes? ";
    cin >> edad;
    cout << "En 10 anos vas a tener " << edad + 10 << "\n";
    return 0;
}
```

---

## 3. Condicionales

Sirven para que el programa tome decisiones. `if` revisa si algo se cumple, y si es asi hace lo que esta adentro. `else if` revisa otra cosa. `else` es lo que pasa si nada de lo anterior se cumplio.

```cpp
#include <iostream>
using namespace std;

int main() {
    int nota = 85;

    if (nota >= 90) {
        cout << "Excelente!" << "\n";
    } else if (nota >= 70) {
        cout << "Bien hecho" << "\n";
    } else if (nota >= 50) {
        cout << "Aprobado, pero estudia mas" << "\n";
    } else {
        cout << "Reprobado" << "\n";
    }
    return 0;
}
```

Operadores de comparacion:

| Operador | Significa | Ejemplo |
| --- | --- | --- |
| `==` | Es igual a | `x == 5` |
| `!=` | Es distinto de | `x != 0` |
| `<` | Menor que | `x < 10` |
| `>` | Mayor que | `x > 3` |
| `<=` | Menor o igual | `x <= 100` |
| `>=` | Mayor o igual | `x >= 18` |

Puedes combinar condiciones con `&&` (y) y `||` (o):

```cpp
#include <iostream>
using namespace std;

int main() {
    int edad = 15;
    bool tienePermiso = true;

    if (edad >= 13 && tienePermiso) {
        cout << "Puedes entrar" << "\n";
    } else {
        cout << "No puedes entrar" << "\n";
    }
    return 0;
}
```

---

## 4. Bucles

Un bucle repite un bloque de codigo varias veces.

### `for` — cuando sabes cuantas veces repetir

```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; ++i) {
        cout << "Repeticion numero " << i << "\n";
    }
    return 0;
}
```

El `for` tiene tres partes: desde donde arranca (`int i = 1`), hasta cuando sigue (`i <= 5`), y de cuanto en cuanto sube (`++i` significa que sube de a uno).

### `while` — cuando no sabes cuantas veces, pero sabes la condicion

```cpp
#include <iostream>
using namespace std;

int main() {
    int numero = 1;
    while (numero <= 100) {
        numero = numero * 2;
    }
    cout << "El primer numero mayor a 100 duplicando es: " << numero << "\n";
    return 0;
}
```

???+ tip "Ejercicio: Tabla del 7"
    Usa un `for` para mostrar la tabla de multiplicar del 7 (del 1 al 10).

    La salida deberia verse asi:

    ```
    7 x 1 = 7
    7 x 2 = 14
    7 x 3 = 21
    ...
    ```

---

## 5. Funciones

Una funcion es un bloque de codigo con nombre que puedes reutilizar. Le pasas datos (parametros), hace algo, y puede devolver un resultado.

```cpp
#include <iostream>
using namespace std;

int doble(int n) {
    return n * 2;
}

int main() {
    cout << doble(5) << "\n";   // 10
    cout << doble(13) << "\n";  // 26
    return 0;
}
```

Si una funcion no devuelve nada, usas `void`:

```cpp
#include <iostream>
using namespace std;

void saludar(string nombre) {
    cout << "Hola, " << nombre << "!" << "\n";
}

int main() {
    saludar("Carlos");
    saludar("Maria");
    return 0;
}
```

???+ tip "Ejercicio: Es par?"
    Escribe una funcion `esPar` que reciba un `int` y devuelva `true` si es par, `false` si no.

    Pista: un numero es par si el resto de dividirlo por 2 es cero (`n % 2 == 0`).

---

## 6. Arreglos (arrays)

Un arreglo guarda varios datos del mismo tipo, uno al lado del otro. Se accede a cada dato con su posicion (empezando desde 0).

```cpp
#include <iostream>
using namespace std;

int main() {
    int notas[4] = {90, 75, 88, 60};

    cout << "Primera nota: " << notas[0] << "\n";
    cout << "Ultima nota: " << notas[3] << "\n";

    // recorrer el arreglo con for
    for (int i = 0; i < 4; ++i) {
        cout << "Nota " << i + 1 << ": " << notas[i] << "\n";
    }
    return 0;
}
```

> Las posiciones van de `0` a `tamano - 1`. Si tienes 4 elementos, las posiciones son 0, 1, 2 y 3.

???+ tip "Ejercicio: Suma total"
    Tienes un arreglo con 5 numeros. Usa un `for` para sumarlos todos y mostrar el resultado.

    ```cpp
    int datos[5] = {3, 7, 2, 9, 1};
    ```

---

## 7. Strings (texto)

Un `string` es una cadena de caracteres. Puedes unirlos con `+`, ver cuantos caracteres tiene con `.length()`, y acceder a letras individuales con `[ ]`.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string saludo = "Hola";
    string nombre = "Ana";
    string mensaje = saludo + ", " + nombre + "!";

    cout << mensaje << "\n";
    cout << "Tiene " << mensaje.length() << " caracteres" << "\n";
    cout << "Primera letra: " << mensaje[0] << "\n";
    return 0;
}
```

???+ tip "Ejercicio: Contar una letra"
    Pide al usuario una palabra y cuenta cuantas veces aparece la letra 'a'.

    Pista: recorre el string con un `for` y compara cada `palabra[i]` con `'a'`.
