Analysis validation
===================

Search result data associated with an Analysis must be validated before being accessible by end-user for further interpretation. 
Data processing of Analysis data is a multi-step process. 

Analyses icons are color-coded based on their data processing status to help users to easily determine the validation level of each of them:
	- |validation_not_completed| : Protein annotation import not yet completed.
	- |validation_not_validated| : Data not yet validated.
	- |validation_partially_validated| : Data partially validated.
	- |validation_validated| : Data validated and reported.

.. |validation_not_completed| image:: img/analysis_validation_not_completed.gif
.. |validation_not_validated| image:: img/analysis_validation_not_validated.gif
.. |validation_partially_validated| image:: img/analysis_validation_partially_validated.gif
.. |validation_validated| image:: img/analysis_validation_validated.gif

.. note:: 
	Protein annotation import from the databank file(s) is not part of the validation process. 
	It is triggered as a background task immediately after search result data import. 
	This process can take several minutes depending on the number of proteins identified. 
	However, validated data cannot be reported (see the Reporting section below for more details) before protein annotation data import has been completed.

Automated peptide/protein validation
------------------------------------

FDR (False discovery rate) - based validation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

FDR-based validation is initiated at the data import step to filter out data below the corresponding threshold score (see :ref:`analysis_import`). 

Qualitative validation
^^^^^^^^^^^^^^^^^^^^^^

Comparative validation
^^^^^^^^^^^^^^^^^^^^^^

Validation templates
^^^^^^^^^^^^^^^^^^^^


Manual peptide/protein validation
---------------------------------

Peptides selection/exclusion
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Protein exclusion and filtering
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


Lower-scoring peptides activation
---------------------------------


Clear peptide/protein selections
--------------------------------


Sequence modification validation
--------------------------------

Phosphorylation sites validation with PhosphoRS
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**PhosphoRS** [1]_ is an algorithm used to determine phosphorylation positions on a peptide, based on its sequence and MS2 fragmentation spectrum. 
This tool is included into myProMS and can be used to correct imported phosphorylation data.
From “Process analyses” menu, select `Peptide/Protein Selection` process type, and click on ``Start PhosphoRS analysis``. 

The following form is then displayed:

<Figure phosphoRS form>

PhosphoRS parameters can be set in `PhosphoRS Analysis Rules` section:
- : 
- **Activation type**: select the fragmentation mechanism of the analysis instrument. PhosphoRS is optimized for each activation type.
- **Mass Deviation**: mass error tolerance when PhosphoRS matches experimental spectra with theoretical spectra.

Manual validation of modifications
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^



Validation traceability
-----------------------


Reporting
---------


.. [1] PhosphoRS: `T. Taus et al., J. Proteome Res., 2011 <http://pubs.acs.org/doi/abs/10.1021/pr200611n>`_