Templates
=========

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

Illustrator
-----------

When creating a new template, always use an existing one as reference.
In fact, study a bunch of the existing templates spanning all of our
product categories and subcategories to get an idea of how they need to
be built. Everything from layer names, object names, their order in each
layer, layer color, fill opacity etc. are all important. Julieann can
help considerably with this.

InDesign
--------

As with Illustrator templates, the best way to create a new InDesign
template is to open an existing one to use as a starting point. Try to
pick one for a product that closely resembles the product for which
you're making a template. For the purposes of clarity, I'll call this
the 'old' template. We'll call the one you are trying to create the
'new' template.

*Before doing anything at all*, immediately save the opened template to
the :file:`~\\Documents\\temp\\` directory using the new product number. This
way, the original (old template) will not be altered. At this point, you
are working on a safe copy of the old template (we'll call this the
'temporary copy'), but all of the links (images, InCopy files, etc.) are
still loaded from that old template's location and it is not safe to
alter them. We'll take care of that now.

If there are any InCopy links in the template, now is a good time to
sever those links. To do so, open the :guilabel:`Assignments` panel from
:guilabel:`Window` -> :guilabel:`Editorial` -> :guilabel:`Assignments`. This is where all the
InCopy links in the document are listed. Typically they are under
:guilabel:`Unassigned InCopy Content`, so expand that tree in the panel. The links
with names like :guilabel:`inks` and :guilabel:`header` are safe to leave alone, but the
rest—such as :guilabel:`art` or :guilabel:`ST161Side Art`\ —need to be deleted. Select them
and hit the trashcan icon in the panel. Re-save the document.

Now copy over the artwork from the Illustrator file to the InDesign
document. For the artwork to be copied, it must be on a visible,
unlocked, and non-template layer in Illustrator. In addition, it would
be best of the paths that you are copying have a fill but no stroke.
Otherwise, a stroked path will be pasted in as a compound path where the
stroke has been expanded to become filled. Try it and you'll see what I
mean.

When copying over the product image, it is best to save a transparent
``.png`` of the product and place it (:kbd:`Ctrl` + :kbd:`D`) in the InDesign Document.
If a 'Product Images' layer doesn't already exist at the bottom of the
Layers panel, create it. I usually like to give it a color of Dark
Green, but it doesn't really matter. Place the product image(s) on that
layer. Align and rotate them to the existing product images if you need
to, then delete the old product images. You may need to remove them from
the :guilabel:`Digital Proof`, :guilabel:`Pack Sheet`, and/or :guilabel:`Spec Sheet` layers. Copy them
to any other layers they should be on and then scale them appropriately.
Make note of the scaling values. I typically like to use whole numbers
as much as possible to make this process easier.

Paste in the imprint area onto the 'Art Work (max imprint)' layer and
apply the :guilabel:`Art Frame` Object Style from :guilabel:`Window` -> :guilabel:`Styles` ->
:guilabel:`Object Styles` if it exists. If not, make the imprint area path with
**no** fill and a '**NO PRINT BLACK!**' stroke at **0.5 pt** and using
the **Dotted** stroke style. Lastly, with the path still selected, go to
:guilabel:`Object` -> :guilabel:`Content` -> :guilabel:`Graphic`. Now, if it needs to be on
other layers (e.g., a non-Digital product, or one that has been scaled
on the first page), we need to create an InCopy file of the imprint
area. So before copying it to other layers, right-click on the path and
choose :guilabel:`InCopy` -> :guilabel:`Export to Selection…` from the context menu.
Navigate to the :file:`~\\Documents\\temp\\` folder and save it as :file:`art.icml`. If
the product is two-sided, save it as :file:`art-front.icml` (or :file:`art-back.icml`,
:file:`art-inside.icml`, :file:`art-outside.icml`, etc. Use your judgement). InDesign will
tell you that the document must be saved, which is fine since we're
working on a temporary copy anyway (that's another reason we made one).
Once that's done, *then* you may copy-paste the path to other layers and
scale/rotate/flip as necessary. After pasting it to the output page on a
Tradition or Hi-Speed item, remove the stroke. Be sure to name the path
accordingly; use previous templates as a guide (e.g., :guilabel:`artProof`,
:guilabel:`artProofDuplex`, :guilabel:`artProofBack`, etc.).

When everything looks right, Be sure to type in the name and description
of the Product on all pages. Save the temporary document one more time,
then package it up (:kbd:`Ctrl` + :kbd:`Alt` + :kbd:`Shift` + :kbd:`P`). Use the defaults for the first
two dialogs, then save it that same :file:`~\\Documents\\temp\\` directory with
the name of the product (it should already be filled-in), but without
the :file:`Folder` on the end. This will take a moment. When it's done,
close the document, delete all the temporary files in that temp folder
(The :file:`.indd` temporary copy, any :file:`.png` images, and :file:`.icml` InCopy files),
and move the newly-created package directory to its rightful place in
:file:`C:\\Product Templates (Master)\\`.

Now the product needs to be added to the scripts.
