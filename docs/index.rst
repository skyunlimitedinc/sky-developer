.. Sky Developer documentation master file, created by
   sphinx-quickstart on Tue Jul 13 15:43:37 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Responsibilities and Instructions for the Developer
===================================================

.. toctree::
   :numbered:
   :maxdepth: 2
   :caption: Contents:

   environments
   art-dept-scripts
   important-directories


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

This document is just a rough outline of the various tasks that the
on-site developer is expected to be able to accomplish. The following
are technologies that the developer must be at least familiar with or
willing to learn:

*  Web Development

   *  HTML
   *  CSS
   *  Sass
   *  Git
   *  GitHub

*  Programming Languages

   *  JavaScript
   *  Adobe ExtendScript
   *  TypeScript
   *  VBScript
   *  PHP
   *  Java

*  Frameworks

   *  Laravel
   *  Bootstrap
   *  JQuery
   *  Swing

*  DevOps

   *  Linux
   *  Docker
   *  Ansible
   *  MySQL
   *  Apache
   *  Nginx
   *  PowerShell
   *  DigitalOcean
   *  WordPress
   *  Plesk

If the candidate does not have the knowledge of any one of the above
technologies, they will need to train in them by watching LinkedIn
Learning videos or by taking online courses.


4. Templates
------------

At the heart of the Proofing and Output processes are the templates
representing our products and their imprint areas. Although an entire
book could be written about this subject, I'll just try to distill our
process of making templates down to the very basics.

When update templates or creating new ones, they must be synchronized to
the file server as well as added to the Proofing/Output scripts. I use
`SyncBackFree <https://www.2brightsparks.com/download-syncbackfree.html>`__
for the file syncing and already have two tasks set up to keep the
templates mirrored onto the server. I highly recommend playing with this
utility and researching what it can do as it is more powerful than it at
first appears.

4.1. Illustrator
~~~~~~~~~~~~~~~~

When creating a new template, always use an existing one as reference.
In fact, study a bunch of the existing templates spanning all of our
product categories and subcategories to get an idea of how they need to
be built. Everything from layer names, object names, their order in each
layer, layer color, fill opacity etc. are all important. Julieann can
help considerably with this.

4.2. InDesign
~~~~~~~~~~~~~

As with Illustrator templates, the best way to create a new InDesign
template is to open an existing one to use as a starting point. Try to
pick one for a product that closely resembles the product for which
you're making a template. For the purposes of clarity, I'll call this
the 'old' template. We'll call the one you are trying to create the
'new' template.

*Before doing anything at all*, immediately save the opened template to
the ``~\Documents\temp\`` directory using the new product number. This
way, the original (old template) will not be altered. At this point, you
are working on a safe copy of the old template (we'll call this the
'temporary copy'), but all of the links (images, InCopy files, etc.) are
still loaded from that old template's location and it is not safe to
alter them. We'll take care of that now.

If there are any InCopy links in the template, now is a good time to
sever those links. To do so, open the 'Assignments' panel from
``Window`` -> ``Editorial`` -> ``Assignments``. This is where all the
InCopy links in the document are listed. Typically they are under
'Unassigned InCopy Content', so expand that tree in the panel. The links
with names like 'inks' and 'header' are safe to leave alone, but the
rest—such as 'art' or 'ST161Side Art'—need to be deleted. Select them
and hit the trashcan icon in the panel. Re-save the document.

Now copy over the artwork from the Illustrator file to the InDesign
document. For the artwork to be copied, it must be on a visible,
unlocked, and non-template layer in Illustrator. In addition, it would
be best of the paths that you are copying have a fill but no stroke.
Otherwise, a stroked path will be pasted in as a compound path where the
stroke has been expanded to become filled. Try it and you'll see what I
mean.

