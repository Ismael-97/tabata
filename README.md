# Tabata
Tabata est un package qui permet la manipulation de séries de signaux numériques.

    tabata
        + notebooks
        |    + opset_doc + instants_doc + tubes_doc + plots_doc
        |    + data
        |         + in (exemple de données)
        |         |   + AFL1EB.h5 (Aircraft FLight 1 Extended & Banalized)
        |         |
        |         + out (données produites par les notebooks
        |    + exercices
        |         + examen - M2 - Stats Descriptives (corrigé)
        + scripts
        |    + pip_intall_all.bat (installation des packages utiles)
        |    + pipupdate.bat
        |    + jupyterlab_plotly_install.bat (plaotly sous jupyterlab)
        + opset.py
        |    + Opset
        |    + OpsetError
        + instants.py
        |    + Selector + indicator()
        + tubes.py
        |    + Tube + highlight() + AppTube
        + plots.py
             + nameunit() + selplot() + byunitplot() + get_colname()
             + groupplot() + doubleplot()

La plupart des analyses de données travaillent sur un tableau de mesures. Pourtant très souvent on a affaire à une liste de signaux. C'est le cas dans l'aéronautique quand on traite une série de vols (ou d'essais) et que chaque vol remonte un tableau de mesures indexé par le temps, souvent à une fréquence moyenne entre 1 Hz et 100 Hz. On a exactement la même chose quand on veut suivre les données d'usinage issues d'une machine-outil. Dans ce second cas, chaque pièce usinée donne un signal de mesures faites par la machine durant l'opération de production.

La première chose à faire quand on dispose de tels listes de signaux et de pouvoir les manipuler et les afficher. L'opset est un raccourci pour "liste d'opérations". Avec l'objet `Opset` il est facile de placer ses signaux stockés dans des DataFrames pandas dans un unique fichier HDF5. L'Opset réfère alors ce fichier et offre des fonctions d'itération et de visualisation.

Le sous-package "instants" contient l'objet `Selector` qui peremt de créer de manière interactive un détecteur d'instants spécifiques. Ce type d'instant correspond à des éléments graphiques visuels qu'un expert est capable d'identifier à l'écran. Le code utilise cet a priori pour construire une règle de décision très simple qui mime le comportement de l'expert.

Le sous-package "tubes" gère les opérations de scoring et de détection de signaux faible à l'aide de tubes de confiances adaptatifs.

**Un notebook spécifique détaille chacun de ces packages.**


Les tubes sont encore très rudimentaires, il reste à faire notamment une estimation des bornes statistiquement robuste à partir de valeurs extrêmes et pouvoir transférer un miodèle de tube sur un signal qui n'a pas servi à l'apprentissage. Je mets la plupart de ces choses "à faire" dans les _issues_.
