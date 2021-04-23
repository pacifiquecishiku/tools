# tools
Un brouillon qui sert de guide

## Table of contents
- [tools](#tools)
  - [Table of contents](#table-of-contents)
  - [Installer Postman sur Linux mint](#installer-postman-sur-linux-mint)

## Installer Postman sur Linux mint
[Postman](https://www.postman.com/) c'est un outil interresent au developpement, teste et utilisation des apis. Il peut être installer comme un plugin sur le navigateur Chrome mais avec l'application installée sur son bureau, on peut faire bien plus des choses que sur le plugin. Alors, comment installer sur linux? 

1. Télécharger Postman

Postman peut-être téléchargé sur le [site officiel](https://www.postman.com/downloads/) en choisissant la distribution de ton choix.

2. Installation 
   
Aprés avoir téléchargé le fichier __Postman-linux-x*.tar.gz__, il faudras:
* Extraire le fichier *.tar.gz dans le dossier /opt
  ```shell
  $ sudo tar -xvzf Postman-linux-x*.tar.gz -C /opt
  ```
  Aprés ça, tu peut effacer le fichier téléchargé pour liberer la mémoire de ton ordi car t'en auras plus jamais besoin!

  Dans ton dossier /opt/ il y auras un nouveau dossier "Postman" crée et dans le dossier __/opt/Postman/app/__ tu trouveras un fichier nomé __Postman__. Ce fichier, c'est simplement l'executable de Postman pour Linux (Ce serais un équivalent de .exe de Windows). Donc, en faisant double-clic dessus, il vas s'executer normalement. Sauf que tu seras obligé d'aller dans le dossier et faire double-clic sur le fichier pour lancer Postman à chaque fois que t'en auras besoin. Alors, pour simplifier la vie, nous allons configurer une icone pour lancer Postman comme n'importe quel outre application Linux (Via le menu principal).

* Création du lien symbolique
  
  Quand nous aurons notre icone de Postman dans le menu principale, l'icone auras besoin de lancer l'executable __/opt/Postman/app/Postman__. Mais pour ça, il auras besoin d'un lien symbolique dans __/usr/bin/__ pour y arriver. Pour créer le lien, il suffit d'executer le script suivant:
  ```shell
  $ sudo ln -s /opt/Postman/Postman /usr/bin/postman
  ```
  Aprés avoir executer le script, il y auras un nouveau fichier nomé __postman__ dans le dossier __/usr/bin/__. Ce fichier est simplement un lien qui pointe sur le l'executable Postman.

* Création et configuration de l'icone
  
  Une incone d'application Linux est simplement un fichier d'extension __*.desktop__ qui contient certaines informations pour le personaliser et le diferencier des autres applis.

  Il existe plusieurs façons de créer ce fichier. Ici je parlerais d'une façon beaucoup plus simple pour la comprehension à tout les niveau.

  Nous allons utiliser la commande __touch__ pour créer notre icone nommé __postman.desktop__ dans le dossier __/usr/share/applications/__
  ```shell
  $ cd /usr/share/applications/
  $ sudo touch postman.desktop
  ```
  Notre fichier icone a bien été crée. Nous devons maintenant le configurer et pour ça, on peut utiliser n'importe quel editeur de text. Dans mon cas, j'utiliserais l'editeur defaul de mon SO avec la comande __xed__.
  ```shell
  $ sudo xed postman.desktop
  ```
  Notre fichier est ouvert, il suffit juste de copier le contenu suivant:

  ```
  [Desktop Entry]
  Encoding=UTF-8
  Name=Postman
  Exec=postman
  Icon=/opt/Postman/app/resources/app/assets/icon.png
  Terminal=false
  Type=Application
  Categories=Development;
  ```
C'est fait! Tu peut maintenant utiliser postman comme n'importe quelle application Linux à partir du menu principal.