============
Installation
============

VirtualMicroscope is `hosted on GitHub <https://github.com/evildmp/VirtualMicroscope>`_.

To install::

    git clone -b hackday git@github.com:evildmp/VirtualMicroscope.git  # use the hackday branch
    cd VirtualMicroscope
    virtualenv env  # create a virtual environment
    source env/bin/activate  # activate it
    pip install -e .  # run setup.py and install required components


*******************
Set up the database
*******************

This repository includes demo images and a database in JSON format, so we'll use those to get
started.

Create your local database, and import the serialised JSON data::

    python manage.py syncdb --noinput  # noinput will prevent it asking for superuser details
    python manage.py loaddata example_database.json
    python manage.py runserver

Assuming you're running on localhost on port 8000, visit ``http://localhost:8000/admin/`` and
login::

    ``username``: *vm*
    ``pasword``: *vm*

*****************
View a demo image
*****************

Visit ``http://localhost:8000/virtualmicroscope``. From *Collections*, choose *Demo images*, then
select *Hackday people*.

And that's it - now you can zoom in and out on people at the HackDay event; our team's the one
at the bottom right.

*****************
Add a tiled image
*****************

We've included a second tiled image, but you need to add this yourself. That image has been
tiled for you already, and is to be found in ``virtualmicroscope/static/auraya``.

In the Django admin, create a new Slide:

* ``URL to slide directory:``: *http://localhost:8000/static/auraya*
* ``Label``: whatever you like
* ``Maximum Google Zoom Level``: ``4``

**Save** the Slide.

Add a new *Collection*, and make sure you are in the ``Authors``.

Add a *Collection Slide*, that refers to your news Slide and your new Collection; fill in the
other fields as you like.

Visit ``http://localhost:8000/virtualmicroscope``.

Choose your Collection from the *Collections* menu, and choose your slide below.

And that's it - now you can zoom in and out on Auraya the dog.