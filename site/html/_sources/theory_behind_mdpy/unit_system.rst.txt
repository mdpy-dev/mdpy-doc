============
Unit system
============

In most cases, the **SI unit system** is frequently chosen to describe physical quantities. However, the scale of MD simulation is much smaller than the SI unit system. In this case, using the SI system to perform numerical operations like addition yields big **numerical errors**.

To ensure the **convergence** and **accuracy** of the simulation, most MD packages choose a new unit system that is comparable to the atomic scale. Here, we list the default unit system used in MDPy.

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
     - :math:`10^{10}`
   * - Time
     - s
     - femtosecond
     - :math:`10^{12}`
   * - Mass
     - kg
     - dalton
     - :math:`6.023\times10^{26}`
   * - Temperature
     - kelvin
     - kelvin
     - :math:`1`
   * - Charge
     - coulomb
     - e
     - :math:`6.24\times10^{18}`
   * - Amount of substance
     - mol
     - mol
     - :math:`1`

Other units, such as energy and force, are derived from the multiplication and division of the basic units.

.. tip::
    To get more information of unit system of MDPy, check tutorial: :doc:`../tutorial/unit`