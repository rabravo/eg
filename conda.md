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


export an environment to a YAML file

    conda env export > environment.yml


recreate an environment from a YAML file

    conda env create -f environment.yml


delete an environment

    conda env remove -n myenv


search for a package

    conda search numpy


clean unused packages and caches

    conda clean --all


