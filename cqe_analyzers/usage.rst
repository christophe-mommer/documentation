Utilisation
===========
Chaque outil fourni dispose de sa propre aide, disponible en appelant l'outil suivi de "-h". 

CQELight_CodeRewriter
^^^^^^^^^^^^^^^^^^^^^
Cet outil s'appelle en ligne de commande `cqe_rewrite [MODE]`. Le mode correspond à ce que l'outil doit réécrire. Les valeurs disponibles sont :
 - `produce` : Réécris les fichiers qui sont producteur d'un message donné pour ajouter l'information sous forme d'attribut sur la classe concernée.

Options de `cqe_rewrite produces [DIR] [OPTIONS]` :
 - `[DIR]` : le répertoire parent dans lequel il faut trouver les fichiers cs. Si non spécifié, le répertoire courant d'exécution sera considéré. Pour chaque fichier cs trouvé, le csproj du projet concerné se verra ajouté une référence vers le package `CQELight_AnalyzersCommon` qui contient les attributs ajoutés.
 - `[OPTIONS]` : possibilité de préciser plusieurs options de fonctionnement :
    - `-no-csproj` : N'ajoute pas le package dans le csproj (peut créer des erreurs de compilations s'il est absent)
    - `-nonuget` : Ne réécris pas (ou ne créé pas s'il n'existe pas) le fichier Nuget.config qui contient le chemin vers le serveur Hybrid Technologies Solutions
    - `-tests` : Réécris également les projets qui sont détectés comme projets de tests unitaires
    - `-ver [VERSION]` : Définis la version du package a ajouté au csproj. Si non précisé, l'outilse chargera de prendre la version la plus appropriée.
    - `-v | --verbose` : Bascule l'outil en mode verbeux permettant d'avoir des traces sur ce qui est fait (à des fins de débug)

CQELight_MapGenerator
^^^^^^^^^^^^^^^^^^^^^
Cet outil s'appelle en ligne de commande `cqe_mapgen [PROJECTS] [OPTIONS]`.
  - `[PROJECTS]` : contient le répertoire dont on veut générer la map (recherche récursive des DLLs présentes à l'intérieur) ou le chemin vers les DLL à traiter
  - `[OPTIONS]` : possibilité de préciser plusieurs options de fonctionnement :
     - `-o [DIR]` : spécifie à le répertoire de sortie
     - `-f [FILTER]` : spécifie un filtre à appliquer lors de la recherche des DLLs. Se comporte comme "contient".
     - `r` : définit si la recherche doit être récursive dans le cas où `[PROJECTS]` est un dossier. Sans effet si `[PROJECTS]` est un fichier.
     - `-v | --verbose` :  Bascule l'outil en mode verbeux permettant d'avoir des traces sur ce qui est fait (à des fins de débug)

CQELight_MapAnalyzer
^^^^^^^^^^^^^^^^^^^^
Cet outil s'appelle en ligne de commande `cqe_mapanalyze [FILE] [OPTIONS]`.
  - `[FILE]` : chemin vers le fichier à analyser. Si non fourni, un fichier appelé "map.json" sera recherché dans le répertoire courant.
  - `[OPTIONS]` : possibilité de préciser plusieurs options de fonctionnement :
     - `-v | --verbose` :  Bascule l'outil en mode verbeux permettant d'avoir des traces sur ce qui est fait (à des fins de débug)
	 
Versions
^^^^^^^^
  - 1.0.0.0 : Version initiale. Recherche dans cycle de communication. 