============
Overview
============

MDPy is a freely distributed Molecular Dynamics (MD) package based on **Python**, which is **GPU-accelerated** and licensed under the **BSD** License. It is designed to enable researchers with no prior experience in coding with C++ or Fortran to implement new theoretical models with GPU acceleration efficiently.

**Zhenyu Wei** (zhenyuwei99@gmail.com), from **Yunfei Chen**’s group in Southeast University, developed and maintains MDPy. As a newly developed program, we always welcome developers to contact us or discuss in our `Github site <https://github.com/mdpy-dev/mdpy>`_.

The document is organized in four parts:

1. **Quick start**: This section provides an introduction to our program and installation suggestions.
2. **Theory behind MDPy**: This section introduces the physical models and mathematical tricks implemented in MDPy.
3. **Tutorial**: This section provides basic example codes to give users a clear understanding of MDPy’s features and workflow.
4. **API reference**: This section gives a detailed description of all packages and classes of MDPy.

.. tip::

   We highly recommend that beginners of MD simulation read the "Theory behind MDPy" before utilizing MDPy.

.. tip::

   Once the user becomes familiar with MDPy, the "API reference" will be a useful resource for quickly checking their code.

============
Framework
============

.. figure:: ../_static/image/quick_start/framework.png
    :align: center

In MDPy, the main task of conducting a simulation is creating a well-defined :doc:`Ensemble <../api_reference/core/generated/mdpy.core.Ensemble>` object. An :code:`Ensemble` object includes all the information required for the MD simulation, such as:

- :doc:`Topology <../api_reference/core/generated/mdpy.core.Topology>`: This contains the particles' properties, such as atom type, mass, and charge, as well as other topological information like bonds, angles, and dihedrals.
- :doc:`State <../api_reference/core/generated/mdpy.core.State>`: This contains the **spatial coordinates** and **velocities** of each particle in the Topology. This information describes the coordinate of the Ensemble in the **phase space**. Additionally, State also includes information about the Periodic Boundary Condition (PBC) and Neighbor list.
- Constraints: This is a :code:`list` of :doc:`Constraint <../api_reference/constraint/index>` objects, each of which describes a specific interaction between particles. It returns the force on each particle and the potential energy of the Ensemble.

.. tip::

    MDPy also provides a higher-level API for creating typical :code:`Ensemble`, which is included in the :doc:`mdpy.recipe <../api_reference/recipe/index>` package.

The user can then perform operations on the :code:`Ensemble` object. MDPy supports two types of operators:

- :doc:`Minimizer <../api_reference/minimizer/index>`: Takes the :code:`Ensemble` object as input and **minimizes** the total **potential energy** of the :code:`Ensemble`.
- :doc:`Integrator <../api_reference/integrator/index>`: Takes the :code:`Ensemble` object as input and **integrates** the **forces** acting on each particle in a specific manner to sample the phase space.



============
Installation
============

**Beta version**


We strongly recommend installing MDPy from the **source code** for the beta version. First, you need to clone this repository to your local device:

.. code:: bash

    git clone https://github.com/mdpy-dev/mdpy.git


Then go to the path of mdpy, running:

.. code:: bash

    conda install --file requirements.txt -c defaults -c conda-forge
    conda develop .

Now, any changes made to the MDPy source code can be reflected in your code without needing to reinstall the MDPy package.

============
Performance
============

=========
Cite MDPy
=========