When copying over the product image, it is best to save a transparent
``.png`` of the product and place it (Ctrl+D) in the InDesign Document.
If a 'Product Images' layer doesn't already exist at the bottom of the
Layers panel, create it. I usually like to give it a color of Dark
Green, but it doesn't really matter. Place the product image(s) on that
layer. Align and rotate them to the existing product images if you need
to, then delete the old product images. You may need to remove them from
the 'Digital Proof', 'Pack Sheet', and/or 'Spec Sheet' layers. Copy them
to any other layers they should be on and then scale them appropriately.
Make note of the scaling values. I typically like to use whole numbers
as much as possible to make this process easier.

Paste in the imprint area onto the 'Art Work (max imprint)' layer and
apply the 'Art Frame' Object Style from ``Window`` -> ``Styles`` ->
``Object Styles`` if it exists. If not, make the imprint area path with
**no** fill and a '**NO PRINT BLACK!**\ ' stroke at **0.5 pt** and using
the **Dotted** stroke style. Lastly, with the path still selected, go to
``Object`` -> ``Content`` -> ``Graphic``. Now, if it needs to be on
other layers (e.g., a non-Digital product, or one that has been scaled
on the first page), we need to create an InCopy file of the imprint
area. So before copying it to other layers, right-click on the path and
choose ``InCopy`` -> ``Export to Selection…`` from the context menu.
Navigate to the ``~\Documents\temp\`` folder and save it as ``art``. If
the product is two-sided, save it as ``art-front`` (or ``art-back``,
``art-inside``, ``art-outside``, etc. Use your judgement). InDesign will
tell you that the document must be saved, which is fine since we're
working on a temporary copy anyway (that's another reason we made one).
Once that's done, *then* you may copy-paste the path to other layers and
scale/rotate/flip as necessary. After pasting it to the output page on a
Tradition or Hi-Speed item, remove the stroke. Be sure to name the path
accordingly; use previous templates as a guide (e.g., ``artProof``,
``artProofDuplex``, ``artProofBack``, etc.).

When everything looks right, Be sure to type in the name and description
of the Product on all pages. Save the temporary document one more time,
then package it up (Ctrl+Alt+Shift+P). Use the defaults for the first
two dialogs, then save it that same ``~\Documents\temp\`` directory with
the name of the product (it should already be filled-in), but without
the ``Folder`` on the end. This will take a moment. When it's done,
close the document, delete all the temporary files in that temp folder
(The ``.indd`` temporary copy, any ``.png`` images, and InCopy files),
and move the newly-created package directory to its rightful place in
``C:\Product Templates (Master)\``.

Now the product needs to be added to the scripts.

5. Websites
-----------

In addition to managing our internal scripts, there are several websites
that must be managed, both private and public.

Since websites do not interact with Adobe products, I work on them
through WSL, so I will be using Linux directory notation. As noted
earlier in this document, all websites are stored locally at
``~/sites/``. This is just a symbolic link to a Windows directory
(``C:\Users\christopher.mcgee\Sites``), but as I have said before, I
prefer to work under WSL when I can.

When/if any changes must be made to the AA, ACS, or AYS sites, be aware
that I have a CD pipeline in place. Specifically, I have a GitHub Action
set up on each of them so that they will automatically be uploaded to
their respective live server anytime a ``git push`` action is performed
on the ``main`` branch of their repos. **This process is not perfect and
can lead to website downtime if you are not careful with the changes you
make to the site.** Be sure to test, test, and test some more before
pushing! If you are at all unsure but need to push anyway, make sure to
add ``[skip ci]`` to the comment of each commit you make. This will skip
the GitHub Action that pushes the code up to the server. Better yet,
create a local branch and do all of your work there and test it before
merging it back into ``main`` and pushing to upstream.

5.1. American Accents
~~~~~~~~~~~~~~~~~~~~~

Until the AA WordPress site is fully operational, the old static
HTML/CSS site must be maintained. Although it does have some PHP code to
alleviate a great deal of repetitive code and manual management, it is
still very much outdated and requires careful editing.

The current iteration of the AA site is at ``~/sites/aa2021/`` so all
subsequent references to directories on the site will be relative to
this location.

Most of the work maintaining the site will be done on the individual
product pages, which can be found under ``products/``. Note the method
by which I have used to name most of the products. The naming convention
is as follows:

.. code:: text

    category-subcategory-product[-other_factors…]-print_method.php

There is some variation in this, of course, but almost all products
should follow this general convention. When new products are added, a
good rule of thumb is to just go with your gut instinct after having
viewed the list of existing products.

5.1.1. Splash Images on the Page
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

What I call 'splash images' are the header-like images that are seen at
the top of each product page. They are usually separate pieces that can
be moved around because they are absolutely positioned on the page. To
move them, find their ID selector in the ``<style>`` section of the
``<head>`` of the page and adjust their ``top`` and ``left`` CSS
attributes.

5.1.2. Aggregate Pages
^^^^^^^^^^^^^^^^^^^^^^

There are several pages at the root of the site that begin with
``download-``. These aggregate the various downloads from the individual
product pages, such as high-resolution images or templates.

When updating a product's high-res images (printed or blank), templates,
or even compliances, don't forget to also update the same product's
section in the ``download-hires-printed.php``,
``download-hires-blank.php``, ``download-templates.php``, and
``download-compliances.php`` files. Take care to not just copy/paste
without making sure to adjust some PHP variables such as ``$product`` or
``$productLine``.

The other ``download-*.php`` files are far less likely to need regular
updates.

5.1.3. Images
^^^^^^^^^^^^^

The ``images/`` folder needs to be looked at a bit more closely as it
can be quite confusing.

Before I came along, just about every image the site used was shoved
into this directory without a single thought toward organization. It is
now considerably better, but many vestiges of the old layout persist. I
would not be surprised if many of the older files have already been
replaced with newer versions but we just haven't noticed that yet and
removed the older files. It isn't likely that we will ever bother to
clean these up anymore since we are in the middle of getting our new
WordPress site created which will make this one moot.

Most of the files and directories in ``images/`` are either
self-explanatory or can be figured out, but a few of them need a little
explanation.

5.1.3.1. Newest High-Res Images
'''''''''''''''''''''''''''''''

``images/products/`` is where all of the individual, high-resolution
product images will go. The bulk of the ``.psb`` files are here, each
one pertaining to a product and includes images for all print methods as
well as blank versions. The file is set up to take advantage of
PhotoShop's Generator so that all high-res images will be automatically
generated along with every level of thumbnail needed for different
display densities (e.g., retina). The generated files are stored in the
directory of the same name, but with ``-assets`` appended to it. In each
of these assets directories, you will find directories for each of the
print methods and the blank versions, plus a ``thumbs/`` directory that
contains the thumbnails of each of those high-res images, organized in
the same manner.

The naming convention for the ``.psb``\ s follows the same as that for
the ``.php`` files in the ``products/`` directory with the notable
exception of shaped products. Here, including all permutations of a
shaped product's shape and color would make the ``.psb`` far too
unwieldy. Thus, these files are broken up into shape categories using
the category numbers.

5.1.3.2. Older High-Res Images
''''''''''''''''''''''''''''''

Before we started going with the ``images/products/`` method of storing
high-res images, we attempted to store everything in a single
``products.psb`` file and, later, a ``products-2019.psb`` file
containing updates. These also used the same Generator method of, well,
generating the high-res images and their associated thumbnails, but as
you may imagine, those files became far too large to work with
effectively. Nevertheless, many of our images still exist in
``images/products-assets/`` because we haven't had time (nor the
motivation) to move them to the newer ``images/products/`` structure.

