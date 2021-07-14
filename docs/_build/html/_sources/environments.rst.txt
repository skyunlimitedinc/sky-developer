Environments
============

There are two primary environments in which I do development work:
PowerShell and WSL2. Or, in other words, Windows and Linux.

PowerShell
----------

This is just Windows, really. I use the PowerShell environment for
working on anything that needs to run Adobe scripts, so that's mostly
the :file:`adobe-scripts` folder in :file:`%USERPROFILE%\\Documents\\`.

WSL2
----

`WSL <https://docs.microsoft.com/en-us/windows/wsl/>`__ is Windows
Sub-system for Linux. It is currently at its 2nd iteration which
includes an entire Linux kernel in Windows.

I tend to prefer this environment because Linux is more geared for
developers than Windows. In addition, :ref:`ansible1` doesn't
yet have a Windows executable, so all Ansible playbooks *must* be run
from WSL2.

Git and GitHub
--------------

I have moved the GitHub repos for all of the Sky projects to
`skyunlimitedinc <https://github.com/skyunlimitedinc>`__. However, I
remain the sole contributor to them. Once a new developer has been
established, please `contact me <contact-me.html>`__ and I can add their
GitHub account to those repos.
