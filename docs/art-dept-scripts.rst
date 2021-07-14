Art Dept Scripts
================

To handle the Proofing and Output tasks in the Art Department, a Java
desktop program called "Sky Launcher" is run which determines which
script is called as well as handling data in the database.

.. _sky-launcher:

Sky Launcher
------------

`Sky Launcher repo <https://github.com/skyunlimitedinc/sky-launcher>`__

This is the Java program which calls the
:ref:`scripts<indesign-scripts>`. It is written in Java 14 (I think)
and is installed to individual PCs from the IT folder
``Sky Programs``.

It should not be necessary to maintain this further unless a glaring bug
makes itself known or the database is moved. I had planned on eventually
scrapping this in the future in favor of a Node.js app that communicates
with the Adobe apps (using updated UXP versions of the Proof and Output
scripts) through Websockets.

.. _indesign-scripts:

InDesign Scripts
----------------

`Sky ArtDept repo <https://github.com/skyunlimitedinc/sky-artdept>`__

There are two main scripts, :file:`ProofJWin.jsx` and :file:`OutputJWin.jsx`
that handle the Proofing and Output tasks respectively. They are called
by :ref:`Sky Launcher<sky-launcher>` through :file:`Proof.vbs` and
:file:`Output.vbs`. They communicate with :ref:`Acrobat
Scripts<acrobat-scripts>` by way of :file:`CopyFile.vbs`,
:file:`GetCoverInfo.vbs`, :file:`OpenPdf.vbs`, :file:`PrintCsFiles.vbs`,
:file:`TestAndPrint.vbs`, and :file:`UnlockCover.vbs`.

The :file:`logging.jsxinc` is a customized version of a JavaScript library
that allows for logging and is necessary for debugging the scripts. All
logs are stored in :file:`G:\\ArtDept\\Scripts\\sky-artdept\\logs\\` and
sorted by computer, then by date. This is useful for tracking down bugs.
Ask the user to reproduce the problem after they have turned on 'debug
log' in :ref:`Sky Launcher<sky-launcher>`.

.. _acrobat-scripts:

Acrobat Scripts
---------------

`Acrobat Scripts repo <https://github.com/skyunlimitedinc/acrobat>`__

All of the scripts necessary for Acrobat to run the way we need it to
are stored in the :file:`Adobe` IT Directory along with custom
stamps. These are installed during initial PC setup so please reference
the :file:`New-PC-Setup.md` document for more details.

.. _template-making-scripts:

Template-Making Scripts
-----------------------

There are several different scripts that I use to help make downloadable
PDF templates and their associated thumbnails for the American Accents
website. For each of these, please see the GitHub repo for more
instructions on how to use them.

`create-downloadable-standard <https://github.com/skyunlimitedinc/create-downloadable-standard>`__
    Script for creating downloadable PDF files for the American Accents web site.

`create-downloadable-shaped <https://github.com/skyunlimitedinc/create-downloadable-shaped>`__
    Generate downloadable PDF templates for shaped Zünd-cut items for the American Accents web site.

`create-downloadable-zund <https://github.com/skyunlimitedinc/create-downloadable-zund>`__
    Generate downloadable PDF templates for Zünd-cut items.