5.1.3.3. Splash Images
''''''''''''''''''''''

Our splash images are stored in a single ``splash-images.psb`` file
under ``images/``. Using Generator, the directory
``images/splash-images-assets/`` is created which contains all of the
splash images for our individual product pages. The naming convention
roughly follows the same one as above, but is modified slightly to
accommodate the many different splash images that a product page can
contain.

An older directory, ``images/SplashImages/``, still exists which
contains some of our older splash images which haven't yet been
converted over to the new method. (Or they already have been converted
but we haven't noticed the duplicates yet.)

5.1.3.4. Oldest High-Res Images
'''''''''''''''''''''''''''''''

We still have many high-res images stored in ``images/hires/`` because
they haven't been converted to our newest format yet. The same goes for
their associated thumbnails under ``images/thumbnails/``.

5.1.4. PDFs
^^^^^^^^^^^

The ``pdf/`` directory contains all of the downloadable PDF templates
for our products as well as their associated thumbnails. Also here are
the PDF compliances that we acquire from our manufacturers to make
available for download. Much more work has been done here to clean
things up, but some files still remain that have a poor naming
convention.

Also in this ``pdf/`` root is the main downloadable catalog PDF for the
current year, ``2021_American_Accents_Catalog_WEB.pdf``.

5.1.4.1. Product Templates
''''''''''''''''''''''''''

Downloadable templates can be found under ``pdf/product_templates/``
following our standard naming scheme. A few directories here—\ ``Cups``,
``Napkins``, ``Plates``, and ``Wraps``—still utilize an older directory
structure.

The thumbnails for these files can be found under ``pdf/thumbnails/``,
predictably, and this directory follows the exact same structure as
``pdf/product_templates/``.

5.1.4.2. Compliances
''''''''''''''''''''

Most of the compliances are found in the ``pdf/`` root using the old,
obscure naming scheme that my predecessor came up with. A few newer
ones, however, can be found in ``pdf/compliances/``, using our current
standard naming scheme.

A ``compliance_thumbnails.tif`` file exists in the ``pdf/`` root to
create thumbnails for all of our compliances, both new and old. They are
generated in ``compliance_thumbnails-assets``, predictably.

5.2. Cabin & Yacht
~~~~~~~~~~~~~~~~~~

5.3. Sky Schedule
~~~~~~~~~~~~~~~~~

Sky Schedule is a web app running on our local ``SkyUbuntu`` server. It
allows Sky employees to manage our orders. `Sky
Launcher <#sky-launcher>`__ communicates with the same database that Sky
Schedule uses to keep all of the order info up to date.

It is based on `Laravel 8 <https://laravel.com/>`__ and uses the
`Metronic 5 <https://keenthemes.com/metronic/>`__ admin theme. You
should not need to update it any longer even though it currently has a
minor bug regarding the links to PDFs.

6. DevOps
---------

There are quite a few servers that need to be managed, both on-site and
in the cloud. This section should help to give an overview of them and
how to manage them.

6.1. IT Directory
~~~~~~~~~~~~~~~~~

+----------------------------+------------------------------------------------------------------------------------------------+
| Directory name             | Description                                                                                    |
+============================+================================================================================================+
| ``Adobe``                  | Contains all the files necessary for initial PC setup. Please see that document for details.   |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Allworx``                | The telephone software, Interact.                                                              |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``BgInfo``                 | Used for displaying info on desktop wallpaper. See the new PC setup guide for details.         |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Certificates``           | SSL certificates for our domains.                                                              |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Driver_*``               | Printer and Video drivers. Most are out of date and unused now.                                |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Eric's Telnet 98``       | Shawn's favorite telnet software.                                                              |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Everything``             | Superior hard drive searching client.                                                          |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Exile``                  | Imagesetter RIP software.                                                                      |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Java``                   | Unused now.                                                                                    |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Link Shell Extension``   | Fantastic software for managing symlinks and hard links.                                       |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Microsoft``              | Just the mouse software for now.                                                               |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Ninite``                 | Outdated software collection for new PCs.                                                      |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``P-touch Editor``         | Mostly for Customer Service. Prints to label printers.                                         |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Powerline Fonts``        | Excellent set of fonts for CLIs.                                                               |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``PuTTY``                  | My favorite telnet software.                                                                   |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``QuickLook``              | Non-Microsoft Store version of the spacebar-preview software.                                  |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``RealVNC``                | The VNC software we use with Cub (PrepCenter) and Caldera (Caldera RIP).                       |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Remote Desktops``        | Outdated list of remote PCs for use with Remote Desktop Client.                                |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Scanner``                | Driver for the Art Department flatbed scanner.                                                 |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Sky Programs``           | Contains "Sky Launcher v5", necessary for all Art Deptartment PCs.                             |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Slack``                  | A signin token to invite new users to our Slack server. Haven't tested.                        |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``SyncBackFree``           | Necessary utility for keeping local and server files in sync.                                  |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``TeamViewer``             | Remote control utility.                                                                        |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``TeraCopy``               | Superior and secure file copying utility.                                                      |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``Wallpapers``             | Installed to the Public folder on new PCs.                                                     |
+----------------------------+------------------------------------------------------------------------------------------------+
| ``ZoomIt``                 | Fantastic, quick screen-drawing tool.                                                          |
+----------------------------+------------------------------------------------------------------------------------------------+

6.2. Ansible
~~~~~~~~~~~~

`repo <https://github.com/skyunlimitedinc/sky-devops>`__

To help manage the servers we have, I use
`Ansible <https://www.ansible.com/>`__. They are all stored in the
``~/devops`` directory on WSL. There are many playbooks in this project
and it can be confusing to follow what does what, so hopefully the
following instructions (along with the project's README.md) will help to
clarify how to use it.

6.2.1. Updating Sites on Staging Server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Although our staging server, **skyubuntu**, is slated to be removed as
soon as possible, it is still being actively used for our `Sky
Schedule <https://github.com/skyunlimitedinc/sky-schedule>`__ app.

There are two kinds of sites/apps on **SkyUbuntu**:

-  Staging servers for testing the new versions of the `American
   Accents <https://github.com/skyunlimitedinc/aa>`__, `American Cabin
   Supply <https://github.com/skyunlimitedinc/acs>`__, and `American
   Yacht Supply <https://github.com/skyunlimitedinc/ays>`__ websites.
-  `Sky Schedule <https://github.com/skyunlimitedinc/sky-schedule>`__
   production app.

Depending on which type of server you want to create/adjust, please
reference `4.2.1.1. Manage Staging
Servers <#4211-manage-staging-servers>`__ and `4.2.1.2. Manage Sky
Schedule <#4212-manage-sky-schedule>`__, below.

If you want to manage *all* of the servers on **SkyUbuntu**, run the
following:

.. code:: bash

    ansible-playbook playbooks/webservers.yml

or

.. code:: bash

    ansible-playbook main.yml

Both will provision all the servers with the necessary dependencies and
run the docker containers necessary to keep the sites/apps running
smoothly. This includes running **HAProxy** to act as a proxy rather
than a load balancer for the sites/apps.

6.2.1.1. Manage Staging Servers
'''''''''''''''''''''''''''''''

To provision and launch the staging sites on SkyUbuntu, run the command

.. code:: bash

    ansible-playbook playbooks/<server_name>.yml

where ``<server_name>`` is either ``acs`` or ``ays`` (for `American
Cabin Supply <https://github.com/skyunlimitedinc/acs>`__ and `American
Yacht Supply <https://github.com/skyunlimitedinc/ays>`__, respectively).

6.2.1.2. Manage Sky Schedule
''''''''''''''''''''''''''''

