Validated proteins
==================

Match groups and protein visibility
-----------------------------------

**Match groups** are a key feature in myProMS. 
Understanding and setting properly the rules that control match group organization and protein visibility is essential for accurate data analysis and interpretation.

Because the shotgun mass spectrometry technique (used to generate all Analysis data) allows to identify peptides and not protein, multiple proteins can be matched with the same (set of) peptides. 
This creates an inherent ambiguity on the identity of the proteins contained in the extract analysed. myProMS deals with this problem by organizing the proteins identified in match groups representing groups of proteins sharing the same (sub-)set of peptides. 

To avoid protein inflation, by default **only 1 (top) protein per match group is made visible** and all other will be hidden (not considered as identified in the sample studied). 
The top protein is also used as **alias** for the match group. Only visible proteins are considered as present in the sample analyzed. 
Hidden proteins will not be listed (unless the user specifies otherwise) and not used in all subsequent data processing such as protein quantification or Gene Ontology analyses.

Top protein selection rules
^^^^^^^^^^^^^^^^^^^^^^^^^^^

For each match group, myProMS attempts to set the protein most likely identified by the corresponding set of peptides as top protein using the following rules sequentially until only 1 protein remains:

	1.	The protein is matched by all peptides in the set.
	2.	\*The protein is the most often found as top proteins in previously validated analyses.
	3.	The best scoring protein among those meeting the previous criteria.
	4.	The protein with best sequence coverage among those meeting the previous criteria.
	5.	The best annotated protein among those meeting the previous criteria. Annotation quality is estimated as follows:
	
		a.	SwissProt identifier.
		b.	trEMBL identifier.
		c.	None of the following keywords found in the protein description.
		d.	The hypothetical keyword is found in the protein description.
		e.	The unknown or unnamed keywords are found in the protein description.
		f.	The protein description is missing.
	   
	6.	the shortest protein among those meeting the previous criteria.
	7.	the protein with identifier first in alphabetic order.
	
*\* myProMS will preferentially select a protein that has been identified often in previous samples.*

Project-wide protein visibility rules
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

By default, only the top protein of each match group is visible. However, the user can use 1 of 3 predefined project-wide protein visibility rules to alter this default behavior. 
Edit the corresponding project. The following section is part of the edition form:

<Figure protein visibility rules in project edition form>

These rules are self-explanatory and ordered by decreasing stringency. 
Selecting rule #2 or #3 will alter myProMS default behavior and can potentially lead to multiple visible proteins per match group. 
Click on ``Save`` to validate your changes. 
Visibility of all identified proteins will re-evaluated based on the rule selected except if involved in quantifications or GO analyses. 
Keep also in mind that *protein lists* and *saved comparisons* (see :ref:`save_comparison`) can be modified by the resulting changes in protein visibility.

Checking for conflicting match groups
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

It is possible to check for inconsistency in match groups across multiple analyses; meaning to detect proteins with inconsistent visibility (visible vs hidden) across multiple analyses.
From the Summary view of any project item containing at least 2 validated analyses, click on the ``Scan for conflicts`` button right of the number of visible/total proteins validated. 
A list of such proteins (if any) will be displayed with the number of analyses where each protein is found visible or hidden as shown in figure below.

<Figure list conflicts>

Click on the ``[+]`` icon to display the list of the analyses involved. From this list, you can either:
	- Edit a specific match group by selecting an analysis (radio list) and clicking on the ``Edit match group`` button at the top of the table (see :ref:`manual_edition`).
	- Display detailed information on a protein in the context of the analysis of your choice by directly clicking on that analysis’ name.

Displaying match group composition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

*List Proteins* at Analysis-level (see :ref:`project_lists`) and check ``Show Match groups`` at the top of the list. 
Click on the ``[+]`` icon next to the alias protein identifier to display the content of the match group. 
No ``[+]`` icon indicates that the protein is alone in its group. As shown in the screen capture below, visible proteins are listed in bold while hidden ones appear in light font.


<Figure match group in protein list>

.. _manual_edition:

Manual edition
^^^^^^^^^^^^^^

Aside from project-wide protein visibility rules, any match group can be manually edited to modify the top protein selection as well as the visibility of any protein in the group. 
Modification is allowed only if corresponding analysis is not associated with protein quantifications nor GO analyses. 
Click on the ``Edit Match Group`` button at the bottom of the match group list to enter editing mode.

<Figure edit Match group part 1)>

In *part 1)* of the form, the top (alias) protein can be changed and any other protein can be made visible meaning that you believe they are indeed present in the biological sample analysed.

<Figure edit Match group part 2) & 3)>

In *part 2)* of the form, you can propagate the changes made in *part 1)* upward in the project tree. 
You can chose to propagate independently the alias, visible and hidden protein selection.

Finally, *part 3)* lets you decide whether your changes can contradict or not the current project-wide protein visibility rule.
If this option is unchecked, any changes made that do not agree with  the project-wide rule will be ignored.
Click on ``Proceed`` to validate your changes.

Peptide distribution in match group
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

It is possible to visualize graphically the set of peptides of the match group and where they match each protein sequence. To do so, click on the “Peptide Distribution” button at the bottom of the match group list.

<Figure Peptide distribution in MG>

See ``Peptide Distribution`` in :ref:`single_prot_view` for more information on how to interpret the displayed data.


Identifier mapping
------------------


.. _single_prot_view:

Single protein view
-------------------
