.. _Python package:

**************
Python package
**************

.. contents:: Table of Contents


.. _Package installation:

Installation
============

.. Important::

  We strongly recommand installing the Capybara package only in virtual environments.

  First, install Pipenv if you don't have it already:
  
  .. code:: console

    pip install pipenv
  
  Then, navigate to the project folder, create and activate a virtual environment:

  .. code:: console

    cd PATH-TO-THE-PROJECT-FOLDER
    pipenv install
    pipenv shell

  Once inside the virtual environment, follow the installation guide below.
  


Install the package **capybara-cophylogeny** via ``pip``:

.. code:: console

  python -m pip install capybara-cophylogeny


You can verify whether the installation is successful inside the Python interactive shell:

.. code:: console

  python

Import the two Capybara modules:

.. code:: console

   >>> import capybara.counter
   >>> import capybara.enumerator


The import statements should not yield any error.


.. Important::

  Be sure to update to the newest version if you have not used Capybara for a while:

  .. code:: console
  
    python -m pip install capybara-cophylogeny --upgrade


.. admonition:: Improve performance with PyPy

   You can **speed up the computation** by using PyPy3.6 instead of the standard CPython interpreters.
   To do this, follow these simple steps:

   1. `Download and install PyPy3.6 <https://www.pypy.org/download.html>`__.

   2. Create and activate the virtual environment using PyPy3 as interpreter:

     .. code:: console

       pipenv install --python=pypy3
       pipenv shell

   3. Already done! Python commands will now use PyPy3. For example, you can write:

      .. code:: console

        python -m pip install capybara-cophylogeny
        python MY_SCRIPT.py
   


Usage
=====

The user is assumed to be already familiar with the GUI version of Capybara.

The Python package provides two functions ``capybara.counter.run`` and ``capybara.enumerator.run``,
corresponding to the two buttons :guilabel:`Count` and :guilabel:`Enumerate` in :ref:`Optimal enumeration`.


Count: ``capybara.counter.run``
-------------------------------

The function takes 4 parameters (2 optional):

.. list-table::
   :widths: 10 40
   :header-rows: 1
   :stub-columns: 1

   * - Parameters
     -
   * - input_name
     - Name of the input file (or the path)
   * - task           
     - Integer between 1 and 4
   * - cost_vector    
     - List (or tuple) of four integers. **Default**: (-1,1,1,1)
   * - verbose        
     - If set to True, print a message when the computation starts and ends. **Default**: False


The function returns an integer, depending on the chosen task (see also :ref:`Enumeration tasks`):

.. list-table::
   :widths: 5 20
   :header-rows: 1
   :stub-columns: 1     

   * -
     - Return value
   * - task=1
     - Number of optimal reconciliations   
   * - task=2
     - Number of event vectors
   * - task=3
     - Number of event partitions
   * - task=4
     - Number of equivalence classes


Enumerate: ``capybara.enumerater.run``
--------------------------------------

The function takes 7 parameters (4 optional):

.. list-table::
   :widths: 10 40
   :header-rows: 1
   :stub-columns: 1

   * - Parameters
     -
   * - input_name
     - Name of the input file (or the path)
   * - output_name
     - Name of the output file (or the path)
   * - task           
     - Integer between 1 and 4
   * - cost_vector    
     - List (or tuple) of four integers. Default: (-1,1,1,1)
   * - verbose        
     - If set to True, print a message when the computation starts and ends. **Default**: False
   * - maximum
     - Maximum number of solutions to be outputted. **Default**: Infinity
   * - acyclic_only
     - If set to True and task=1, output only acyclic solutions. **Default**: False


The function does not return anything. It writes the output to the specified file, depending on the chosen task (see :ref:`Enumeration tasks`).
The output format is the same as in the GUI version.

For tasks 3 and 4, the output format corresponds to the option **Labels only** in the GUI version (see :ref:`Output options`).


Log file
--------

With the option **verbose**, only simple messages are printed to the console, at the start and the end of computation.

More detailed information (parameters used, time of computation, cause of error) can be found in the log file **capybara.log** in the working directory.

After a successful job, the user can find messages similar to the following at the end of the log file: ::

    2020-04-19 21:50:05,131 - capybara - INFO - ===== Job started! =====
    2020-04-19 21:50:05,131 - capybara - INFO - Running Capybara Counter Task 2
    2020-04-19 21:50:05,132 - capybara - INFO - Input file: /home/user/cophy/data/input1.nex
    2020-04-19 21:50:05,132 - capybara - INFO - Cost vector: (0, 1, 1, 1)
    2020-04-19 21:50:05,133 - capybara - INFO - Reading the input file...
    2020-04-19 21:50:05,134 - capybara - INFO - Successful! Computing...
    2020-04-19 21:50:05,162 - capybara - INFO - Done! The result of Counter Task 2 is 8
    2020-04-19 21:50:05,166 - capybara - INFO - ===== Job finished successfully! =====

A job interrupted by the user (for example, by pressing Ctrl+C) is also shown in the log file: ::

    2020-04-19 22:04:11,600 - capybara - INFO - ===== Job started! =====
    2020-04-19 22:04:11,600 - capybara - INFO - Running Capybara Enumerator Task 4
    2020-04-19 22:04:11,601 - capybara - INFO - Input file: /home/user/cophy/data/input1.nex
    2020-04-19 22:04:11,601 - capybara - INFO - Cost vector: (0, 1, 1, 1)
    2020-04-19 22:04:11,601 - capybara - INFO - Output file: /home/user/cophy/input1-classes.txt
    2020-04-19 22:04:11,601 - capybara - INFO - Reading the input file...
    2020-04-19 22:04:11,602 - capybara - INFO - Successful! Computing...
    2020-04-19 22:04:11,604 - capybara - WARNING - Keyboard interrupt
    2020-04-19 22:04:11,604 - capybara - INFO - ===== Job aborted! =====

The log file is automatically cleaned after 48 hours.


Examples
========

A simple example
----------------

Here is a simple script where we print the number of event vectors, for different cost vectors:

.. code:: python

    for cost_vector in [(-1,1,1,1), (0,1,1,1), (0,1,1,0), (0,2,3,1)]:
        num_vectors = capybara.counter.run('input.nex', task=2, cost_vector=cost_vector)

        print("Cost vector =", cost_vector)
        print("Number of event vectors =", num_vectors)


Multiprocessing on multiple input files
---------------------------------------

The user may want to use **more than one CPU unit** when working with a large number of files.

We propose below a script that uses **multiprocessing**. It follows three steps:

- Define a function that applies ``capybara.enumerator.run`` with parameters *task=4* and *cost_vector=(0,1,1,1)*
  on the given input file.
  The output file name is obtained by **adding a suffix** "0111_classes" to the input file name. 

- Get the list of all input files, located in the directory **data/**.

- Create a pool of 4 worker processes, and apply the function on the list of input files.

.. code:: python

    import os
    from multiprocessing import Pool
    import capybara.enumerator

    # define my custom function
    def my_function(input_name):
        output_name = '{name}_{suffix}.txt'.format(name=os.path.splitext(input_name)[0],
                                                   suffix='0111_classes')
        capybara.enumerator.run(input_name, output_name, task=4, cost_vector=(0,1,1,1))

    # getting all .nex files in the data folder
    nexfiles = [os.path.join('data', fname) for fname in os.listdir('data') 
                                            if fname.endswith('.nex')]

    # apply the function to the list of files
    with Pool(processes=4) as pool:
      pool.map(my_function, nexfiles)



  


