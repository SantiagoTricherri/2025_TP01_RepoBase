**1. Configurar tu entorno y preparar tu repositorio**

Hice un fork del repositorio base apretando la opción de Fork arriba a la derecha y lo asocié a mi cuenta, me  quedó la siguiente URL para mi repo: https://github.com/SantiagoTricherri/2025_TP01_RepoBase.git

Para configurar mi identidad usaría los comandos git config --global pero en este caso yo ya la tenía configurada y simplemente verifiqué que todo este bien configurado usando git config --global --list

**2. Desarrollar una funcionalidad**

Para este punto lo que hice primero fue crear una rama separada del main llamada santiago, use esa rama porque hice de cuenta como que yo estaba trabajando en el repo y quería crearme una rama donde guardar mis cambios sin alterar el main.

Luego, lo que hice fue usar dos archivos de prueba llamados archivodeprueba1.txt y archivodeprueba2.txt, a esos archivos los agregue a mi rama santiago usando los siguientes comandos:

Santiago:~$ git add archivodeprueba1.txt
Santiago:~$ git commit -m "agregado archivodeprueba1.txt a la rama"
[santiago e4c1e73] agregado archivodeprueba1.txt a la rama
 1 file changed, 1 insertion(+)
 create mode 100644 archivodeprueba1.txt

(para el archivo 2 es lo mismo)

Tambien se puede usar el comando git diff main santiago para ver las diferencias actuales entre ambas ramas una vez realizados los cambios.


**3. Corregir un error (simulado) y aplicar el fix**

Para este punto lo que hice fue primero que nada crear un archivo malo.txt que contenía un error ortográfico en mi rama main, luego lo que hice fue crear una rama hotfix para poder solucionar el error del archivo malo ahí. Luego, usé el comando nano para acceder al archivo desde la terminal y ahí corregí el error que tenía. Una vez corregido hice el commit, volví a la rama main e hice un merge con hotfix para traerme el archivo corregido que estaba en hotfix, por último tambien use un comando diff para chequear que los dos archivos malo en el main y en el hotfix sean iguales. Estos son los comandos que usé:

Santiago:~$ git checkout main
Cambiado a rama 'main'
Tu rama está actualizada con 'origin/main'.
Santiago:~$ echo "este es el archivo que contiene un error ortografico" > malo.txt
Santiago:~$ git add malo.txt
Santiago:~$ git commit -m "agregado archivo con error ortografico"
[main 2564b9a] agregado archivo con error ortografico
 1 file changed, 1 insertion(+)
 create mode 100644 malo.txt
Santiago:~$ git branch hotfix
Santiago:~$ git checkout hotfix
Cambiado a rama 'hotfix'
Santiago:~$ nano error.txt
Santiago:~$ git add error.txt
Santiago:~$ git commit -m "corregido error en error.txt"
[hotfix 0a43e52] corregido error en error.txt
 1 file changed, 1 insertion(+)
 create mode 100644 error.txt
Santiago:~$ git checkout main
Cambiado a rama 'main'
Tu rama está adelantada a 'origin/main' por 1 commit.
  (usa "git push" para publicar tus commits locales)
Santiago:~$ git merge hotfix
Actualizando 2564b9a..0a43e52
Fast-forward
 error.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 error.txt
Santiago:~$ git diff main hotfix
Santiago:~$

**4. Hace un PR y aceptalo**

Lo que hice en este punto fue desde github ir a la pestaña pull request para desde allí seleccionar el mi repo (mi fork) y las ramas base y compare sobre las que quiero hacer el pull request. Lo que hice en este caso fue poner como rama base al main y como compare a mi rama santiago, de modo que el pull request se realizó desde la rama santiago hacia el main, conteniendo los commits atómicos que había realizado junto con los demas cambios (fue como hacer un merge).

**5. Crear una versión etiquetada**

Para este paso lo primero que tuve que hacer fue sincronizar mi main local con mi main de github ya que no habia pusheado unos commits, lo hice de la siguiente forma:
git push origin main
Luego, una vez hecho eso ya pude etiquetar la versión del main y subir el tag, lo hice de la siguiente forma:

Santiago:~$ git tag -a v1.0 -m "Versión inicial v1.0" 
Santiago:~$ git push origin v1.0
Enumerando objetos: 1, listo.
Contando objetos: 100% (1/1), listo.
Escribiendo objetos: 100% (1/1), 175 bytes | 175.00 KiB/s, listo.
Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/SantiagoTricherri/2025_TP01_RepoBase.git
 * [new tag]         v1.0 -> v1.0
