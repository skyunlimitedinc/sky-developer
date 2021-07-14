Websites
========

In addition to managing our internal scripts, there are several websites
that must be managed, both private and public.

Since websites do not interact with Adobe products, I work on them
through WSL, so I will be using Linux directory notation. As noted
earlier in this document, all websites are stored locally at
:file:`~/sites/`. This is just a symbolic link to a Windows directory
(:file:`C:\\Users\\christopher.mcgee\\Sites\\`), but as I have said before, I
prefer to work under WSL when I can.

When/if any changes must be made to the AA, ACS, or AYS sites, be aware
that I have a CD pipeline in place. Specifically, I have a GitHub Action
set up on each of them so that they will automatically be uploaded to
their respective live server anytime a :program:`git push` action is performed
on the ``main`` branch of their repos.

.. warning::

    This process is not perfect and
    can lead to website downtime if you are not careful with the changes you
    make to the site.

Be sure to test, test, and test some more before
pushing! If you are at all unsure but need to push anyway, make sure to
add ``[skip ci]`` to the comment of each commit you make. This will skip
the GitHub Action that pushes the code up to the server. Better yet,
create a local branch and do all of your work there and test it before
merging it back into ``main`` and pushing to upstream.

American Accents
----------------

Until the AA WordPress site is fully operational, the old static
HTML/CSS site must be maintained. Although it does have some PHP code to
alleviate a great deal of repetitive code and manual management, it is
still very much outdated and requires careful editing.

The current iteration of the AA site is at :file:`~/sites/aa2021/` so all
subsequent references to directories on the site will be relative to
this location.

Most of the work maintaining the site will be done on the individual
product pages, which can be found under :file:`products/`. Note the method
by which I have used to name most of the products. The naming convention
is as follows:

.. code:: text

    category-subcategory-product[-other_factors…]-print_method.php

There is some variation in this, of course, but almost all products
should follow this general convention. When new products are added, a
good rule of thumb is to just go with your gut instinct after having
viewed the list of existing products.

Splash Images on the Page
~~~~~~~~~~~~~~~~~~~~~~~~~

What I call 'splash images' are the header-like images that are seen at
the top of each product page. They are usually separate pieces that can
be moved around because they are absolutely positioned on the page. To
move them, find their ID selector in the ``<style>`` section of the
``<head>`` of the page and adjust their ``top`` and ``left`` CSS
attributes.

Aggregate Pages
~~~~~~~~~~~~~~~

There are several pages at the root of the site that begin with
``download-``. These aggregate the various downloads from the individual
product pages, such as high-resolution images or templates.

When updating a product's high-res images (printed or blank), templates,
or even compliances, don't forget to also update the same product's
section in the :file:`download-hires-printed.php`,
:file:`download-hires-blank.php`, :file:`download-templates.php`, and
:file:`download-compliances.php` files. Take care to not just copy/paste
without making sure to adjust some PHP variables such as ``$product`` or
``$productLine``.

The other :file:`download-*.php` files are far less likely to need regular
updates.

Images
~~~~~~

The :file:`images/` folder needs to be looked at a bit more closely as it
can be quite confusing.

Before I came along, just about every image the site used was shoved
into this directory without a single thought toward organization. It is
now considerably better, but many vestiges of the old layout persist. I
would not be surprised if many of the older files have already been
replaced with newer versions but we just haven't noticed that yet and
removed the older files. It isn't likely that we will ever bother to
clean these up anymore since we are in the middle of getting our new
WordPress site created which will make this one moot.

Most of the files and directories in :file:`images/` are either
self-explanatory or can be figured out, but a few of them need a little
explanation.

Newest High-Res Images
^^^^^^^^^^^^^^^^^^^^^^

