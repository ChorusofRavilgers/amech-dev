# amech-dev

This repository provides instructions for installing and running AutoMech from source,
as a developer.

If you are a brand new AutoMech developer, start by following the instructions at the
very bottom to fork the AutoMech repositories.

## Install AutoMech with Mamba

The following instructions only need to be done once per machine.

### Install Miniforge

If you haven't already, install Miniforge as follows.
*Note:
If your home directory has limited disk space, you will want to set the installation
path to a directory with more space when prompted.  Also, if you have the `TMPDIR`
environment variable set to a non-existent directory, you will need to run `mkdir
$TMPDIR` first.*
```
wget "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
bash Miniforge3-$(uname)-$(uname -m).sh
```
If you don't wish to activate your conda base environment on startup, you can add the
following aliases to your `~/.bashrc` for activating the `base` and `amech-deps` conda environments.
(The latter will be created below.)
```
alias cab='. <path to conda installation>/bin/activate'
alias caa='. <path to conda installation>/bin/activate amech-deps'
```

### Install AutoMech in developer mode

1. Clone this `amech-dev` repository wherever you want your AutoMech source code to
live and enter its top-level directory.
Unless you are a core developer, you can clone via HTTP from the main Auto-Mech repo.
(Core developers should fork and clone via SSH, so that they can make changes to this repo as needed.)
```
git clone https://github.com/Auto-Mech/amech-dev.git
cd amech-dev/
```

2. Create the `amech-deps` conda environment.
```
mamba env create -f mamba.yml
```

3. Run the download script to download the repositories and check out their `dev` branches. These will be placed in `src/`.
```
./download.sh
```

4. Activate the `amech-deps` environment and run the install script to install each of
the main AutoMech modules into it in edit mode.
```
caa # alias defined above, or `conda activate amech-deps`
./install.sh
```

## Run AutoMech and Contribute to the Code

```
pixi shell
```

## New AutoMech Developers Start Here

### Fork repositories and add dev branches

Log into GitHub and fork the following five repositories:

 - [AutoMech](https://github.com/Auto-Mech/autochem)
 - [AutoIO](https://github.com/Auto-Mech/autoio)
 - [AutoFile](https://github.com/Auto-Mech/autofile)
 - [MechAnalyzer](https://github.com/Auto-Mech/mechanalyzer)
 - [MechDriver](https://github.com/Auto-Mech/mechdriver)

Then, for each fork, add the `dev` branch of the Auto-Mech repository as follows:

1. On the GitHub page for your fork, add `/branches` to the URL.
2. Click the green button in the upper right that says "New branch".
3. Set `dev` as the branch name and choose the `dev` branch from the main `Auto-Mech` repository as its source.