To provision and launch the Sky Schedule web app on SkyUbuntu, run the
command

.. code:: bash

    ansible-playbook playbooks/schedule.yml

If desired, it is possible to provision and launch all three servers at
once.

.. code:: bash

    ansible-playbook main.yml

This calls ``playbooks/webservers.yml``, which controls all the staging
servers and Sky Schedule at once.

6.2.2. Managing Production Servers on **DigitalOcean**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To provision the production droplets on **DigitalOcean**, run the
command

.. code:: bash

    ansible-playbook do-prep.yml

Please note that this will only create the production droplets, install
the necessary dependencies, and get **Apache** ready for serving the
sites. It *will not* transfer the actual site files to the droplets. For
that, **Github Actions** is set up to watch any pushes to the **main**
branches of their respective repositories and transfer them
automatically to the droplets.

6.2.3. Updating Packages
^^^^^^^^^^^^^^^^^^^^^^^^

As a part of regular maintenance, upgrade the packages and reboot the
servers as necessary with

.. code:: bash

    ansible-playbook update-packages.yml

This will affect all hosts, including **SkyUbuntu**, **localhost**, and
the hosts on DigitalOcean.

6.2.4. Updating the Databases
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you just want to update the databases on the staging server or local
machine, then you'll want to execute the ``db-init.yml`` playbook along
with two variables:

