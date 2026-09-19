# conda

create a new environment with a specific Python version

    conda create -n myenv python=3.11


activate an environment

    conda activate myenv


deactivate the current environment

    conda deactivate


list all environments

    conda env list


install a package into the active environment

    conda install numpy


install from a specific channel

    conda install -c conda-forge scikit-learn


install multiple packages at once

    conda install numpy pandas matplotlib


list installed packages in the active environment

    conda list


remove a package

    conda remove numpy


update a package

    conda update numpy


update all packages in the active environment

    conda update --all


export environment cross-platform compatible (history only, preferred)
note: omits auto-resolved dependencies and pip-installed packages; pin Python
explicitly at env creation time (conda create -n ENVNAME python=3.11) so it
appears in the history and is captured here

    conda env export --from-history > ENV.yml


export an environment to a YAML file (platform + package specific)

    conda env export > environment.yml


recreate an environment from a YAML file

    conda env create -f environment.yml


delete an environment

    conda env remove -n myenv


search for a package

    conda search numpy


clean unused packages and caches

    conda clean --all


rename an environment (clone then remove the old one)

    conda create -n newname --clone oldname
    conda env remove -n oldname


rename an environment (native rename)

    conda rename -n ENVNAME NEWENVNAME


verify conda install and check version

    conda info


update conda itself (run in base)

    conda update -n base conda


list installed packages with source channel info

    conda list --show-channel-urls


install a specific version of a package

    conda install PKGNAME=3.1.4


install a package using channel::package syntax

    conda install CHANNELNAME::PKGNAME


install a package with a version range (AND logic)

    conda install "PKGNAME>2.5,<3.2"


install a package with version alternatives (OR logic)

    conda install "PKGNAME[version='2.5|3.2']"


view configured channel sources

    conda config --show-sources


add a channel

    conda config --add channels CHANNELNAME


set strict channel priority

    conda config --set channel_priority strict


list packages in a named environment with source info

    conda list -n ENVNAME --show-channel-urls


install packages into a named environment

    conda install -n ENVNAME PKG1 PKG2


remove a package from a named environment

    conda uninstall PKGNAME -n ENVNAME


update all packages in a named environment

    conda update --all -n ENVNAME


list revision history for an environment

    conda list -n ENVNAME --revisions


restore an environment to a previous revision

    conda install -n ENVNAME --revision NUMBER


uninstall a package from a specific channel in a named environment

    conda remove -n ENVNAME -c CHANNELNAME PKGNAME


export environment platform- and package-specific

    conda env export ENVNAME > ENV.yml


export environment with explicit channel and platform info

    conda list --explicit > ENV.txt


create environment from a .yml file

    conda env create -n ENVNAME --file ENV.yml


create environment from a .txt file

    conda create -n ENVNAME --file ENV.txt


get help for any command

    conda COMMAND --help


get detailed info for a package

    conda search PKGNAME --info


run a command without user confirmation prompts

    conda install PKG1 PKG2 --yes


examine full conda configuration

    conda config --show


