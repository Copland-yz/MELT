---
title: 'MELT: An Interactive Web-Based Database for Molecular Emission Spectroscopy‘
tags:
  - Database
  - LIBS
  - Plasma
  - Astronomy
  - Chemical Physics
authors:
  - name: Chengzheng Yong
    orcid: 0000-0001-6713-0254
    corresponding: true
    affiliation: 1
authors:
  - name: Hongkun Quincy Qu
    orcid: 0000-0002-5626-8298
    affiliation: 2
affiliations:
  - name: Department of Earth, Environmental, and Planetary Sciences, Washington University in St. Louis, MO 63130, USA
    index: 1
affiliations:
  - name: Aerospace Information Technology University, Jinan 250200, China
    index: 2
date: 3 February 2026
bibliography: paper.bib
---

# Summary

MELT (Molecular Emission Line Tool) is a web-based, interactive tool that compiles the data from several spectroscopic datasets [@pearse:1976; @borucki:1985; @clay:1996; @camacho:2008; @reyes:2008; @rezaei:2014; @kiristi:2015; @zhang:2022]. This tool overcomes the limitations of traditional, text-based spectroscopic resources by providing a dynamic user interface for searching, filtering, browsing, and visualizing molecular emission line data. Built with Jekyll and a JavaScript application, MELT offers a modern, user-friendly interface to a foundational spectroscopic dataset, with applications in plasma physics, astronomy, chemistry, and planetary science. The tool is openly accessible at [https://copland-yz.github.io/MELT/](https://copland-yz.github.io/MELT/).

# Statement of Need

The analysis of molecular spectra is fundamental to many fields, including plasma physics, astronomy, chemical physics, and planetary science. For example, it could reveal the composition of exoplanet atmosphere or interstellar medium [@exoplanet] or analyze complicated planetary atmospheric processes [@Alcouffe:2010], and LIBS (Laser Induced Breakdown Spectroscopy) is a useful technique to examine planetary materials in-situ [@LIBS]. 

For decades, researchers have relied on comprehensive compilations of molecular spectra, but these resources are often text-based. Hence, it has the following problems: 1) The readers have to search the content manually, while computer-based keyword search is quite common nowadays. 2) The readers have to know the molecules before they look up the emission lines. But in practice, a common task is the reverse: identifying which molecule is responsible for an observed spectral line. 3) The existing data compilations lack visualization tools for comparing spectral data, a feature available in modern databases such as the NIST LIBS database [@NISTdatabase]. MELT was developed to overcome these limitations by digitizing a foundational spectroscopic dataset and making it accessible through a modern web interface. The goals of the project were to:

1. Digitize the spectral data into a structured, machine-readable format.
2. Create a fast, modern, and intuitive web interface for accessing this data.
3. Develop a tool that enables the generation of an example spectrum for comparison with observed data.
4. Ensure the resource is freely and globally accessible to researchers, educators, and students.

# About MELT

The project is developed and hosted on a free domain, [https://copland-yz.github.io/MELT/](https://copland-yz.github.io/MELT/). It is open-source, the source code and the database can be
accessed at [https://github.com/Copland-yz/MELT](https://github.com/Copland-yz/MELT) and the Documentation/User manual can be found on [https://melt.readthedocs.io/en/latest/index.html](https://melt.readthedocs.io/en/latest/index.html). 

The data is structured into the JSON format, stored in 'assets/data'. Each entry contains the information of a single emission line, including the molecule species, transition system, wavelength, data source, and other characteristics.

The website is built upon the Jekyll static site generator. The core functions are written in 'assets/js/molecular-lines.js'. Users can deploy the site locally by installing the requirements (can be found in Github README or the documentation site) and then add their own data for further use. 

The primary features of MELT include:

* **Element Selection:** Users can choose to include or exclude certain elements to narrow down the range of search results. It is also possible to search for all molecules in the database.
* **Data Range Filtering:** The dataset can be filtered by wavelength, wavenumber, or frequency. Wavelength units can be specified in Å, nm, or µm.
* **Example Spectrum Generation:** Many molecular emission lines exist as the form of line groups. Thus, users can select a few lines of the same molecule, and generate an example spectrum based on their relative intensity. This example spectrum may not match the real spectrum, but it provides the users with a more intuitive way of showing a group of emission lines.

# Future Work

Future work could involve several key improvements:

* Include more spectroscopic datasets.
* Deploy it on a dedicated domain and apply server-side computation to save memory on the client side and to enhance safety.
* Continue proofreading of the original text, and develop a plan to handle special molecules with different data format.

# Acknowledgements

The author wishes to thank Chun Huang's suggestions, the open-source community, the creators of the Jekyll framework for providing the tools of building the website.
