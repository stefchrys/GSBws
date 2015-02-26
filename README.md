# GSBws
Procédure d'installation du service Windows GSB à l'aide du code source.

1)Télécharger l'archive complète puis décompresser celle-ci dans votre dossier réservé aux projets C# de Visual Studio 2010.

2)Ouvrir Visual studi0 2010 , puis Fichier/Ouvrir/Projet/ et dans le dossier fraîchement installé ouvrir ServiceGSB.sln, la solution est en place.

3)pour tester l'application il faut ABSOLUMENT être en mode DEBUG . Le mode RELEASE ne peut fonctionner tant que le service n'est pas réellement installé.

Paramètres pour tester l'application en mode DEBBUG :
Il est possible de tester l'application soit sur le serveur distant soit sur le serveur local.
Il suffit de changer les paramètres du fichier MySqlGsb à la ligne 13
Exemple :
private string cs = @"server=localhost;userid=gsb_data;password=motdepasse;database=gsb2";
Remplacer les valeurs pas des valeurs valides.

Le service web mis en place est prévu de fonctionner à l'aide d'un TIMER qui déclenche un événement tout les 24 heures.Pour tester l'application , il est possible de changer la fréquence du TIMER dans le fichier Service1.cs à la ligne 58.
Pour un service qui se déclenche toute les 30 secondes il suffit donc de remplacer la ligne existante par :
timer.Interval = 30000;

Tests Unitaires :
Des tests unitaires sur la classe DateGsb sont disponibles.
Pour ce faire doubleclic sur le fichier ServiceGSB.vsmdi qui se trouve dans SolutionItems qui lui même se trouve dans L'explorateur de solution ServiceGSB.
Selectionner tout les tests, faites un « actualiser » en cliquant sur le petit icône en haut à gauche puis clicdroit sur les tests/Executer tests Activés.

Installation manuelle de la version RELEASE sur un système d'exploitation Windows.

En principe le fichier .exe est existant pas besoin de le recréer.
Il faut donc ouvrir la console Windows en mode Administrateur via le menu de Visual Studio dans le menu demarrer

Ensuite se placer dans le dossier bin/release du projet et ecrire : installutil ServiceGsb.exe


Si tous ce passe bien un message de succès apparaît.Le service est installé , il faut maintenant le déclencher.
Ouvrir le gestionnaire de service et trouver  le service GSBservice.
Attention avant de le lancer s'assurer par un clicdroit dans les propriétés  des autorisations  configurées.
Lancer ensuite le service , il est prêt à fonctionner.

Pour désinstaller le service il suffit de répéter la procédure d'installation en ecrivant :
 installutil /u ServiceGsb.exe.

