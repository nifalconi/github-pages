# Ejercicios OCI

Los problemas de programacion competitiva tienden a ser largos. Esto es a proposito — parte del reto es leer un enunciado extenso, entender que te estan pidiendo, y traducirlo en algo que se pueda programar. Muchas veces la solucion es mas sencilla de lo que parece. Por eso, antes de ver los ejercicios, queremos darte algunos tips extra para enfrentar este tipo de problemas.

## Tips

1. **Lee con atención y ==subraya==.** Lee el problema completo sin apurarte. ==Subraya== o resalta las partes que te parecen clave: qué datos te dan, qué te piden calcular, qué restricciones hay.

2. **Anota las partes importantes.** Después de leer, escribe en tus propias palabras: cuál es la entrada, cuál es la salida, y qué hay que hacer para ir de una a la otra.

3. **Dilo en tus propias palabras.** Intenta explicar el problema como si se lo contaras a un amigo. Si puedes decirlo en una o dos frases simples, ya lo entendiste.

4. **Escribe comentarios antes de programar.** Antes de escribir código, escribe en comentarios los pasos que vas a seguir. Esto te ayuda a ordenar tus ideas y a no perderte.

---

## Ejemplo: un problema real de la OCI

Veamos un problema real de la [Olimpiada Chilena de Informática 2024 — Fase Regional](https://github.com/OCIoficial/2024-10-Regional/tree/main/baldosas). Fíjate en lo largo que es el enunciado... y lo simple que es la solución.

### Paso 1: Leer el enunciado completo

> **Baldosas**
>
> Después de mucho meditarlo, Ana ha decidido postular a la Organización de Cocinas Impecables (OCI). La OCI es muy estricta y pone ciertos requisitos que las cocinas de todos sus miembros deben cumplir. Uno de ellos exige que el piso de la cocina tenga un novedoso patrón de baldosas con estilo de ajedrez. Este patrón consiste en formar una grilla donde se alternan baldosas de color blanco y color negro. Adicionalmente, de acuerdo a la última moda, el cuadrado superior izquierdo siempre debe ser de color blanco.
>
> La cocina de Ana no cumple con el requisito y por lo tanto debe remodelarla. Su cocina es un rectángulo de *n* metros de alto y *m* metros de ancho. Para poder formar el patrón, Ana ha decidido comprar baldosas de 1×1 metros y por lo tanto necesitará un total de *n*×*m* baldosas para cubrir todo su piso.
>
> Ana no quiere desperdiciar material, y por lo tanto desea comprar la cantidad exacta de baldosas que requiere de cada color. La tienda cierra en menos de 4 horas, y no hay tiempo que perder. ¿Podrías ayudarla escribiendo un programa que determine la cantidad exacta de baldosas necesarias de cada color?
>
> **Entrada:** Una línea con dos enteros *n* y *m*.
>
> **Salida:** Una línea con dos enteros *x* e *y*, la cantidad de baldosas blancas y negras respectivamente.

¿Largo, verdad? La historia de Ana, la OCI de cocinas, el ajedrez, la tienda que cierra... Ahora apliquemos las estrategias.

### Paso 2: Subrayar y anotar lo importante

Volvamos a leer, pero esta vez ==resaltando== solo lo que importa:

> Después de mucho meditarlo, Ana ha decidido postular a la Organización de Cocinas Impecables (OCI). La OCI es muy estricta y pone ciertos requisitos que las cocinas de todos sus miembros deben cumplir. Uno de ellos exige que el piso de la cocina tenga un novedoso ==patrón de baldosas con estilo de ajedrez==. Este patrón consiste en formar una ==grilla donde se alternan baldosas de color blanco y color negro==. Adicionalmente, ==el cuadrado superior izquierdo siempre debe ser de color blanco==.
>
> La cocina de Ana no cumple con el requisito y por lo tanto debe remodelarla. Su cocina es un ==rectángulo de *n* metros de alto y *m* metros de ancho==. Para poder formar el patrón, Ana ha decidido comprar ==baldosas de 1×1== metros y por lo tanto necesitará un total de ==*n*×*m* baldosas== para cubrir todo su piso.
>
> Ana no quiere desperdiciar material, y por lo tanto desea comprar la ==cantidad exacta de baldosas que requiere de cada color==.

**Mis notas:**

- Me dan `n` y `m` (alto y ancho).
- Es un tablero de ajedrez: blanco y negro alternados.
- La esquina superior izquierda es blanca.
- Tengo que decir cuántas baldosas blancas y cuántas negras.
- Total de baldosas: `n * m`.

### Paso 3: Decirlo en tus propias palabras

Ahora que ya subrayaste, intenta explicar el problema como si se lo contaras a un amigo:

> *"Me dan un rectángulo de n×m. Tengo que pintar las casillas como tablero de ajedrez (blanco y negro alternados, empezando por blanco). Necesito decir cuántas son blancas y cuántas negras."*

¿Ves? Todo el cuento de Ana, la organización de cocinas, la tienda que cierra... se reduce a eso.

### Paso 4: Escribir comentarios antes de programar

Antes de escribir código, pensemos: en un tablero de ajedrez, si el total de casillas es par, hay exactamente la mitad de cada color. Si es impar, hay una blanca más que negras (porque la primera es blanca).

```cpp
#include <iostream>
using namespace std;

int main() {
    // Leer alto y ancho
    // Calcular total de baldosas
    // Si el total es par: mitad y mitad
    // Si el total es impar: blancas = total/2 + 1, negras = total/2
    // Mostrar blancas y negras
}
```

### Paso 5: Completar el código

```cpp
#include <iostream>
using namespace std;

int main() {
    long long n, m;
    cin >> n >> m;

    long long total = n * m;
    long long blancas = (total + 1) / 2;
    long long negras = total / 2;

    cout << blancas << " " << negras << endl;
    return 0;
}
```

¡Eso es todo! Un enunciado de tres párrafos largos... y la solución son **3 líneas de lógica**. La clave fue ignorar la historia y quedarse con lo esencial.
