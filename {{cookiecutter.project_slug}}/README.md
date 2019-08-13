# TemplateProject
Project template

## Table of contents

## Getting started
### Structure
You can see, below, the initial structure of your project:

```
├── README.md                <- The top-level README for developers using this project.
├── data
│   ├── external             <- Data from third party sources.
│   ├── processed            <- Intermediate/Final data that has been transformed.
│   └── raw                  <- The original, immutable data dump.
│
├── docs                     <- A default Sphinx project; see sphinx-doc.org for details
│
├── tools                    <- Pure Python scripts, utilities and configuration files
│
├── references               <- Data dictionaries, manuals, and all other explanatory materials.
│
├── reports                  <- Generated analysis as HTML, PDF, LaTeX, etc.
│   └── figures              <- Generated graphics and figures to be used in reporting
│
├── requirements.txt         <- The requirements file for reproducing the analysis environment
|
├── 1.0-pp-explore.ipynb     <- Jupyter notebooks. Naming convention is a number (for ordering),
│                               the creator's initials, and a short `-` delimited description

├── Dockerfile               <- The config file for Docker
├── LICENSE
├── Makefile                 <- The file that contains all the useful commands to launch your project
└── structure.txt            <- The structure file of the project
```

## Requirements

- Having a Python version >= 3
- Having a Docker installed on your computer
- Having a Git installed on your computer

## Docker or venv?

First you need to choose whether you want to use Docker or a virtual environment for your project.

### Use Docker

All you have to do is to use the following command in your terminal, this will build the image and run it.

``` bash
make launch-docker
```

When you are done with your code, click on the button "Quit" of Jupyter before closing the window/tab.

If you forgot to click on it, stop docker with:
``` bash
make clean-docker
```

### Use a virtual environment

Use the following command to launch Jupyter:

``` bash
make launch-local
```

This command creates the virtual environment automatically


### Update your tools documentation

Sphinx

## Usefull tips
### Add other packages

If ever you need to install new packages for your project with pip, but don't forget to update your file *requirements.txt*

### Update your structure file

If you add new files and/or folders, update your file *structure.txt*:
``` bash
make update-tree
```


### Using Git
[Git cheat sheet](https://rogerdudler.github.io/git-guide/files/git_cheat_sheet.pdf)


### Installing and using Docker
[Docker site](https://www.docker.com/)