:file:`images/products/` is where all of the individual, high-resolution
product images will go. The bulk of the :file:`.psb` files are here, each
one pertaining to a product and includes images for all print methods as
well as blank versions. The file is set up to take advantage of
PhotoShop's Generator so that all high-res images will be automatically
generated along with every level of thumbnail needed for different
display densities (e.g., retina). The generated files are stored in the
directory of the same name, but with ``-assets`` appended to it. In each
of these assets directories, you will find directories for each of the
print methods and the blank versions, plus a :file:`thumbs/` directory that
contains the thumbnails of each of those high-res images, organized in
the same manner.

The naming convention for the :file:`.psb` files follows the same as that for
the :file:`.php` files in the :file:`products/` directory with the notable
exception of shaped products. Here, including all permutations of a
shaped product's shape and color would make the :file:`.psb` far too
unwieldy. Thus, these files are broken up into shape categories using
the category numbers.

Older High-Res Images
^^^^^^^^^^^^^^^^^^^^^

Before we started going with the :file:`images/products/` method of storing
high-res images, we attempted to store everything in a single
:file:`products.psb` file and, later, a :file:`products-2019.psb` file
containing updates. These also used the same Generator method of, well,
generating the high-res images and their associated thumbnails, but as
you may imagine, those files became far too large to work with
effectively. Nevertheless, many of our images still exist in
:file:`images/products-assets/` because we haven't had time (nor the
motivation) to move them to the newer :file:`images/products/` structure.

Splash Images
^^^^^^^^^^^^^

Our splash images are stored in a single :file:`splash-images.psb` file
under :file:`images/`. Using Generator, the directory
:file:`images/splash-images-assets/` is created which contains all of the
splash images for our individual product pages. The naming convention
roughly follows the same one as above, but is modified slightly to
accommodate the many different splash images that a product page can
contain.

An older directory, :file:`images/SplashImages/`, still exists which
contains some of our older splash images which haven't yet been
converted over to the new method. (Or they already have been converted
but we haven't noticed the duplicates yet.)

Oldest High-Res Images
^^^^^^^^^^^^^^^^^^^^^^

We still have many high-res images stored in :file:`images/hires/` because
they haven't been converted to our newest format yet. The same goes for
their associated thumbnails under :file:`images/thumbnails/`.

PDFs
~~~~

The :file:`pdf/` directory contains all of the downloadable PDF templates
for our products as well as their associated thumbnails. Also here are
the PDF compliances that we acquire from our manufacturers to make
available for download. Much more work has been done here to clean
things up, but some files still remain that have a poor naming
convention.

Also in this :file:`pdf/` root is the main downloadable catalog PDF for the
current year, :file:`2021_American_Accents_Catalog_WEB.pdf`.

Product Templates
^^^^^^^^^^^^^^^^^

Downloadable templates can be found under :file:`pdf/product_templates/`
following our standard naming scheme. A few directories here—\ :file:`Cups`,
:file:`Napkins`, :file:`Plates`, and :file:`Wraps`\ —still utilize an older directory
structure.

The thumbnails for these files can be found under :file:`pdf/thumbnails/`,
predictably, and this directory follows the exact same structure as
:file:`pdf/product_templates/`.

Compliances
^^^^^^^^^^^

Most of the compliances are found in the :file:`pdf/` root using the old,
obscure naming scheme that my predecessor came up with. A few newer
ones, however, can be found in :file:`pdf/compliances/`, using our current
standard naming scheme.

A :file:`compliance_thumbnails.tif` file exists in the :file:`pdf/` root to
create thumbnails for all of our compliances, both new and old. They are
generated in :file:`compliance_thumbnails-assets`, predictably.

Cabin & Yacht
-------------

Sky Schedule
------------

Sky Schedule is a web app running on our local ``SkyUbuntu`` server. It
allows Sky employees to manage our orders. :ref:`Sky
Launcher<sky-launcher>` communicates with the same database that Sky
Schedule uses to keep all of the order info up to date.

It is based on `Laravel 8 <https://laravel.com/>`__ and uses the
`Metronic 5 <https://keenthemes.com/metronic/>`__ admin theme. You
should not need to update it any longer even though it currently has a
minor bug regarding the links to PDFs.