+------------+---------------------------------------------------------------------------------------------------------------------+
| Variable   | Description                                                                                                         |
+============+=====================================================================================================================+
| ``app``    | Defines which application's database you want to copy. Accepted values are ``schedule``, ``acs``, and ``ays``.      |
+------------+---------------------------------------------------------------------------------------------------------------------+
| ``act``    | Defines whether you want to copy the database from staging to local (``get``) or from local to staging (``put``).   |
+------------+---------------------------------------------------------------------------------------------------------------------+

For example, to get a copy of the Sky Schedule database from the staging
server, you would run the playbook like so:

.. code:: bash

    ansible-playbook db-init.yml --extra-vars "app=schedule act=get"

**NOTE:** There seems to be a bug with this playbook. If it fails the
first time, run it again and it should complete successfully the second
time.

6.3. Plesk & WordPress
~~~~~~~~~~~~~~~~~~~~~~

The sign-in credentials for these should be included with the exported
credentials list from 1Password. I highly recommend creating a new user
for the American Accents WordPress site and perhaps even one for Plesk,
to avoid having to use the generic 'admin' login credentials.

Find and follow Plesk and WordPress tutorials and videos online to learn
how to use them as there is far too much to write about here and they
would do a better job than I.

6.4. Databases
~~~~~~~~~~~~~~

