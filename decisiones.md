**TRABAJO PRÁCTICO 1**

**1. Configurar tu entorno y preparar tu repositorio**

Hice un fork del repositorio base apretando la opción de Fork arriba a la derecha y lo asocié a mi cuenta, me  quedó la siguiente URL para mi repo: https://github.com/SantiagoTricherri/2025_TP01_RepoBase.git

Para configurar mi identidad usaría los comandos git config --global pero en este caso yo ya la tenía configurada y simplemente verifiqué que todo este bien configurado usando git config --global --list

**2. Desarrollar una funcionalidad**

Para este punto lo que hice primero fue crear una rama separada del main llamada santiago, use esa rama porque hice de cuenta como que yo estaba trabajando en el repo y quería crearme una rama donde guardar mis cambios sin alterar el main.

Luego, lo que hice fue usar dos archivos de prueba llamados archivodeprueba1.txt y archivodeprueba2.txt, a esos archivos los agregue a mi rama santiago usando los siguientes comandos:

Santiago:$ git add archivodeprueba1.txt
Santiago:$ git commit -m "agregado archivodeprueba1.txt a la rama"
[santiago e4c1e73] agregado archivodeprueba1.txt a la rama
 1 file changed, 1 insertion(+)
 create mode 100644 archivodeprueba1.txt

(para el archivo 2 es lo mismo)

Tambien se puede usar el comando git diff main santiago para ver las diferencias actuales entre ambas ramas una vez realizados los cambios.


**3. Corregir un error (simulado) y aplicar el fix**

Para este punto lo que hice fue primero que nada crear un archivo malo.txt que contenía un error ortográfico en mi rama main, luego lo que hice fue crear una rama hotfix para poder solucionar el error del archivo malo ahí. Luego, usé el comando nano para acceder al archivo desde la terminal y ahí corregí el error que tenía. Una vez corregido hice el commit, volví a la rama main e hice un merge con hotfix para traerme el archivo corregido que estaba en hotfix, por último tambien use un comando diff para chequear que los dos archivos malo en el main y en el hotfix sean iguales. Estos son los comandos que usé:

Santiago:$ git checkout main
Cambiado a rama 'main'
Tu rama está actualizada con 'origin/main'.
Santiago:$ echo "este es el archivo que contiene un error ortografico" > malo.txt
Santiago:$ git add malo.txt
Santiago:$ git commit -m "agregado archivo con error ortografico"
[main 2564b9a] agregado archivo con error ortografico
 1 file changed, 1 insertion(+)
 create mode 100644 malo.txt
Santiago:$ git branch hotfix
Santiago:$ git checkout hotfix
Cambiado a rama 'hotfix'
Santiago:$ nano error.txt
Santiago:$ git add error.txt
Santiago:$ git commit -m "corregido error en error.txt"
[hotfix 0a43e52] corregido error en error.txt
 1 file changed, 1 insertion(+)
 create mode 100644 error.txt
Santiago:$ git checkout main
Cambiado a rama 'main'
Tu rama está adelantada a 'origin/main' por 1 commit.
  (usa "git push" para publicar tus commits locales)
Santiago:$ git merge hotfix
Actualizando 2564b9a..0a43e52
Fast-forward
 error.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 error.txt
Santiago:$ git diff main hotfix
Santiago:$

**4. Hace un PR y aceptalo**

Lo que hice en este punto fue desde github ir a la pestaña pull request para desde allí seleccionar el mi repo (mi fork) y las ramas base y compare sobre las que quiero hacer el pull request. Lo que hice en este caso fue poner como rama base al main y como compare a mi rama santiago, de modo que el pull request se realizó desde la rama santiago hacia el main, conteniendo los commits atómicos que había realizado junto con los demas cambios (fue como hacer un merge).

**5. Crear una versión etiquetada**

Para este paso lo primero que tuve que hacer fue sincronizar mi main local con mi main de github ya que no habia pusheado unos commits, lo hice de la siguiente forma:
git push origin main.
Luego, una vez hecho eso ya pude etiquetar la versión del main y subir el tag, lo hice de la siguiente forma:

Santiago:$ git tag -a v1.0 -m "Versión inicial v1.0" 
Santiago:$ git push origin v1.0
Enumerando objetos: 1, listo.
Contando objetos: 100% (1/1), listo.
Escribiendo objetos: 100% (1/1), 175 bytes | 175.00 KiB/s, listo.
Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/SantiagoTricherri/2025_TP01_RepoBase.git
 * [new tag]         v1.0 -> v1.0



