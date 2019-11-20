.. NewEucalypt documentation master file, created by
   sphinx-quickstart on Thu Sep 19 18:09:51 2019.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. |EUCALPYT| image:: resources/eucalypt.png
   :height: 1em
   :target: http://eucalypt.gforge.inria.fr/


Welcome to Quokka's documentation!
=======================================

Quokka has some features in common with its predecessor |EUCALPYT| [1]_: counting the number of optimal reconciliations, listing optimal reconciliations to a file, keeping only the acyclic ones (the definition of cyclicity is taken from [2]_).


.. sidebar:: Wow! New features!

    .. image:: resources/quokka.jpg

Quokka also has some **exciting new features**: 

- Counting and enumeration of even vectors, event partitions, equivalence classes (see the :ref:`Enumeration tasks` in :ref:`Optimal enumeration`)

- Enumeration of suboptimal reconciliations (see :ref:`Suboptimal enumeration`)

- Animated visualization of event partitions and equivalence classes (see :ref:`Output visualization`)

Download
--------
`Click here to get Quokka <https://github.com/Helio-Wang/Quokka-app/releases/latest>`__.


.. toctree::
   :caption: Documentation
   :maxdepth: 2

   enumeration
   suboptimal
   visualization


References
----------

.. [1] Beatrice Donati, Christian Baudet, Blerina Sinaimeri, Pierluigi Crescenzi, and Marie-France Sagot. Eucalypt: efficient tree reconciliation enumerator. 
       *Algorithms for Molecular Biology*, 10(1):3, 2015. doi: 10.1186/s13015-014-0031-3.

.. [2] Maureen Stolzer, Han Lai, Minli Xu, Deepa Sathaye, Benjamin Vernot, and Dannie Durand. Inferring duplications, losses, transfers and incomplete lineage sorting with nonbinary species trees. 
       *Bioinformatics*, 28(18):i409–i415, 2012. doi: 10.1093/bioinformatics/bts386.


