## Conda Buildpack

This is a Buildpack for [Conda](http://conda.pydata.org/), the Python distribution for scientific computing by Continuum Analytics.

This buildpack enables the installation of binary packages through the open source [conda](http://conda.pydata.org/) application.  Conda is recognized as being core to Continuum's Anaconda Scientific Python distro but it's also at the heart of the lighter weight [Miniconda](http://conda.pydata.org/miniconda.html) distro which we use here to install _only_ the binary packages we need for our apps deployed on [PaaS](https://en.wikipedia.org/wiki/Platform_as_a_service) platforms like [Heroku](https://www.heroku.com/) and [Dash Deployment Server](https://plot.ly/dash/pricing/).

### Usage and files needed

#### conda requirements

To control what binary packages are installed by conda, supply a `conda-requirements.txt` file.

#### pip requirements

Like when using the standard `buildpack` for python from Heroku, you can also still supply a `requirements.txt` file for [pip](https://github.com/pypa/pip) to process.
This allows you to install binary packages via `conda` when possible and still use pip for packages that are not available via `conda`.

#### .condarc configuration file

A [`.condarc` configuration file](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/use-condarc.html) can be added to the root of the app, this file will be detected and used to build and run the conda app. This can be useful for a number of things as described in the official conda documentation linked to earlier in this paragraph, including [using a proxy](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/use-condarc.html#configure-conda-for-use-behind-a-proxy-server-proxy-servers) for conda installs and [using conda channels other than the default one](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/use-condarc.html#channel-locations-channels).

