# TDC
Tabular data curation (TDC) tool

This is the structure of the TDC parent folder:
- hosted: a folder where the server temporarily stores the input dataset (it is removed after the execution).
- results: a folder where the results are stored.
- sample_datsets: includes a test input dataset (for demonstration purposes) in .xlsx, .csv and .json formats.
- static: includes a subfolder “images” which contains the HTML logos (from EUCAIM and from FORTH).
- .gitignore: this is needed when pushing unnecessary updates to github.
- templates: a folder which includes the HTML script (index.html) along with the logos (from EUCAIM and FORTH).
- app.py: the main script of the TDC tool.
- DockerFile: the file for building the dockerized application.
- README.md: a readme document which is needed for the GitHub repository.
- requirements.txt: the versions of the required python libraries that are necessary when building the docker.
