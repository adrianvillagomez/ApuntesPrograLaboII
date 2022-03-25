# Pasos para subir un repositorio a GitHub

0.  

    git config --global user.name "John Doe"

    git config --global user.email "johndoe@example.com"

1. inicializar el repositorio: 

        git init

2.  agregar repo remoto:

        git remote add origin URLxxxxxxxxxxxxx

3.  ver estado de archivos: 

        git status

4.  Preparar los archivos para la "fotito":

        git add -A

5. Saco la foto (commit):

        git commit -m "primer commit"

6. ver los commits:

        git log

7. Subir archivos a repo remoto:

        git push -u origin master