Art Dept Scripts
================

To handle the Proofing and Output tasks in the Art Department, a Java
desktop program called "Sky Launcher" is run which determines which
script is called as well as handling data in the database.

Sky Launcher
------------

`Sky Launcher repo <https://github.com/skyunlimitedinc/sky-launcher>`_

This is the Java program which calls the
`scripts <indesign-scripts>`__. It is written in Java 14 (I think)
and is installed to individual PCs from the IT folder
``Sky Programs``.

It should not be necessary to maintain this further unless a glaring bug
makes itself known or the database is moved. I had planned on eventually
scrapping this in the future in favor of a Node.js app that communicates
with the Adobe apps (using updated UXP versions of the Proof and Output
scripts) through Websockets.

InDesign Scripts
----------------

`Sky ArtDept repo <https://github.com/skyunlimitedinc/sky-artdept>`_

There are two main scripts, ``ProofJWin.jsx`` and ``OutputJWin.jsx``
that handle the Proofing and Output tasks respectively. They are called
by `Sky Launcher <sky-launcher>`_ through ``Proof.vbs`` and
``Output.vbs``. They communicate with `Acrobat
Scripts <acrobat-scripts>`_ by way of ``CopyFile.vbs``,
``GetCoverInfo.vbs``, ``OpenPdf.vbs``, ``PrintCsFiles.vbs``,
``TestAndPrint.vbs``, and ``UnlockCover.vbs``.

The ``logging.jsxinc`` is a customized version of a JavaScript library
that allows for logging and is necessary for debugging the scripts. All
logs are stored in ``G:\\ArtDept\\Scripts\\sky-artdept\\logs`` and
sorted by computer, then by date. This is useful for tracking down bugs.
Ask the user to reproduce the problem after they have turned on 'debug
log' in `Sky Launcher <sky-launcher>`_.

Acrobat Scripts
---------------

`Acrobat Scripts repo <https://github.com/skyunlimitedinc/acrobat>`_

All of the scripts necessary for Acrobat to run the way we need it to
are stored in the ``Adobe`` IT Directory along with custom
stamps. These are installed during initial PC setup so please reference
the ``New-PC-Setup.md`` document for more details.

Template-Making Scripts
-----------------------

There are several different scripts that I use to help make downloadable
PDF templates and their associated thumbnails for the American Accents
website. For each of these, please see the GitHub repo for more
instructions on how to use them.

`create-downloadable-standard <https://github.com/skyunlimitedinc/create-downloadable-standard>`_
    Script for creating downloadable PDF files for the American Accents web site.

`create-downloadable-shaped <https://github.com/skyunlimitedinc/create-downloadable-shaped>`_
    Generate downloadable PDF templates for shaped Zünd-cut items for the American Accents web site.

`create-downloadable-zund <https://github.com/skyunlimitedinc/create-downloadable-zund>`_
    Generate downloadable PDF templates for Zünd-cut items.
