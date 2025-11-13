Molecular Emission Line Tool (MELT)
===================================

MELT is an interactive spectroscopic database for molecular emission lines with the function of search and simple visualization. This is the complete User Manual and Developer Guide for the MELT tool. 

🔗 **Live Tool**: https://copland-yz.github.io/MELT/

Overview
--------

You choose the spectral range, the elements must or must not include, then: 

* MELT provides the emission line information of the molecules that meet the requirements, including the spectral position, relative intensity, and the electronic transition systems.
* You can download the result in csv or txt, and generate an example spectrum based on the emission lines you choose. 

The tool is designed for researchers in spectroscopy, plasma physics, planetary science, analytical chemistry, spectrometer instrumentation, and astronomy.

Quick Start
-----------

1. Visit the live tool
2. Click elements in the periodic table to filter (once=include, twice=exclude)
3. Enter wavelength range and select units (nm, Å, μm, GHz, cm⁻¹)
4. Click "Search" to find matching lines
5. Select lines and generate spectra if desired
6. Download results

Documentation
-------------

.. toctree::
   :maxdepth: 2

   usage
   data
   development
   citation

Features
--------

Element Filtering
~~~~~~~~~~~~~~~~~

Click elements in the periodic table to:

* Include (green) - Show only molecules containing this element
* Exclude (red) - Hide molecules containing this element
* Reset (gray) - Remove filter

Multiple Units
~~~~~~~~~~~~~~

Search using your preferred unit:

* Nanometers (nm) - UV-Visible-NIR
* Ångström (Å) - Traditional spectroscopy
* Micrometers (μm) - Infrared
* Gigahertz (GHz) - Radio/microwave
* Wavenumber (cm⁻¹) - IR spectroscopy

Spectrum Visualization
~~~~~~~~~~~~~~~~~~~~~~

Generate synthetic spectra with:

* Adjustable peak width (FWHM) for instrumental resolution
* Interactive zoom and pan
* Export as PNG image

Data Sources
------------

Current database: **Pearse & Gaydon (1976)** - ~10,000 molecular emission lines covering UV to near-IR

Citation
--------

.. code-block:: bibtex

   @software{yong2025,
     author = {Yong, Chengzheng},
     title = {Molecular Emission Line Tool},
     url = {https://github.com/Copland-yz/MELT},
     year = {2025}
   }

Support
-------

* GitHub: https://github.com/Copland-yz/MELT
* Issues: https://github.com/Copland-yz/MELT/issues
* Email: chengzheng@wustl.edu

License
-------

MIT License
