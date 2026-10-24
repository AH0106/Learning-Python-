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




--------------------------------------------------------------------------------
 PASO 3 - Crear el archivo .gitignore
--------------------------------------------------------------------------------

  El archivo .gitignore le dice a Git que archivos debe ignorar. Se crea en la
  carpeta del proyecto con este comando (copiar y pegar COMPLETO, es una sola
  instruccion):

      printf '%s\n' '.venv/' 'venv/' '.DS_Store' '.ruff_cache/' '__pycache__/' '*.pyc' '.ipynb_checkpoints/' '.vscode/' '*.pdf' 'pcc_3e-main/' > .gitignore

  Lo que ignora:
      .venv/ y venv/        entornos virtuales
      .DS_Store             basura de macOS
      .ruff_cache/, __pycache__/, *.pyc, .ipynb_checkpoints/
                            caches y archivos temporales
      .vscode/              configuracion personal del editor
      *.pdf                 el libro (derechos de autor)
      pcc_3e-main/          recursos oficiales del libro (otro repositorio)

  Alternativa: en VS Code, crear un archivo nuevo llamado .gitignore, escribir
  cada nombre de la lista anterior en una linea distinta (sin espacios al
  inicio) y guardar.

  Comprobar que se creo bien:

      cat .gitignore

--------------------------------------------------------------------------------
 PASO 4 - Crear el repositorio local con Git
--------------------------------------------------------------------------------

  1. Inicializar Git en la carpeta (la rama principal se llamara "main"):

         git init -b main

  2. Ver que archivos detecta Git:

         git status

     En "Untracked files" deben aparecer los notebooks, weather_data/ y
     README.txt. NO deben aparecer .venv, .DS_Store, el PDF ni pcc_3e-main.
     Si aparece alguno, revisar el .gitignore antes de seguir.

  3. Agregar los archivos al area de preparacion:

         git add .

  4. Revisar que se va a guardar:

         git status

     Todo debe aparecer en verde, bajo "Changes to be committed".

  5. Crear el primer commit (la "foto" inicial del proyecto):

         git commit -m "Apuntes de Python Crash Course: capitulos 2 al 16"

--------------------------------------------------------------------------------
 PASO 5 - Crear el repositorio vacio en GitHub
--------------------------------------------------------------------------------

  1. Entrar a https://github.com e iniciar sesion.
  2. Arriba a la derecha, hacer clic en el "+" y elegir "New repository".
  3. Completar:
       - Repository name: por ejemplo  python-crash-course-notes
         (sin espacios; usar guiones).
       - Description (opcional): "Apuntes del libro Python Crash Course".
       - Public (cualquiera puede verlo) o Private (solo tu). Si dudas,
         elegir Private; despues se puede cambiar en Settings.
       - NO marcar "Add a README file".
       - NO marcar "Add .gitignore".
       - NO elegir una licencia.
     (Se deja todo vacio porque el proyecto ya tiene sus propios archivos;
     si no, el primer "push" dara error por conflicto.)
  4. Hacer clic en "Create repository".
  5. GitHub mostrara una pagina con la URL del repositorio, algo como:

            
          https://github.com/AH0106/Learning-Python-.git


--------------------------------------------------------------------------------
 PASO 6 - Conectar el repositorio local con GitHub
--------------------------------------------------------------------------------

  Reemplazar TU_USUARIO y el nombre del repositorio por los tuyos:

      git remote add origin https://github.com/AH0106/Learning-Python-.git


  Comprobar que quedo conectado:

      git remote -v

  Debe mostrar dos lineas (fetch y push) con la URL.

--------------------------------------------------------------------------------
 PASO 7 - Subir el proyecto (push)
--------------------------------------------------------------------------------

      git push -u origin main

  Git pedira iniciar sesion. IMPORTANTE: GitHub ya NO acepta la contrasena de
  la cuenta al subir por HTTPS. Hay que usar UNA de estas formas:

  OPCION A - Personal Access Token (la mas simple)

    1. En GitHub: foto de perfil > Settings > Developer settings >
       Personal access tokens > Tokens (classic) > Generate new token
       (classic).
    2. Note: "subir apuntes". Expiration: la que prefieras (por ejemplo
       90 dias). Marcar el permiso "repo". Clic en "Generate token".
    3. COPIAR EL TOKEN AHORA (no se vuelve a mostrar).
    4. Al ejecutar "git push", cuando pida:
         Username: tu nombre de usuario de GitHub
         Password: pegar el TOKEN (no la contrasena de la cuenta)
       En macOS, Git guarda el token en el Llavero, asi que solo se pide una
       vez.

      (aqui va tu token; NUNCA lo escribas en un archivo del proyecto)

  Si todo sale bien, la terminal termina con algo como:
      "branch 'main' set up to track 'origin/main'."

--------------------------------------------------------------------------------
 PASO 8 - Verificar en GitHub
--------------------------------------------------------------------------------

  1. Abrir https://github.com/TU_USUARIO/python-crash-course-notes
  2. Comprobar que estan los notebooks, weather_data/ y el README.txt, y que
     NO estan .venv, el PDF ni pcc_3e-main.
  3. Hacer clic en un notebook (.ipynb): GitHub lo muestra renderizado, con
     las tablas y el codigo.

--------------------------------------------------------------------------------
 PASO 9 - Subir cambios en el futuro
--------------------------------------------------------------------------------

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