We currently use two databases, ``sky`` and ``sky-schedule``. ``sky`` is
used by the American Cabin Supply and American Yacht Supply websites
while ``sky-schedule`` is used solely by Sky Schedule.

6.4.1. ``sky``
^^^^^^^^^^^^^^

This database has not been updated for a couple of years or so and
likely will not need to be updated until Shawn declares that the ACS and
AYS sites need updating. The table structure is far too complex to
describe and explain in detail here, but should the need arise, I can be
contracted to help explain it to anyone who needs to know.

Currently, this db exists on **skyubuntu**, our staging server, to help
us test any changes done to ACS and AYS on an actual server before we
commit them for publishing to the live servers on DigitalOcean. On
**skyubuntu**, it is running in the Docker container ``acsays-db`` and
the data for it is stored in the Docker volume ``acsays-dbdata``.

On **DigitalOcean**, you can find it on the managed database
``db-acsays`` and you can get more information about it from the DO
site.

6.4.2. ``sky-schedule``
^^^^^^^^^^^^^^^^^^^^^^^

The Sky Schedule database is in constant use on the **skyubuntu**
server. The Art Department PCs are always accessing and writing data to
it whenever a Proof or Output job is run. The Production and Customer
Service PCs are accessing it often to check on order statuses as well as
to mark them when complete. Like ``sky``, this db is massively complex
and requires a great deal of explanation to even begin to understand the
table relationships and why ceratin structural choices were made.

This database is currently only being actively used on **skyubuntu**,
but plans were begun to transfer it to **DigitalOcean** shortly before
the end of my tenure. For now, however, **skyubuntu** is the only place
to find it fully working. It's running in a Docker container called
``schedule-db`` and its associated data is in the Docker volume
``schedule-dbdata``.

6.4.3. Logins
^^^^^^^^^^^^^

The login information on **DigitalOcean** can be easily retrieved there
and reset as necessary, but the passwords cannot be modified. On
**skyubuntu**, however, the passwords are very simple because they were
not changed after the initial testing phases of the websites and web
apps.

