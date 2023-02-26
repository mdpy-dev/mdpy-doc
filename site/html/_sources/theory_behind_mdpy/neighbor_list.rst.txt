=============
Cell list
=============

Background
----------

In many cases, particles only interact with each other over short distances, and these interactions can be described using short-range potentials.

The Lennard-Jones potential is a common example of a short-range potential used to describe the Van der Waals interaction between particles.

.. math::
    :label: neighbor-list-eq-vdw

    U_{\text{vdw}}=\sum_{i\ne j}^{N_{\text{p}}}{4}\varepsilon _{ij}\left[ \left( \frac{\sigma _{ij}}{r_{ij}} \right) ^{12}-\left( \frac{\sigma _{ij}}{r_{ij}} \right) ^6 \right]


As shown in Eq :math:numref:`neighbor-list-eq-vdw`, the computation of pairwise interactions has a complexity that scales with the square of the number of particles, denoted as :math:`N_{\text{p}}`. This leads to a quadratic increase in computational cost as the number of particles increases. However, since only particles in close proximity to a given central particle have a significant effect on it, it is important to use a data structure that efficiently identifies the neighboring particles.

.. figure:: ../_static/image/cell_list/cell_list.png
    :align: center
    :width: 250

    Illustration of cell-list :cite:`cell-list-illstration-png`

The cell-list is a data structure commonly used in computational physics and chemistry simulations to efficiently compute pairwise interactions between particles in a system. It works by dividing the simulation domain into a grid of cells and assigning each particle to the cell that contains its position.

By doing this, particles in nearby cells are likely to interact with each other, while particles in distant cells are unlikely to interact. This reduces the number of pairwise interactions that need to be computed, resulting in a significant computational speedup.

Implementation
--------------

Cutoff radius
+++++++++++++



Memory coalescing
+++++++++++++++++++

.. figure:: ../_static/image/cell_list/coalsed-memory.png
    :align: center
    :width: 350

    Comparison between coalesced and uncoalesced memory accessing :cite:`cell-list-memory-coalesing-png`. "In this scenario, accessing memory in a coalesced manner requires only one request, whereas accessing memory in an uncoalesced manner requires 32 separate requests.

Memory coalescing is a technique used in computer systems to optimize memory access patterns and improve performance. It involves grouping memory requests from multiple threads or blocks of threads into larger, more contiguous requests.

When a GPU executes a kernel, it does so in parallel across many threads. These threads are grouped into blocks, and each block is assigned to a streaming multiprocessor (SM) on the GPU. When a thread needs to access memory, it issues a memory request. If multiple threads in a block issue memory requests for adjacent locations in memory, these requests can be combined into a single request that reads or writes a larger block of memory.

By grouping memory requests in this way, memory coalescing reduces the number of requests that need to be sent to memory, which can improve overall performance. It also helps to reduce memory bandwidth usage, which can be a bottleneck in GPU performance.

Space filling curve
+++++++++++++++++++


.. figure:: ../_static/image/cell_list/space_filling_curve.png
    :align: center
    :width: 550

    Illustration of the Hilbert curve :cite:`cell-list-space-filling-curve-png`.

A space-filling curve is a mathematical construct that maps a one-dimensional sequence of numbers to a two-dimensional or higher-dimensional space in a way that preserves locality. In other words, it is a curve that traverses a space in a way that maximizes the continuity of nearby points.

The idea behind space-filling curves is that they provide a way to traverse a multi-dimensional space in a linear order, which can be useful for indexing or searching large datasets. By mapping the points in a multi-dimensional space to a one-dimensional sequence, space-filling curves can reduce the overhead of accessing and processing data.

.. figure:: ../_static/image/cell_list/space-partition.png
    :align: center
    :width: 450

    Space partition result