Development
===========

This page explains how to contribute to MELT or run it locally.

Local Development
-----------------

Prerequisites
~~~~~~~~~~~~~

For local Jekyll development:

* Ruby 2.5+ and ruby-dev
* Node.js 12+
* Bundler gem

Installation
~~~~~~~~~~~~

**Linux/WSL**:

.. code-block:: bash

   sudo apt install ruby-dev ruby-bundler nodejs

**macOS**:

.. code-block:: bash

   brew install ruby node
   gem install bundler

Setup
~~~~~

.. code-block:: bash

   # Clone repository
   git clone https://github.com/Copland-yz/MELT.git
   cd MELT

   # Install dependencies locally
   bundle config set --local path 'vendor/bundle'
   bundle install

   # Run development server
   bundle exec jekyll serve -l -H localhost

Visit http://localhost:4000/MELT/

The ``-l`` flag enables live reload - changes auto-refresh in browser.

Contributing
------------

Ways to Contribute
~~~~~~~~~~~~~~~~~~

* **Add spectroscopic databases** - New emission line data
* **Report bugs** - Issues or unexpected behavior
* **Improve documentation** - Clarifications or corrections
* **Suggest features** - New functionality ideas

Workflow
~~~~~~~~

1. **Fork** the repository on GitHub
2. **Clone** your fork locally
3. **Create branch**: ``git checkout -b feature-name``
4. **Make changes** and test
5. **Commit**: ``git commit -m "Description"``
6. **Push**: ``git push origin feature-name``
7. **Create Pull Request** on GitHub

Adding New Data
---------------

Data Format
~~~~~~~~~~~

Create JSON file for each molecule:

.. code-block:: json

   [
     {
       "molecule": "CO",
       "system": "d³Δ–a³Π",
       "wavelength_nm": 646.46,
       "wavelength_angstrom": 6464.6,
       "upper_level": "d³Δ",
       "lower_level": "a³Π",
       "intensity": null,
       "source": "Pearse & Gaydon (1976) p.111",
       "page": 111
     }
   ]

**Required fields**: molecule, wavelength_nm, wavelength_angstrom, source

**Optional fields**: intensity, system, upper_level, lower_level, page


Adding to MELT
~~~~~~~~~~~~~~

1. Place JSON file in ``assets/data/YourDatabase/``
2. Edit ``assets/data/data-manifest.json``
3. Add file path to loading array:

.. code-block:: json
   {
   "description": "Manifest of all molecular emission line data files. Add new JSON files here to include them in searches.",
      "files": [
         "Pearse&Gaydon/page_029.json",
         // ... existing files
         "YourDatabase/EXAMPLE.json",  // Add here
      ]
   }

4. Test locally
5. Submit pull request


Commit Messages
~~~~~~~~~~~~~~~

.. code-block:: text

   Short summary (50 chars max)

   Optional detailed explanation.
   - Use bullet points if needed
   - Explain what and why, not how

Good examples:

* "Add OH molecule data from NIST database"
* "Fix spectrum generation for missing intensity values"
* "Update README with new citation format"

Testing
-------

Before submitting changes:

1. **Build locally** - Verify no errors
2. **Test search** - Search for wavelength range with new data
3. **Test spectrum** - Generate spectrum from new lines
4. **Test export** - Download CSV/TXT/PNG

Documentation
-------------

Building Docs Locally
~~~~~~~~~~~~~

.. code-block:: bash

   cd docs
   pip install -r requirements.txt
   make html

View at ``docs/_build/html/index.html``

Updating Docs
~~~~~~~~~~~~~

Edit files in ``docs/`` directory and build locally to preview. Then simply push the change to github. Our documentation site https://melt.readthedocs.io/en/latest/index.html will update automatically.

Support
-------

* **GitHub Issues**: https://github.com/Copland-yz/MELT/issues
* **Email**: chengzheng@wustl.edu

License
-------

MELT is released under the MIT License. Contributions are welcome!
