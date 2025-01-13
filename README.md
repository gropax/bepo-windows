# bepo-windows

Bug :
* XPS17 windows 11 : la touche AltGr+N ne déclenche pas la touche morte. Bizarrement, on peut quand même l'activer
en maintenant Ctrl+Alt tout en tapant **successivement** AltGr puis n.
* En pratique, pour taper seulement `~`, utiliser AltGr+B

## Patcher MSKLC pour binder `_` sur la touche espace
MSKLC refuse de valider une disposition qui associe un caractère non-espace à la barre d'espace. Pour passer outre,
il faut patcher le code en éditant le binaire dans un éditeur hexadécimal. Voir: https://forum.bepo.fr/d/1306-utiliser-microsoft-keyboard-layout-creator-avec-le-fichier-bepo-klc.

Patch qui supprime l’erreur de validation de _ sur la barre d’espace :
- Installer MSKLC (version 1.4.6000.2)
- Ouvrir MSKLC.exe dans un éditeur hexadécimal
- Rechercher la séquence 2D 05 04 2D 02 17 2A 17 0A et remplacer 0A par 2A
- Sauvegarder dans un nouvel exécutable

## Conserver les raccourcis Ctrl azerty
Pour permettre des raccourcis en Ctrl+… différents de la distribution des caractères, il faut éditer manuellement
la colonne `VK_` du fichier `.klc`.

https://web.archive.org/web/20220122064240/http://www.sensefulsolutions.com/2010/08/how-to-fix-keyboard-shortcuts-in-klc-eg.html