**TRABAJO PRÁCTICO 3**


**1. Configuración inicial del proyecto**

- Crear una organización en Azure DevOps

Para crear la organización fui a la pantalla principal de azure devops, y usando el botón create organization cree mi organización, a la cual nombre SantiagoTricherri.

- Crear un proyecto con la metodología ágil que consideres apropiada

 Una vez dentro de mi organización, creé un nuevo proyecto usando el botón New Project, a mi proyecto lo nombré TP3_4 Tricherri y Ojeda y lo creé privado y con la metodologia ágil Scrum.

 
- Configurar los equipos y áreas del proyecto

Para esto, primero que nada fui a project settings, teams, y allí creé dos equipos de trabajo, uno llamado Backend y otro Frontend. Por otro lado para crear las áreas fui dentro de project settings a project configuration, y desde allí creé dos sprints con su respectiva fecha, de modo que el segundo empiece cuando termine el primero


**2. Gestión del trabajo con Azure Boards**

- Crear un Epic que represente una funcionalidad completa

Para esto fui a la sección Boards, Work items, y allí creé un nuevo work item de tipo Epic. Lo nombré **Gestión de Pedidos Online**, que representa la funcionalidad general de permitir a los clientes registrarse, armar un carrito y realizar un pedido en la aplicación.

- Crear 3 User Stories relacionadas con el Epic

Dentro del Epic, en la parte de Related Work, usé la opción Add link, Child, Product Backlog Item, y así fui creando tres PBIs como hijos del Epic. Los llamé:
1. **Registro de usuarios**
2. **Carrito de compras**
3. **Pago en línea**

- Crear 2 Tasks por cada User Story

Luego, abrí cada PBI creado y desde Related Work, con la opción Add link, Child, Task, agregué dos tareas. Por ejemplo, en “Registro de usuarios” creé las tareas **Diseñar UI registro** e **Implementar validación y almacenamiento**. Hice lo mismo para los otros dos PBIs, cada uno con dos tareas correspondientes.

- Crear 2 Bugs de ejemplo

En la misma sección Boards, Work items, creé dos nuevos work items de tipo Bug. Los nombré **Validación de contraseña no bloquea envío** y **Carrito no actualiza el total al quitar producto**, simulando errores que podrían encontrarse en el desarrollo.

- Configurar un Sprint de 2 semanas

Para configurar el Sprint fui a Project Settings → Project Configuration → Iterations y allí creé una nueva iteración llamada **Sprint 1**, con una duración de dos semanas.

- Asignar los work items al Sprint

Finalmente, edité algunos PBI, Task y Bug creado, y en el campo Iteration seleccioné **Sprint 1**, de modo que todos quedaran dentro del primer Sprint y pudieran visualizarse desde Boards.


**3. Control de versiones con Azure Repos**

- Importar o crear un repositorio con código de una aplicación

Para esto entré en la sección **Repos** dentro de mi proyecto. Allí utilicé la opción **New repository** y cree un nuevo respositorio git llamado PruebaEj3.

- Configurar políticas de branch para la rama principal

Dentro de **Repos, Branches**, seleccioné la rama **main** y abrí el menú de **Branch policies**.  
Desde allí configuré las siguientes políticas:  
1. **Requerir Pull Request**: habilité la opción que impide pushear cambios directos a la rama main.  
2. **Mínimo 1 reviewer**: configuré que cada Pull Request necesite al menos una revisión/aprobación antes de poder hacer merge.

- Crear al menos 2 branches de feature

Desde **Repos, Branches** usé la opción **New branch**. Creé dos ramas nuevas a partir de main, con los nombres:  
- `feature/login`  
- `feature/carrito`

- Realizar cambios y crear Pull Requests

Me cambié a cada rama desde la interfaz web de Azure DevOps,  En `feature/login` edité un archivo de ejemplo (README.md) para simular un cambio, y lo guardé en esa rama.  
Luego fui a **Repos, Pull requests**, y con el botón **New Pull Request** abrí un PR desde `feature/login` hacia `main`. El sistema aplicó la política configurada y me pidió al menos 1 revisor. Lo mismo pasaría con la rama `feature/carrito`.  
De esta manera se validó el flujo de trabajo: desarrollo en ramas de feature, revisión obligatoria y posterior integración a main mediante Pull Request.


