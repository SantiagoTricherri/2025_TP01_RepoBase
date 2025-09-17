# **TRABAJO PRÁCTICO 1**

## **1. Configurar tu entorno y preparar tu repositorio**

Hicimos un fork del repositorio base apretando la opción de Fork arriba a la derecha y lo asociamos a nuestra cuenta. Nos quedó la siguiente URL para nuestro repo:
https://github.com/SantiagoTricherri/2025_TP01_RepoBase.git

Para configurar nuestra identidad usaríamos los comandos git config --global, pero en este caso ya la teníamos configurada y simplemente verificamos que todo esté bien configurado usando git config --global --list.

## **2. Desarrollar una funcionalidad**

Para este punto lo que hicimos primero fue crear una rama separada del main llamada santiago. Usamos esa rama porque simulamos que estábamos trabajando en el repo y queríamos crear una rama donde guardar nuestros cambios sin alterar el main.

Luego, lo que hicimos fue usar dos archivos de prueba llamados archivodeprueba1.txt y archivodeprueba2.txt. A esos archivos los agregamos a nuestra rama santiago usando los siguientes comandos:

Santiago:$ git add archivodeprueba1.txt

Santiago:$ git commit -m "agregado archivodeprueba1.txt a la rama"

[santiago e4c1e73] agregado archivodeprueba1.txt a la rama
 1 file changed, 1 insertion(+)
 create mode 100644 archivodeprueba1.txt

(para el archivo 2 es lo mismo)

Tambien se puede usar el comando git diff main santiago para ver las diferencias actuales entre ambas ramas una vez realizados los cambios.


## **3. Corregir un error (simulado) y aplicar el fix**

Para este punto lo que hicimos fue, primero que nada, crear un archivo malo.txt que contenía un error ortográfico en nuestra rama main. Luego, creamos una rama hotfix para poder solucionar el error allí. Después, usamos el comando nano para acceder al archivo desde la terminal y corregimos el error que tenía.

Una vez corregido hicimos el commit, volvimos a la rama main e hicimos un merge con hotfix para traernos el archivo corregido que estaba en hotfix. Por último, también usamos un comando diff para chequear que los dos archivos malo en el main y en el hotfix fueran iguales.
Al final aplicamos el fix a la rama de santiago también.

Estos son los comandos que usamos:

echo "este es el archvio con eror ortografico" > malo1.txt

git add malo1.txt

git commit -m "feat: agregar malo.txt con error ortográfico"

**Creamos la rama de fix y corregimos EL MISMO archivo**

git checkout -b hotfix

echo "Error ortográfico corregido" > malo1.txt

git add malo1.txt

git commit -m "fix: corregir ortografía en malo1.txt"

**Volvemos a main y traemos el fix**

git checkout main

git merge hotfix

git diff main hotfix

# Aplicamos el fix también a la rama de desarrollo (santiago)

git checkout santiago

git merge main


## **4. Hace un PR y aceptalo**

Lo que hicimos en este punto fue, desde GitHub, ir a la pestaña Pull request para desde allí seleccionar nuestro repo (nuestro fork) y las ramas base y compare sobre las que queríamos hacer el pull request.

En este caso pusimos como rama base al main y como compare a nuestra rama santiago, de modo que el pull request se realizó desde la rama santiago hacia el main, conteniendo los commits atómicos que habíamos realizado junto con los demás cambios (fue como hacer un merge).

## **5. Crear una versión etiquetada**

Para este paso lo primero que tuvimos que hacer fue sincronizar nuestro main local con nuestro main de GitHub ya que no habíamos pusheado unos commits. Lo hicimos de la siguiente forma:
git push origin main

Luego, una vez hecho eso, ya pudimos etiquetar la versión del main y subir el tag. Lo hicimos de la siguiente forma:

Santiago:$ git tag -a v1.0 -m "Versión inicial v1.0" 

Santiago:$ git push origin v1.0

Enumerando objetos: 1, listo.
Contando objetos: 100% (1/1), listo.
Escribiendo objetos: 100% (1/1), 175 bytes | 175.00 KiB/s, listo.
Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/SantiagoTricherri/2025_TP01_RepoBase.git

 * [new tag]         v1.0 -> v1.0

## Uso de IA 

Durante el desarrollo del trabajo práctico utilizamos ChatGPT como herramienta de apoyo. Nos ayudó a comprender conceptos relacionados con Git, aclarar dudas que surgían durante la simulación de branches y merges, y además nos permitió tener a mano los comandos necesarios para realizar las distintas operaciones de forma más clara y ordenada.





