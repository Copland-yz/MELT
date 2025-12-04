Data and Technical Details
==========================

Database Information
--------------------

Current Database
~~~~~~~~~~~~~~~~

**Pearse & Gaydon (1976)**

* Citation: Pearse, R. W. B., & Gaydon, A. G. (1976). *The identification of molecular spectra* (4th ed.). Chapman and Hall.
* **Coverage**: ~10,000 emission lines
* **Wavelength range**: 200-2,000 nm (UV to near-IR)
* **Precision**: Typically 0.01-0.1 nm

Data Description
-----------
When a molecule is excited (e.g., by electron collision in a plasma), it will decay from a higher energy level (upper level) to a lower energy level (lower level) undergoing a downward transition and release a photon with a precise wavelength which depends on the energy difference between the two levels, E = E_upper - E_lower = h\v = hc/λ. It is the spectral fingerprint of a molecule, since each molecular species (and its specific excited state) possesses a distinct pattern of emission lines. Owing to the coupling of electronic, vibrational, and rotational degrees of freedom, molecular transitions typically give rise not to isolated lines, but to band spectra—clusters of closely spaced lines resulting from simultaneous changes in vibrational and rotational quantum numbers during an electronic transition.

Each emission line includes:

* **Molecule** - Chemical formula (e.g., CO, H2, OH)
* **System** - Spectroscopic transition notation
* **Wavelength** - In nm and Ångström
* **Upper/Lower Level** - Energy state notation
* **Intensity** - Relative intensity (when available)
* **Source** - Literature reference and page number

Technical Implementation
------------------------

Architecture
~~~~~~~~~~~~

* **Frontend**: HTML/CSS/JavaScript
* **Visualization**: Chart.js library
* **Data**: Static JSON files
* **Hosting**: GitHub Pages (Jekyll)

MELT is entirely client-side - all data processing happens in your browser. No server required.

Spectrum Generation
~~~~~~~~~~~~~~~~~~~

Emission lines are modeled as Gaussian peaks:

.. math::

   I(\lambda) = I_0 \cdot \exp\left(-\frac{(\lambda - \lambda_0)^2}{2\sigma^2}\right)

Where:

* λ₀ = line center wavelength
* I₀ = peak intensity
* σ = standard deviation (related to FWHM by: FWHM = 2.355σ)

File Structure
--------------

.. code-block:: text

   MELT/
   ├── index.html              # Main application
   ├── assets/
   │   ├── js/
   │   │   └── molecular-lines.js   # Core logic
   │   └── data/
   │       └── Pearse&Gaydon/       # JSON data files
   └── docs/                   # This documentation

Data Files
~~~~~~~~~~

JSON format, one file per molecule:

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

Adding New Databases
--------------------

To contribute additional spectroscopic data:

1. **Format data** as JSON following the schema above
2. **Validate** JSON syntax
3. **Test** in local copy of MELT
4. **Submit** via GitHub pull request

See :doc:`development` for detailed instructions.

Limitations
-----------

* **Intensity data** not always available (shown as null)
* **Wavelength precision** varies by source (typically 0.01-0.1 nm)
* **Temperature dependence** not specified
* **Line shapes** modeled as Gaussian (real shapes may differ)

For absolute intensity measurements or high-precision work, consult original sources.


References
----------

**Primary data source**:

Pearse, R. W. B., & Gaydon, A. G. (1976). *The identification of molecular spectra* (4th ed.). Chapman and Hall.

**Additional resources**:

* NIST Atomic Spectra Database: https://physics.nist.gov/PhysRefData/ASD/lines_form.html
* Atomic Line List: https://www.pa.uky.edu/~peter/atomic/
* NIST LIBS Database: https://physics.nist.gov/PhysRefData/ASD/LIBS/libs-form.html
