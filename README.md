# boilerplates-latex_doc

Template para desenvolvimento de documetos LaTex

## Needed Tools

- Python (v3.12.3 or later) **Mandatory**
- Poetry (v1.8.2 or later) ***Mandatory**
- TextLive (v2024 or later) ***Mandatory**
  - libyaml-tiny-perl
- asdf (v0.12 or later) **Optional**

Tools installation instructions are available below.

### Install TexLive

The TextLive is a distribution of LaTeX that is available for all major operating systems. The installation instructions are available at the [official website](https://www.tug.org/texlive/). 

> I'm getting Can't locate Config/YAML.pm in @INC (you may need to install the Config::YAML module) while running a perl script.  On Ubuntu 22.04, I was only missing **libyaml-tiny-perl**

```bash
sudo apt-get install libyaml-tiny-perl
sudo apt-get install libfile-homedir-perl
```

### Install Python

The Python is a programming language that lets you work quickly and integrate systems more effectively. The installation instructions are available at the [official website](https://www.python.org/).

### Install Poetry

The Poetry is a tool for dependency management and packaging in Python. The installation instructions are available at the [official website](https://python-poetry.org/).

### Install asdf

The asdf is a CLI tool that can manage multiple language runtime versions on a per-project basis. The installation instructions are available at the [official website](https://asdf-vm.com/).

## Start Development Environment

1. Install project needed tools: **Poetry**, **TexLive** and **asdf** are the are used in the following steps.
1. Clone the repository: ```git clone && cd 'project directory'```
1. Install python env: ```asdf install```
1. Load python env: ```poetry shell```
1. Install project dependencies: ```poetry install```
1. Open the project in your favorite editor and start coding. VSCode is recommended.
