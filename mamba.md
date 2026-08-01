# mamba

drop-in faster replacement for conda — most conda commands work as-is

    mamba install numpy


create a new environment

    mamba create -n myenv python=3.11


install packages into an existing environment

    mamba install -n myenv pandas matplotlib


install from a specific channel

    mamba install -c conda-forge polars


update all packages in the active environment

    mamba update --all


recreate an environment from a YAML file (much faster than conda)

    mamba env create -f environment.yml


search for a package across channels

    mamba search scikit-learn


show dependency tree for a package

    mamba repoquery depends numpy


show what depends on a given package

    mamba repoquery whoneeds numpy


install micromamba (standalone, no base environment needed)

    "${SHELL}" <(curl -L micro.mamba.pm/install.sh)


create an environment with micromamba without activating base

    micromamba create -n myenv python=3.11 numpy -c conda-forge
    micromamba activate myenv


