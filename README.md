# Curso de C++

Página web interactiva para enseñar C++ a estudiantes. Los ejemplos se pueden editar y ejecutar directamente en el navegador.

**URL**: [nifalconi.github.io/curso-cpp](https://nifalconi.github.io/curso-cpp/)

## Contenido

La página está dividida en cuatro secciones:

| Sección | Temas |
| --- | --- |
| **Básico** | Primer programa, variables, entrada/salida, condicionales, bucles |
| **Medio** | Arreglos (arrays), vectores |
| **Avanzado** | Funciones, recursión (con slides reveal.js de Fibonacci), structs |
| **Glosario** | Referencia rápida de todos los conceptos con ejemplos comentados |
| **Estrategias** | Cómo abordar un problema paso a paso (con diagrama Mermaid) + Ejercicios OCI con ejemplo real (Baldosas, OCI 2024 Regional) |
| **Referencias** | Links a Programación Competitiva UChile, OCI e IOI |

## Tecnologías

| Tecnología | Para qué se usa |
| --- | --- |
| [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) | Generador de sitio estático con tema Material Design |
| [CodeMirror 5](https://codemirror.net/5/) | Editor de código en el navegador con tema Dracula y resaltado de C++ |
| [Wandbox API](https://wandbox.org/) | Compilación y ejecución remota de C++ (gcc-head, C++17) |
| [GitHub Pages](https://pages.github.com/) | Hosting del sitio |
| [GitHub Actions](https://github.com/features/actions) | CI/CD: lint de markdown + build + deploy automático |

## Cómo funciona el editor interactivo

Cada bloque de código C++ en las páginas se convierte automáticamente en un editor editable gracias a `docs/js/cpprunner.js`. El flujo es:

1. Al cargar la página, el script busca todos los bloques `<code>` dentro de `div.highlight`
2. Los reemplaza con un editor CodeMirror (tema Dracula, modo C++ mejorado con keywords de la STL)
3. Si el código usa `cin`, aparece un campo de texto para escribir la entrada
4. Al hacer clic en **Ejecutar**, el código se envía a la API de Wandbox y la salida se muestra abajo
5. Botones adicionales: **Copiar** (al portapapeles) y **Restaurar** (vuelve al código original)

## Estructura del proyecto

```text
docs/
  index.md              # Nivel básico
  medio.md              # Nivel medio
  avanzado.md           # Nivel avanzado
  glosario.md           # Glosario de referencia
  estrategias.md        # Cómo abordar un problema
  ejercicios.md         # Ejercicios OCI: ejemplo real con estrategia de subrayar y anotar
  referencias.md        # Links útiles (UChile, OCI, IOI)
  slides/fibonacci.html # Presentación reveal.js de recursión
  js/cpprunner.js       # Lógica del editor interactivo y conexión con Wandbox
  css/cpprunner.css     # Estilos del editor, toolbar y panel de salida
mkdocs.yml              # Configuración de MkDocs (tema, nav, assets externos)
requirements.txt    # Dependencia de Python: mkdocs-material
.github/workflows/
  pages.yml         # CI: markdownlint -> build -> deploy a GitHub Pages
```

## Requisitos

- **Python 3.10+** — para MkDocs
- **Node.js 18+** — solo si quieres correr el linter de markdown en local

### Paquetes de Python

Definidos en `requirements.txt`:

- `mkdocs-material` — incluye MkDocs, Jinja2, Pygments, pymdown-extensions y todo lo necesario para generar el sitio

### Paquetes de Node (opcionales, solo para linting)

- `markdownlint-cli2` — valida los archivos `.md` antes de pushear

## Desarrollo local

```bash
# 1. Crear entorno virtual de Python (recomendado)
python3 -m venv venv
source venv/bin/activate   # en Windows: venv\Scripts\activate

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Levantar el servidor local
mkdocs serve --livereload
```

La página estará en `http://127.0.0.1:8000/`. El flag `--livereload` hace que el navegador se recargue solo cada vez que guardas un archivo.

### Linter de markdown (opcional)

```bash
npx markdownlint-cli2 "docs/**/*.md"
```

Esto es lo mismo que corre el CI en GitHub Actions. Si hay errores, el deploy no pasa.

## CI/CD

Cada push a `main` ejecuta el workflow de GitHub Actions:

1. **Lint** — Valida los archivos markdown con `markdownlint-cli2`
2. **Build** — Genera el sitio estático con `mkdocs build`
3. **Deploy** — Publica en GitHub Pages
