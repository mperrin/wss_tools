.. _quip-installation:

Installation
============

.. note::

    The global installation of Anaconda and ``wss_tools`` (including QUIP)
    on ``wsslinux2`` is no longer available. It was previously created to get
    around the lack of Anaconda support at STScI, which is no longer the case.
    Please follow the instructions below to install your own copy.

Anaconda is the recommended Python distribution for ``wss_tools``.
If you do not have it already,
`download Anaconda <http://continuum.io/downloads>`_ and install it
(Python 3.5+ only). The instructions below
assume you do *not* want ``wss_tools`` in your default Anaconda environment
(``base``), but if you do want it, you can skip the part where you create a
new ``conda`` environment.

It is recommended that you obtain some of the dependencies from the STScI
`AstroConda <http://astroconda.readthedocs.io/en/latest/index.html>`_ channel.
(There are also additional setup/installation info specific to STScI machines
available at
`Anaconda at STScI <http://stsci-env.readthedocs.io/en/latest/>`_.)
To add the ``astroconda`` channel::

    conda config --add channels http://ssb.stsci.edu/astroconda

In a Bash shell, create a new ``conda`` environment for ``wss_tools`` using
Python 3 and then switch to that environment
(skip this if you want to use default ``base`` environment)::

    conda create -n wssenv python=3.7
    source activate wssenv

In the environment above, install the following dependencies directly from
Anaconda::

    conda install astropy
    conda install scipy
    conda install pyqt
    conda install matplotlib
    conda install pillow

In that same environment, install the following dependencies from the
AstroConda channel you added earlier::

    conda install ginga>=2.7
    conda install stginga>=1.0

.. warning::

    ``AboutQUIP`` and ``MosaicAuto`` are broken for Ginga 2.6.3,
    see https://github.com/spacetelescope/wss_tools/issues/25 .
    If you encounter this issue, use ``conda update ginga`` to update Ginga.

Now, you can install ``wss_tools`` using ``pip`` (there was a concious decision
not to include it in AstroConda)::

    pip install git+https://github.com/spacetelescope/wss_tools.git@master

Dependencies installed using ``conda install`` above can be updated from time
to time using ``conda update <packagename>`` command as needed. As for those
installed using ``pip``, use ``pip uninstall <packagename>`` to uninstall the
old version, and then ``pip install <updated_package_url>`` to install the new
version.

When you are done with ``wss_tools``, you can switch back to ``base`` Anaconda
environment by deactivating the ``wssenv`` environment (skip this if you are
using the default ``base`` environment)::

    source deactivate