+-------------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Username          | Password       | Purpose                                                                                                                                                                              |
+===================+================+======================================================================================================================================================================================+
| ``skyadmin``      | ``ncc1701D``   | Administrator. Has effectively the same permissions as the root user of the DBMS, including the ability to manage other users.                                                       |
+-------------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``skyweb``        | ``sky241``     | Daily Usage. This is the main account used to access the database from **Sky Schedule**, **Sky Launcher**, and the DDS machines.                                                     |
+-------------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``skymigrator``   | ``ncc1701``    | **DEPRECATED**. Migration user. Has a few more permissions than ``skyweb``. Used when I was moving db data from MS SQL Server to MySQL using MySQL Workbench. No longer necessary.   |
+-------------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``skylauncher``   | ``sky241``?    | **DEPRECATED**? I think this was just a copy of ``skyweb`` and used with **Sky Launcher**, but I'm pretty sure it isn't used there anymore.                                          |
+-------------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``dds101``        | ``sky241``?    | **DEPRECATED**? I think this was planned for use on the DDS printers in production. Again, I'm pretty sure it isn't used there anymore.                                              |
+-------------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

6.5. PowerShell automations
~~~~~~~~~~~~~~~~~~~~~~~~~~~

In ``C:\Users\christopher.mcgee\Documents`` are a number of ``*.ps1``
files that are used to make it easy to manage the computers at Sky
Unlimited, Inc.

6.5.1. Adobe RUM
^^^^^^^^^^^^^^^^

Sadly, it's not alcoholic. **RUM** is Adobe's updating software,
**Remote Update Manager**. It is automatically installed on any computer
that has at least one piece of Adobe software installed. We use it to
manage when the Adobe apps are updated on the Art Department PCs.

Since it must be run on the machine itself, we use PSTool's ``PsExec``
command to do so. Feel free to research ``PsExec`` to learn how it is
used, but know that I have already created some PowerShell scripts that
call RUM on each individual PC. The format is:

.. code:: powershell

    Adobe-<PC Name>.ps1

Substitute the PC name for ``<PC Name>`` and the specified computer will
automatically download and install any updates to installed Adobe
products. For example, to update the Adobe apps on Aerostar (make sure
to ``cd ~/Documents`` first!):

.. code:: powershell

    Adobe-Aerostar.ps1

If all of the PCs need updating, I created a shortcut for that as well:

.. code:: powershell

    AdobeDownload.ps1

If an update was started on a PC and needs to be killed, open a new
PowerShell instance and run the appropriate "Kill" script. Its format is
very similar to the one used to start an update:

.. code:: powershell

    Adobe-Kill-<PC Name>.ps1

For example, if you need to stop the RUM process on Navajo for whatever
reason:

.. code:: powershell

    Adobe-Kill-Navajo.ps1

6.5.2. End-of-Week Shutdown
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Since we typically shut down all of our Art Department PCs at the end of
every week, there's a command to remotely handle that, as well:
``psshutdown``. Sorry, no script here. This can be left as an exercise
for the new developer. :) As with the Adobe scripts above, make sure to
``cd ~/Documents`` first.

.. code:: powershell

    psshutdown -e p:1:1 -m "Shutting down at the end of the week." -t 16:55 @PCs-ArtDept.txt

Again, it is worthwhile to research the the ``psshutdown`` PowerShell
command to learn how to use it most effectively. The important thing to
know about this command is that it will only shut down those Art
Department PCs that are not currently in use at 4:55 P.M. on the current
day. So it can be run anytime on a Friday.

To manage which computers are shut down by this command, edit the
``PCs-ArtDept.txt`` file in the Documents directory. Likewise, when the
Exile computers (the ones that manage the Exile imagesetters) need to be
shut down at the end of the week, too, run:

.. code:: powershell

    psshutdown -e p:1:1 -m "Shutting down at the end of the week." -t 16:55 @PCs-Exile.txt

7. Contact Me
-------------

When all else fails, you may `email me <chris@chrismcgee.info>`__ and we
can negotiate how I can help. It will likely be in the form of an
hourly-billed training session via phone call or, preferably, a Zoom
call with a remote session.
