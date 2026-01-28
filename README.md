# Molecular Emission Line Tool (MELT)

An interactive web-based search tool for molecular emission lines. 

🔗 **Live Tool**: [https://copland-yz.github.io/MELT/](https://copland-yz.github.io/MELT/)

📖 **Documentation/User manual**: [https://melt.readthedocs.io/en/latest/index.html](https://melt.readthedocs.io/en/latest/index.html)

## Core Features

- **Search emission lines by filtering elements and range parameters**
- **Spectrum Visualization**: Generate example spectra from selected emission lines
- **Downloadable Contents**: Can download the search results and the example spectrum

## Usage Examples

### 🔬Laboratory Spectroscopy

- Search for the source of emission lines for **LIBS (laser induced breakdown spectroscopy), plasma science, or other analytical chemistry** research 
- Find reference lines for wavelength calibration
- Generate example spectra to understand a group of lines and instrumental resolution effects

### 💻Workflow

1. **Search for lines**: Use element (click once to include, click twice to exclude) and data range (nanometers, Ångström, micrometer, GHz, or wavenumber) filters to find relevant emission lines (**a small range <100 nm is recommended!**)
2. **Select lines**: Check the boxes next to lines of interest in the results table
3. **Adjust parameters**: Set the peak width to simulate instrumental resolution
4. **Generate spectrum**: Click "Generate Spectrum" to create an interactive visualization
5. **Export**: Download the spectrum as PNG or the selected lines as TXT/CSV

## Technical Details

### Implementation

- **Frontend**: Pure HTML/CSS/JavaScript with Chart.js for visualization
- **Database**: JSON files loaded dynamically via fetch API  
- **Parsing**: Regex-based molecular formula parsing for element extraction
- **Spectrum Generation**: Gaussian peak modeling with user-adjustable FWHM
- **Export**: Canvas-based PNG export and client-side file generation

### File Structure

```
molecular-lines/
├── index.html              # Main search interface
├── assets/
│   ├── js/
│   │   └── molecular-lines.js   # Search logic and periodic table
│   └── data/
│       ├── data-manifest.json   # Index of all data files
│       ├── Pearse&Gaydon/       # Pearse & Gaydon (1976) data
│       ├── 1985_Borucki.json    # Borucki et al. (1985)
│       ├── 1996_Clay.json       # Clay et al. (1996)
│       ├── 2008_Camacho.json    # Camacho et al. (2008)
│       ├── 2008_Reyes.json      # Reyes et al. (2008)
│       ├── 2014_Rezaei.json     # Rezaei et al. (2014)
│       ├── 2015_Kiristi.json    # Kiristi et al. (2015)
│       └── 2022_Zhang.json      # Zhang et al. (2022)
├── _config.yml             # Jekyll configuration
└── README.md               # This file
```

Any folders not shown in this file structure are Jekyll template style files or documentation files.

## Development

### Deploy the website locally

1. Make sure you have installed the requirements (ruby-dev, bundler, and nodejs)
   
   For Linux (or Windows Subsystem for Linux) the command is:
   
   ```shell
   sudo apt install ruby-dev ruby-bundler nodejs
   ```
   
   If you see error `Unable to locate package ruby-bundler`, `Unable to locate package nodejs` , run the following:
   
   ```shell
   sudo apt update && sudo apt upgrade -y
   ```
   
   then try run `sudo apt install ruby-dev ruby-bundler nodejs` again.
   
   On MacOS the command is:
   
   ```shell
   brew install ruby
   brew install node
   gem install bundler
   ```

2. Run `bundle install` to install ruby dependencies. If you get errors, delete Gemfile.lock and try again.
   
   If you see file permission error like `Fetching bundler-2.6.3.gem ERROR: While executing gem (Gem::FilePermissionError) You don't have write permissions for the /var/lib/gems/3.2.0 directory.` or `Bundler::PermissionError: There was an error while trying to write to /usr/local/bin.` Install Gems Locally (Recommended):
   
   ```shell
   bundle config set --local path 'vendor/bundle'
   ```
   
   then try run `bundle install` again. If succeeded, you should see a folder called `vendor` and `.bundle`.

3. Run:
   
   ```shell
   bundle exec jekyll serve -l -H localhost
   ```
   
   to generate the HTML and serve it from `localhost:4000/MELT` the local server will automatically rebuild and refresh the pages on change.
   
   Note: Sometimes the page will not be automatically rebuild. In this circumstance, use `Ctrl+C` to stop it, and run the building command again.

### Adding New Databases

1. Convert spectroscopic data to JSON format with required fields:
   
   ```json
       {
           "molecule": "CO",
           "system": "THE TRIPLET BANDS, d³Δ–a³Π",
           "wavelength_nm": 646.46,
           "wavelength_angstrom": 6464.6,
           "upper_level": "d³Δ",
           "lower_level": "a³Π",
           "intensity": null,
           "source": "Pearse & Gaydon (1976) p.111",
           "page": 111
       }
   ```

2. Add JSON files to `assets/data/` directory

3. Update `molecular-lines.js` to include new file paths in loading logic

## Citation

If you use this tool in your research, please cite:

```bibtex
@software{yong2025,
  author = {Yong, Chengzheng and Qu, Hongkun},
  title = {Molecular Emission Line Tool},
  url = {https://github.com/Copland-yz/MELT},
  year = {2025}
}
```

## Reference

### Data Sources

- Pearse, R. W. B., & Gaydon, A. G. (1976). *The identification of molecular spectra* (4th ed.). Chapman & Hall.
- Borucki, W. J., McKenzie, R. L., McKay, C. P., Duong, N. D., & Boac, D. S. (1985). Spectra of simulated lightning on Venus, Jupiter, and Titan. *Icarus*, 64(2), 221-232.
- Clay, K. J., Speakman, S. P., Amaratunga, G. A. J., & Silva, S. R. P. (1996). Characterization of a-C:H:N deposition from CH4/N2 rf plasmas using optical emission spectroscopy. *Journal of Applied Physics*, 79(9), 7227-7233.
- Camacho, J. J., Díaz, L., Santos, M., Reyman, D., & Poyato, J. M. L. (2008). Optical emission spectroscopic study of plasma plumes generated by IR CO2 pulsed laser on carbon targets. *Journal of Physics D: Applied Physics*, 41(10), 105201.
- Reyes, P. G., Mendez, E. F., Osorio-Gonzalez, D., Castillo, F., & Martínez, H. (2008). Optical emission spectroscopy of CO2 glow discharge at low pressure. *physica status solidi c*, 5(4), 907-910.
- Rezaei, F., Abbasi-Firouzjah, M., & Shokri, B. (2014). Investigation of antibacterial and wettability behaviours of plasma-modified PMMA films for application in ophthalmology. *Journal of Physics D: Applied Physics*, 47(8), 085401.
- Kiristi, M., Bozduman, F., Oksuz, A. U., Hala, A., & Oksuz, L. (2015). A Comparison Study of Microwave and Radio Frequency Plasma Polymerized PEDOT Thin Films. *Journal of Macromolecular Science, Part A*, 52(2), 124-129.
- Zhang, S., Zeng, X., Bai, H., Zhang, C., & Shao, T. (2022). Optical emission spectroscopy measurement of plasma parameters in a nanosecond pulsed spark discharge for CO2/CH4 dry reforming. *Spectrochimica Acta Part A: Molecular and Biomolecular Spectroscopy*, 267, 120590.

### Website

- The website theme is based on [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/) by © 2016 Michael Rose and released under the MIT License
- Integrated the [Academic Pages](https://academicpages.github.io/) template

## License

MIT License

## Contributing

Contributions are welcome! Please feel free to:

- Add new molecular databases
- help with proofreading
- Improve the search interface
- Report bugs or suggest features
- Submit [pull requests](https://github.com/Copland-yz/molecular-emission-lines/pulls)

## Contact

**Chengzheng (Copland) Yong**  
Washington University in St. Louis  
Email: chengzheng@wustl.edu  
Website: [https://copland-yz.github.io](https://copland-yz.github.io)
