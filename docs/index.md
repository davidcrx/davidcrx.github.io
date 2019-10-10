# Instalación mkdocs con github pages

Proceso de instalación de mkdocss con github pages detallado en un dominio personalizado. 
Este sitio sigue la filosofia del tema "mkdocs-material". Para mas información sobre la plantilla
de este tema: [squidfunk/mkdocs-material](https://github.com/squidfunk/mkdocs-material). 

## Primeros pasos ...

En primer lugar hemos de **crear un repositorio** en github:

    <usuario>.github.io

    Ex: davidcrx.github.io

A partir de ahora github asociará este dominio a una página web. Lo podemos comprobar accediendo a ella.

Ahora nos bajaremos el repositorio para trabajar en local:

    git clone git@github.com:davidcrx/<username>.github.io.git

A continuación crearemos la siguiente estructura de directorios:

    - davidcrx.github.io
    - my-project
        - docs
            - CNAME
            - index.md
        - material
        - src
        - CNAME
        - mkdocs.yml
        - package.json
        - README.md
        - requirements
        - setup.py

Para copiar las carpetas / ficheros que faltan, lo podemos hacer desde [aquí.](https://github.com/squidfunk/mkdocs-material)

Una vez tengamos el directorio montado, ejecutaremos el siguiente comando:

    pip install .

Esto nos va ejecutar el setup.py que va a instalar el tema "material".

Una vez tengamos el tema instalado, vamos a ir a la carpeta *my_project*:

    cd my_project/

A continuación vamos a utilizar el comando *gh-deploy* para lanzar nuestro contenido a *gh-pages*:

    mkdocs gh-deploy --config-file ../my-project/mkdocs.yml --remote-branch master

## Troubleshooting

Si queremos subir nuestro proyecto a la branch "master" tendremos que posteriormente volver a ejecutar el comando anterior.

    git add .

    git commit -m "first mkdocs"

    git push origin master

    cd my-project/ && mkdocs gh-deploy --config-file ../my-project/mkdocs.yml --remote-branch master

## Importante

Recientemente he perdido la estructura /my_project. No pasa absolutamente nada.
Pensaba que cuando subias contenido a github pages también subia el directorio /my_project pero no es así.
Simplemente copiamos los directorios/ficheros que faltan de [aquí](https://github.com/squidfunk/mkdocs-material) y seguimos la estructura mencionada arriba.
He descubierto que el comando único y correcto para subir el contenido a docs.davidcreus.com es este:

    cd my_project/
    mkdocs gh-deploy --config-file ../my-project/mkdocs.yml --remote-branch master

Tenemos que tener en cuenta que dentro del directorio /my-project hemos de inicializar .git

    git init

Y además añadir el repositorio remoto:

    git remote add origin https://github.com/user/repo.git
