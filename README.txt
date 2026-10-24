================================================================================
 PYTHON CRASH COURSE - APUNTES EN JUPYTER NOTEBOOKS
================================================================================

Apuntes personales del libro "Python Crash Course" (3a edicion) de Eric
Matthes. Hay un notebook por capitulo, escritos en espanol,
con los titulos de las secciones en ingles, igual que el libro.

Este repositorio contiene mis apuntes y mis soluciones a los ejercicios.



--------------------------------------------------------------------------------
 2. COMO USAR ESTE PROYECTO
--------------------------------------------------------------------------------

Requisitos: Python 3.10 o superior y VS Code (con las extensiones "Python" y
"Jupyter").

  1) Clonar el repositorio:

         git clone https://github.com/TU_USUARIO/NOMBRE_DEL_REPO.git
         cd NOMBRE_DEL_REPO

  2) Crear y activar un entorno virtual:

         python3 -m venv .venv
         source .venv/bin/activate          (macOS / Linux)
         .venv\Scripts\activate             (Windows)

  3) Instalar lo necesario:

         pip install ipykernel

     Para el capitulo 16 tambien:

         pip install matplotlib plotly

  4) Abrir la carpeta en VS Code, abrir un notebook (.ipynb) y elegir como
     kernel el entorno ".venv".



--------------------------------------------------------------------------------
 PASO 0 - Que subir y que NO subir (leer antes de empezar)
--------------------------------------------------------------------------------

  NO se debe subir:

  .venv/                 234 MB. Es el entorno virtual; cada persona crea el
                         suyo. GitHub rechaza archivos de mas de 100 MB.
  .DS_Store              Basura de macOS.
  .ruff_cache/           Cache de herramientas.
  .vscode/               Configuracion personal del editor (opcional).
  python-crash-course-...pdf
                         El libro completo. Es material con derechos de autor:
                         subirlo a un repositorio publico no esta permitido.
  pcc_3e-main/           65 MB. Son los recursos oficiales del libro (con las
                         soluciones). Es un repositorio ajeno: mejor no copiarlo
                         y poner en el README un enlace a su pagina oficial:
                         https://ehmatthes.github.io/pcc_3e

  SI se debe subir:

  Los notebooks .ipynb, la carpeta weather_data/ y este README.txt.

  Antes de hacer publico el repositorio, revisar que los notebooks no tengan
  texto que no quieras mostrar (nombres, groserias, datos personales).



  Cada vez que escribas mas apuntes:

      git status                          (ver que cambio)
      git add .                           (preparar los cambios)
      git commit -m "Agrega capitulo 7"   (guardar con un mensaje claro)
      git push                            (subir a GitHub)

  Consejos:
    - Hacer commits pequenos y frecuentes (por ejemplo, uno por capitulo).
    - Escribir mensajes que digan que cambio: "Agrega ejercicios del cap. 6".
    - Antes de hacer commit, en cada notebook usar "Restart & Run All" y
      guardar, para que se vea ordenado en GitHub.

--------------------------------------------------------------------------------
 4. SOLUCION DE PROBLEMAS FRECUENTES
--------------------------------------------------------------------------------

  "fatal: remote origin already exists"
      Ya existe un remoto. Cambiarlo con:
          git remote set-url origin URL_CORRECTA

  "remote: Support for password authentication was removed" /
  "Authentication failed"
      Se uso la contrasena de la cuenta. Usar un Personal Access Token
      (Opcion A), GitHub CLI (Opcion B) o SSH (Opcion C).

  "error: failed to push some refs ... (fetch first / non-fast-forward)"
      El repositorio de GitHub no esta vacio (se marco "Add a README" al
      crearlo). Solucion:
          git pull origin main --allow-unrelated-histories
          git push -u origin main
      Si pide un mensaje de merge, guardar y cerrar el editor.

  "this exceeds GitHub's file size limit of 100 MB"
      Se intento subir un archivo grande (por ejemplo .venv). Quitar el
      archivo del seguimiento y rehacer el commit:
          git rm -r --cached .venv
          git commit --amend -m "Apuntes de Python Crash Course"
          git push -u origin main
      (Si ya habia varios commits con el archivo, el mas simple es borrar la
      carpeta .git, ejecutar de nuevo desde el Paso 4 y hacer
      "git push -f origin main" a un repositorio nuevo y vacio.)

  Se subio por error un archivo que no debia (PDF, .DS_Store, etc.)
      Agregarlo al .gitignore y sacarlo del repositorio sin borrarlo del
      disco:
          git rm --cached nombre_del_archivo
          git commit -m "Quita archivo que no debia subirse"
          git push
      Si fue el PDF del libro y el repositorio es publico, hacerlo privado
      (Settings > Danger Zone > Change visibility) y borrar el historial; el
      archivo seguiria visible en commits anteriores.

  "git: command not found"
      Git no esta instalado. Instalarlo desde https://git-scm.com/downloads
      o en macOS con:  xcode-select --install



  Estos apuntes son material personal de estudio.
