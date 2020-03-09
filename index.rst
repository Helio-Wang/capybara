.. Capybara documentation master file, created by
   sphinx-quickstart on Thu Sep 19 18:09:51 2019.
   
   
.. meta::
   :msvalidate.01: 00DE8CC6EEBE9941840E43A3686907F7
   :google-site-verification: SEhBIjCGSQTdPVBknOqimgfKw1AVFhBf-rudiaTXWUE


.. |EUCALPYT| image:: resources/eucalypt.png
   :height: 1em
   :target: http://eucalypt.gforge.inria.fr/


Welcome to Capybara's documentation!
=======================================

Capybara is a desktop application for solving the **Phylogenetic tree reconciliation problem**.

**Keywords**: Cophylogeny reconstruction, phylogenetic tree reconciliationm, enumeration.


.. toctree::
   :caption: Documentation
   :maxdepth: 2

   installation
   enumeration
   suboptimal
   visualization


Overview
--------

**Phylogenetic tree reconciliation** is the method of choice in analyzing host-symbiont systems. Despite the many reconciliation tools that have been proposed in the literature, two main issues remain unresolved: 

- listing **suboptimal** solutions (i.e., whose score is “close” to the optimal ones), and

- listing only solutions that are **biologically different “enough”**. 

The first issue arises because the optimal solutions are not always the ones biologically most significant; providing many suboptimal solutions as alternatives for the optimal ones is thus very useful. The second one is related to the difficulty to analyze an often huge number of optimal solutions.

Capybara addresses both of these problems in an efficient way. Furthermore, it includes a tool for visualizing the solutions that significantly helps the user in the process of analyzing the results.


Features
--------

Capybara has some features in common with its predecessor |EUCALPYT| [1]_: counting the number of optimal reconciliations, listing optimal reconciliations to a file, keeping only the acyclic ones (the definition of cyclicity is taken from [2]_).


.. sidebar:: Wow! New features!

    .. image:: resources/Capybara1.jpg

Capybara also has some **exciting new features**: 

- Counting and enumeration of even vectors, event partitions, equivalence classes (see the :ref:`Enumeration tasks` in :ref:`Optimal enumeration`)

- Enumeration of suboptimal reconciliations (see :ref:`Suboptimal enumeration`)

- Animated visualization of event partitions and equivalence classes (see :ref:`Output visualization`)



References
----------

.. [1] Beatrice Donati, Christian Baudet, Blerina Sinaimeri, Pierluigi Crescenzi, and Marie-France Sagot. Eucalypt: efficient tree reconciliation enumerator. 
       *Algorithms for Molecular Biology*, 10(1):3, 2015. doi: 10.1186/s13015-014-0031-3.

.. [2] Maureen Stolzer, Han Lai, Minli Xu, Deepa Sathaye, Benjamin Vernot, and Dannie Durand. Inferring duplications, losses, transfers and incomplete lineage sorting with nonbinary species trees. 
       *Bioinformatics*, 28(18):i409–i415, 2012. doi: 10.1093/bioinformatics/bts386.


