# ipynb website: Simple data science website using Jupyter notebooks

This repository is an adaptable framework for publishing websites from
[Jupyter interactive notebooks](https://jupyter.org).

*Please copy and adapt this repository for your own project.*

View the demo project website
[here](https://stephenslab.github.io/ipynb-website).

If you find any problems, or would like to suggest new features,
please open an
[Issue](https://github.com/stephenslab/ipynb-website/issues). We also
encourage community contributions, e.g., by forking the repository,
making your suggested changes, and issuing a pull request.

## License

Copyright (c) 2017, Peter Carbonetto & Gao Wang.

All source code and software in this repository are made available
under the terms of the [MIT license](https://opensource.org/licenses/MIT).

## Quick Start

To start your own Jupyter-notebook-based research website, please
follow these steps.

*Note:* These instructions assume that you are managing your project
files inside a git repository, but this is not strictly necessary; if
you prefer not to do this, skip the git commands in the steps
below. (For an introduction to git, see
[here](https://swcarpentry.github.io/git-novice) or
[here](https://doi.org/10.1371/journal.pcbi.1004668).)

1. Install Python >= 3.5 and Jupyter. The recommended way to do this
   is to download and install
   [Anaconda 3](https://www.continuum.io/anaconda-overview). Note that
   Python >= 3.5 comes with [pip](https://pip.pypa.io), so you should
   not need to install it separately.

2. **Please note:** If you already have Jupyter installed for
   Python 2.x (e.g., Anaconda 2), then you will need to be careful
   that you install SoS for Python 3.x in the next step. To make sure,
   before running the commands below run `pip --version` or `pip3
   --version`.)

3. Install [SoS](https://github.com/vatlab/SOS) ("Script of Scripts")
   for Python 3.x:

   ```bash
   pip3 install sos
   ```

   Note that the executable on your computer may be either `pip` or
   `pip3`, depending on your setup. Also note that you may need to
   include the `--user` flag if you do not have administrative
   privileges on the computer.

   If you get a warning, "Could not find .egg-info directory in
   install record for sos...", please ignore it.

4. Install [git](https://git-scm.com/downloads). 

5. Make a personal copy of this repository:

   + Download the [latest release](https://github.com/stephenslab/ipynb-website/releases/tag/v0.9) of this repository from Github.

   + Create a new git repository (`git init ...`), copy all the files
   from this repository to the new repository folder.

   + Change the
   working directory to the new repository folder and commit these
   files to the new repository:

   ```bash
   git add ./
   git commit
   ```

   + Alternatively, if you are not using git, create a new folder
   (`mkdir ...`) and add copy the files to this new folder.

6. Inside your new project directory, re-generate all the webpages
   using the SoS release script:

   ```bash
   sos-runner ./release.sos -s force
   ```

   **Important note:** Building the webpages from the Jupyter
   notebooks does not actually run the code in the notebooks. If you
   would like to run the code prior to generating the webpages, this
   must be done interactively in Jupyter, or from the command line
   using `jupyter nbconvert --execute`.

   All the webpages are created and stored in the "docs"
   directory. This is convenient for git repositories hosted on
   Github because 
   [Github Pages](https://help.github.com/categories/github-pages-basics)
   can be configured to publish the webpages from the "docs" folder.

7. View the newly generated home page `docs/index.html` in your
   favorite Web browser.

8. If you would like to upload your new git repository to a git
   hosting website, do the following:

   + Create a new empty repository on tour favorite git hosting
     website (e.g., [Github](http://github.com),
     [GitLab](http://gitlab.com), [Bitbucket](https://bitbucket.org).
     Currently, only Github has been tested; other sites may work as
     well, but may not support all the website publishing features.

   + Determine the URL of the host repository, and add this URL to the
     repository on your computer with `git remote add origin ...`.

   + Upload to the host repository with `git push origin master`.

   + Configure the repository settings to publish the webpages; e.g.,
     using [Github Pages](https://help.github.com/categories/github-pages-basics)).

9. You are now ready to adapt the Jupyter-notebook-based website for
   your own project:

   + Modify the website settings by editing `config.yml`. See the
     comments in this file for more detailed instructions.

   + Copy, rename or delete the notebooks in the "analysis", "setup"
     and "license" directories.

   + Edit the notebooks interactively in Jupyter.

   + After you are satisfied with your changes, re-build the modified
     webpages by running `sos-runner ./release.sos`, or use
     `sos-runner ./release.sos -s force` to re-build all the webpages,
     then commit your changes to the git repository.

## More setup details

+ Whenever you make global changes to the website (e.g., you change
  the Boostrap theme in `config.yml`), use the `-s force` option to force
  updates to all the webpages, not just the ones that have been modified.

+ The [jnbinder tool](https://github.com/gaow/jnbinder) is used to
  generate the webpages from the Jupyter notebooks. To update jnbinder
  for your project, run this command in the base directory of your
  repository:

  ```bash
  sos-runner ./release.sos upgrade-jnbinder
  ```

## Tips for adapting this framework for your project

+ The `release.sos` script will not automatically remove webpages that
  are no longer needed (e.g., after renaming a Jupyter notebook). You
  will need to delete these unused files manually.

+ The `include_dir` setting in `config.yml` specifies the project
  subdirectories containing Jupyter notebooks to render into
  webpages. If no `index.ipynb` file is provided within a given
  subdirectory, an index with filename `_index.ipynb` will
  automatically be generated, and rendered as `_index.html`.

+ There is also the option of adding a table of contents to each
  notebook by setting `notebook_toc: True` in `config.yml`.

+ For the table of contents and the automatically generated index, it
  is recommended that the notebooks have descriptive names; e.g.,
  `Plot_station_map.ipynb`. All underscores are automatically treated
  as spaces, so `Plot_station_map.ipynb` will show as "Plot station
  map" in the index file and table of contents.

+ So far, only the Cerulean, Flatly and Readable Bootstrap themes have
  been adapted and tested for this framework. It is possible to select
  other themes (see [here](https://bootswatch.com) for a larger
  collection), although they may not work as well. Also note that
  there may be style conflicts or inconsistencies in the included CSS
  files; please report these style conflicts by posting an
  [Issue](https://github.com/stephenslab/ipynb-website/issues).

+ For more website customization details, please refer to the comments
  in the [config.yml](config.yml) file.

## Credits

**ipynb website** was developed by:

Peter Carbonetto and Gao Wang<br>
Dept. of Human Genetics<br>
University of Chicago<br>

[John Blischak](https://github.com/jdblischak),
[Matthew Stephens](http://stephenslab.uchicago.edu) and others have
also contributed to the development of this software.
