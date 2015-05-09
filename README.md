

# Creation du groupe systeme 'pbuilder'

$ sudo addgroup --system pbuilder 
Ajout du groupe « pbuilder » (GID 137)...
Fait.

# Creation de l'utilisateur systeme 'pbuilder'

$ sudo adduser --system --ingroup pbuilder pbuilder
Ajout de l'utilisateur système « pbuilder » (UID 128) ...
Ajout du nouvel utilisateur « pbuilder » (UID 128) avec pour groupe d'appartenance « pbuilder » ...
Création du répertoire personnel `/home/pbuilder'...

# Configuration du sudo

$ printf "%s\n\n%s\t%s\n%s\t%s\n%s\t%s %s\n" "# sudo configuration file for pbuilder" Defaults "env_reset,env_keep='DIST ARCH'" Cmnd_Alias "PBUILDER = /usr/bin/pbuilder /usr/bin/pdebuild /usr/bin/debuild-pbuilder" "%pbuilder" "ALL=(ALL)" PBUILDER |sudo tee /etc/sudoers.d/pbuilder
# sudo configuration file for pbuilder

Defaults	env_reset,env_keep="DIST ARCH"
Cmnd_Alias	PBUILDER = /usr/bin/pbuilder /usr/bin/pdebuild /usr/bin/debuild-pbuilder
%pbuilder	ALL=(ALL) PBUILDER

# Modification des droits du repertoire /home/pbuilder

$ sudo chmod g+s /home/pbuilder/
$ ls -ld /home/pbuilder/
drwxrwsr-x 2 pbuilder pbuilder 6 mai    9 00:06 /home/pbuilder/

# Installation des fichiers de base nécessaires dans /home/pbuilder

$ cd /home/pbuilder/
$ git clone https://github.com/surcouf/pbuilder.git .
Clonage dans '.'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 3
Unpacking objects: 100% (3/3), done.
Vérification de la connectivité... fait.

