.. |EUCALPYT| image:: resources/eucalypt.png
   :height: 1em
   :target: http://eucalypt.gforge.inria.fr/

.. _Output visualization:

********************
Output visualization
********************

For visualizating reconciliations (symbiont tree drawn on top of the host tree), 
use `the original viewer <http://eucalypt.gforge.inria.fr/viewer.html>`__ for |eucalpyt|.

For visualizating event partitions or equivalence classes (colorings of the parasite tree with animation), 
use the `new animated web tool Quokka Viewer <https://observablehq.com/@heliow/tree-viewer>`__.


The Quokka visualizer tool takes two input formats generated from the third tab *Convert enumeration files for visualization* of the main Quokka tool:

- File input (DOT format) can be saved into the filesystem by clicking the :guilabel:`Save` button. This file needs to be uploaded into Quokka viewer
  after selecting the first upload method.

- Plain text input can be copied into the user's clipboard by clicing the :guilabel:`Copy` button. Then the clipboard content can be pasted into Quokka viewer.

  Note that the text area for copy-and-paste is hidden by default, and will only appear after the user selects the second upload method *Copy and paste text*.

.. note::
    When the Quokka app closes, the clipboard content will also be cleared. Therefore, if you choose the second upload method, *do not* close the main app while using the viewer.


