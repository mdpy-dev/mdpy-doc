============
Unit system
============

In most of cases, **SI unit system** is frequently chosen to describe a physical quantity. However, the scale of MD simulation is much smaller then the SI unit system. In this case, using SI system to perform numerical operation like addition yields big **numerical error**.

To ensure the **convergence** and **accuracy** of simulation, most MD package chose a new unit system that comparable to the atomic scale. Here we list the **default unit system** used in MDPy.

.. list-table:: Unit system
   :header-rows: 1
   :align: center

   * - Dimension
     - SI
     - MDPy
     - SI/MDPy
   * - Length
     - m
     - angstrom
     - :math:`10^{-10}`
   * - Time
     - s
     - femtosecond
     - :math:`10^{-12}`
   * - Mass
     - kg
     - dalton
     - :math:`1.66\times10^{-27}`
   * - Temperature
     - kelvin
     - kelvin
     - :math:`1`
   * - Charge
     - coulomb
     - e
     - :math:`1.60\times10^{-19}`
   * - Amount of substance
     - mol
     - mol
     - :math:`1`

The other unit like energy and force are derived from the multiplation and division of the basic unit.

.. tip::
    To get more information of unit system of MDPy, check tutorial: :doc:`../tutorial/unit`