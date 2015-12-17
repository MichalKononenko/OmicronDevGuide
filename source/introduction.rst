Introduction
============

Hello! Welcome to the Omicron Project. Encompassed in this project are (at the
time of writing) the Omicron Server, the Omicron Client, and this Omicron Dev
Guide.

Omicron is intended to be *the* web platform for managing hardware-intensive
experiments at the University of Waterloo Institute for Quantum Computing.
The only required knowledge for an end user to get started should be a research
topic. Users should then be able to create interactive lab procedures in
compliance with standard operating procedures (SOPs) for an experimental
apparatus, and share these with collaborators. Finally, this system will work
as a file store for both the user and computer-controlled systems to upload
results.

    .. note::

        At the time of writing, I was a `second-year undergrad`_ at the
        University of Waterloo, and this was my first foray into full-stack web
        development. Consequently, if you find anything wrong with this
        documentation, if anything needs to be elaborated on, that's a bug.
        Report it `here`_ and we'll work on fixing it up. I open-sourced this
        project to get as many eyeballs on the codebase as possible. Let's work
        together to build the best damn stack that ever was!

.. _here: https://github.com/MichalKononenko/OmicronDevGuide/issues/new
.. _second-year undergrad: https://github.com/MichalKononenko

Audience
--------

This guide is intended for contributors to and stakeholders interested in the
Omicron Project, who wish to understand

   -  The problem that the system is trying to solve
   -  The reasoning behind particular design choices in the platform design
   -  The development process, from contributing to code review
   -  Current and future directions for the project
   -  The basics of developing code for the Omicron Project

    .. note::

        It is recommended that readers of this guide get an account on
        `GitHub`_ as soon as possible. Unfortunately, in order to report bugs,
        You need to have this. Fortunately, it means we can talk in nice
        threaded discussions about your concerns. Alternatively, you can email
        me at ``mkononen@uwaterloo.ca``.

.. _GitHub: https://github.com/

Acknowledgements
----------------

The Omicron Project wishes to thank

    -   The Cory Group at the `Institute for Quantum Computing`_ for
        supporting and giving feedback on the project.

    -   `Miguel Grinberg`_ for his excellent `Flask mega-tutorial`_ series
        on web development in the Flask microframework, as well as his series
        of discussions on REST API development in Flask.

    -   The writers of the `Heroku Platform API`_ documentation, which served
        as inspiration for our own design practices and REST API design. In
        such a `loosely-defined`_ style as REST, this document was a source of
        light to this project.

    -   The maintainers of all the libaries, services, and frameworks on which
        this project depends. From `SQLAlchemy`_ to `Freezegun`_, from
        `React`_ to `Istanbul`_, this project would not be possible without
        talented developers maintaining these projects for Omicron and many
        other web projects. You guys rock!

.. _Institute for Quantum Computing: https://goo.gl/3iGt6a
.. _Miguel Grinberg: http://blog.miguelgrinberg.com/
.. _Flask mega-tutorial: http://goo.gl/IW64Ew
.. _Heroku Platform API: https://goo.gl/tniZ9X
.. _loosely-defined: https://en.wikipedia.org/wiki/Representational_state_transfer
.. _SQLAlchemy: http://www.sqlalchemy.org/
.. _Freezegun: https://pypi.python.org/pypi/freezegun
.. _React: https://facebook.github.io/react/
.. _Istanbul: https://gotwarlost.github.io/istanbul/

The Use Case
------------

The following workflow should eventually be implemented on the site

    -   User comes up with idea for an experiment involving detecting spin
        signals on a silicon chip in NMR
    -   User logs in to the Omicron Client
    -   User creates a project and invites collaborators (also users) to their
        projects
    -   User uses Markdown to make a nice project description
    -   User creates a procedure in the project involving the use of a
        molecular beam epitaxy machine and a nuclear magnetic resonance
        spectrometer.
    -   Collaborator suggests a change, creates his own copy of the procedure,
        and compares it against the User's. If the user likes the changes, they
        can be incorporated into the procedure.
    -   User schedules time on each machine. Other users can then check on when
        the machine is being used.
    -   User carries out the experiment.
    -   User uploads the results to a given procedure
    -   If something breaks, the user raises an issue with the machine, assigns
        it a severity level, and a push notification is sent to Users who have
        "subscribed" to the machine, so that a fix can be made.

The use case for the minimum viable product is

    - User logs in to the client
    - User invites collaborators to projects that the user opened
    - User pushes files to the project

License
-------

The Omicron Server, Client, and Dev Guide are licensed under the GNU General
Public License v3. A copy of the license can be found in the ``LICENSE`` file
in this project's root directory, as well as on the `GNU Project website`_.

.. _GNU Project website: https://www.gnu.org/licenses/gpl-3.0.en.html


Project Breakdown
-----------------

In order to break down the gargantuan use case outlined in the use case,
the Omicron project is broken into three parts

    -   The **Omicron Server** is an HTTP REST API written in Python, which
        takes in data from a relational database and presents a dynamic
        JSON-based data model. Other programs interact with **Omicron Server**
        through HTTP requests that perform transactional CRUD (Create,
        Update, Delete) operations on resources.

    -   The **Omicron Client** is a User Interface (UI) written in Javascript
        and running on the user's browser. React JS was selected as the
        front-end framework for the project. Ideally, the UI will be a
        single-page application (SPA). The UI interacts with the API, and
        transforms the data model presented by the API into meaningful
        information for the user

    -   The **Omicron Dev Guide**, what you are reading now, is a lump of
        documentation meant to introduce the project to new developers, and to
        familiarize users with some of the decisions made for this project.

Hosted versions of the documentation for the `Omicron Server`_ and
`Omicron Dev Guide`_ are available on `readthedocs.org`_.

.. _Omicron Server: omicron-server.readthedocs.org
.. _Omicron Dev Guide: omicron-dev-guide.readthedocs.org
.. _readthedocs.org: readthedocs.org
