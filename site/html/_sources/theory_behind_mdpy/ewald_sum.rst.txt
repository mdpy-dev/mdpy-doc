===================
Ewald summation
===================

Background
----------

.. figure:: ../_static/image/ewald_sum/screening.png
    :align: center
    :width: 550

    Illustration of ewald summation :cite:`ewald-sum-illstration`

.. math::
    \begin{equation}
    \begin{cases}
        \displaystyle \phi _{\text{G}}(r)=\frac{q}{4\pi \varepsilon _0r}\text{erf(}\alpha r\text{),erf(}x)=\frac{2}{\pi ^{\text{1/}2}}\int_0^x{\text{e}^{-x^2}}\text{d}x \\\\
        \displaystyle \phi _{\delta}(r)=\frac{q}{4\pi \varepsilon _0r}
    \end{cases}
    \label{equation}
    \end{equation}
    :label: euler

PME :cite:`ewald_sum_pme_01,ewald_sum_pme_02`, Particle-Particle Particle Mesh :cite:`ewald_sum_p3m_01,ewald_sum_p3m_02` (PPPM or P3M) method


Particle Mesh Ewald
-------------------


Bspline interpolation
++++++++++++++++++++++