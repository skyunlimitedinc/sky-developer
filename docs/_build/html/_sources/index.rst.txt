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
   templates
   websites


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
