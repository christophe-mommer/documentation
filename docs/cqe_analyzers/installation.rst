Installation
============
Généralités
^^^^^^^^^^^
CQELight Analyzers est une collection d'outils qui analysent le code source produit avec le framework d'entreprise CQELight et fourni un ensemble de résultats. Ces outils sont fournis sous forme de dotnet tool. 

Analyzers
^^^^^^^^^
Messaging Analyzers
-------------------
Ces analyzers vont analyser le code de messaging de votre application pour vérifier un ensemble de choses (par exemple s'il existe une ou plusieurs boucle de message dans votre code). Cette suite d'analyzer est composé de trois outils :
 - CQELight_CodeRewriter
 - CQELight_MapGenerator
 - CQELight_MapAnalyzer

CQELight_CodeRewriter
"""""""""""""""""""""
Cet analyzer va réécrire le code source de vos projets pour y ajouter des annotations (des attributs) qui ne changent rien à l'aspect fonctionnel de votre code. Ces attributs permettent aux outils suivant d'exploiter certaines métadonnées pour générer la carte de messaging la plus précise possible.

CQELight_MapGenerator
"""""""""""""""""""""
Cet analyzer va générer une cartographie du système qui comprends la totalité des messages du système en cours d'analyse (fonctionnement par dossier). Cette carte, au format json, va pouvoir être exploitée pour voir les informations de votre système, comme par exemple quels sont les messages, qui envoie quoi, qui reçoit quoi, etc.

CQELight_MapAnalyzer
""""""""""""""""""""
Cet analyzer va se servir de la carte générée précédemment pour faire une suite de vérifications. Si certaines vérifications sont en erreur (comme par exemple l'existence d'un cycle dans vos communications inter-services), un code de retour d'erreur est renvoyé par l'outil, qui peut être utilisé pour interrompre un processus quelconque.

Plugins compatibles
"""""""""""""""""""
Cette collection d'analyzers se reposent sur les signatures de méthodes de base (`PublishEventAsync`, `DispatchCommandAsync`, etc.) et les types de classes de base (`IDomainEventHandler`, `ICommandHandler`, etc.). A cet effet, le mode de transport n'importe pas, ce sont uniquement les points de terminaisons qui sont considérés.

Installation
""""""""""""
Il est nécessaire d'installer les trois outils cités précédemment grâce à la commande `dotnet tool install --global --add-source https://nuget.hybrid-technologies-solutions.com/` suivie du nom de l'outil. 
Par exemple, pour installer le premier, CQELight_CodeRewriter, il faudra faire la commande suivante : `dotnet tool install --global --add-source https://nuget.hybrid-technologies-solutions.com CQELight_CodeRewriter`. L'installation globale n'est pas obligatoire, mais est recommandée pour analyser tous vos services sans avoir à répéter l'étape d'installation.

Installation de la licence
""""""""""""""""""""""""""
La licence est un fichier .lic qui doit s'appeler `license-CQELight_Analyzers_Collection-app_lNW411PSRQr1.lic`. Il est impératif de ne pas modifier ce nom, car les outils iront chercher exactement ce dernier.
On peut préciser au lancement de l'outil le chemin vers la licence grâce à l'option "---license_path:[PATH]". A défaut de présence de cette option, l'outil ira chercher la licence dans le répertoire local, ou s'il ne la trouve pas :

 - Dans le répertoire "%APPDATA%\\CQELight\\licenses" sous Windows
 - Dans le répertoire "/opt/cqelight/licenses" sous Linux & Mac OS X

Au lancement de l'outil, la phrase "Licence vérifiée" doit s'afficher en vert comme première instruction si vous avez mis la licence dans le bon dossier. Si la licence ne peut pas être vérifiée (absence du fichier, fichier corrompu, etc.), les outils basculent automatiquement sur la version démo.

