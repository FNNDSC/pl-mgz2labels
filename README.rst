pl-mgz2labels
================================

.. image:: https://travis-ci.org/FNNDSC/mgz2labels.svg?branch=master
    :target: https://travis-ci.org/FNNDSC/mgz2labels

.. image:: https://img.shields.io/badge/python-3.8%2B-blue.svg
    :target: https://github.com/FNNDSC/pl-mgz2labels/blob/master/setup.py

.. contents:: Table of Contents


Abstract
--------

MGZ label-wise converter


Description
-----------

``mgz2labels`` is a ChRIS-based application whose backbone is `pl-mgz_converter <https://github.com/FNNDSC/pl-mgz_converter>`_. The input file structure is the same as pl-mgz_converter. The output will be 193 labels for each subject in separated folder, and 193 .npy files for each label. The output of this plugin is set to be used for `pl-mricnn <https://github.com/FNNDSC/pl-mricnn>`_ training.

For training purpose, the real label index (`can be found here <https://github.com/FNNDSC/pl-mgz2LUT_report/blob/master/mgz2lut_report/FreeSurferColorLUT.txt>`_) will be convert to values between (0 ~ 255) based on a `label LUT <https://github.com/FNNDSC/pl-mgz2labels>`_.

Usage
-----

.. code::

    python mgz2labels.py
        [-h|--help]
        [--json] [--man] [--meta]
        [--savejson <DIR>]
        [-v|--verbosity <level>]
        [--version]
        <inputDir> <outputDir>

Using Python3
~~~~~~~~~~~~

.. code::
    python3 mgz2labels/mgz2labels.py <inputDir> <outputDir>

Using ``docker run``
~~~~~~~~~~~~~~~~~~~

.. code:: bash
    docker build -t mgz2labels .

.. code:: bash

    docker run --rm -v $(pwd)/in:/incoming -v $(pwd)/out:/outgoing                              \
        mgz2labels mgz2labels.py                                    \
        /incoming /outgoing


Development
-----------

Build the Docker container:

.. code:: bash

    docker build -t mgz2labels .

.. code:: bash

    docker run --rm -v $(pwd)/in:/incoming -v $(pwd)/out:/outgoing                              \
        mgz2labels mgz2labels.py                                    \
        /incoming /outgoing

Examples
--------

.. code:: bash

    docker build -t mgz2labels .

.. code:: bash

    docker run --rm -v $(pwd)/in:/incoming -v $(pwd)/out:/outgoing                              \
        mgz2labels mgz2labels.py                                    \
        /incoming /outgoing


Trouble Shooting
--------
Try to remove all ``.DS_Store`` files in the input directory
