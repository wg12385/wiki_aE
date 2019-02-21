.. _scripts:


***************
Scripts
***************

.. _details_on_scripts:

Details on each script in auto-ENRICH
=========================================

**check_library.sh**

This is just a one line github command to fetch the latest versions of the nmr_processing library and scripts

**move_complete.py**
  This script checks the folders optcom and nmrcom for finished gaussian calculations and copies them into output folders. Successful calculations are moved into the optlog or nmrlog folders, others are put into a failed folder.


xyz_to_opt.py

This script takes the specified .xyz file in your current folder and converts the contained structures into Gaussian com files for optimising the structures, using the preferences contained in ENRICH.prefs. It also produces a submission script and accompanying COM_ARRAY file which is just a list of the com files for submission.

If the .xyz file contains a numbering system (eg if you're doing a population cull after 'cheap' DFT from opt_cull.py) then giving it the argument 'track' after the xyz file will get it to keep the numbering system

.. code-block:: bash

   python ~/auto-ENRICH/RUN/xyz_to_opt.py mymolecule.xyz track
   # Will keep numbering system in xyz file



opt_to_nmr.py

This script takes the optimisation log files and converts the contained structures into gaussian com files for NMR calculation, using the preferences contained in ENRICH.prefs. Optionally it performs redundant conformer elimination to remove conformers which have optimised to the same structure. It also produces a submission script and accompanying COM_ARRAY file which is just a list of the com files for submission.

nmr_process.py

This script takes gaussian NMR log files as well as the population file created by the opt_to_nmr.py script and creates a DATA_output file containing boltzmann weighted scalar coupling and chemical shifts. It also produces an .xyz file from each conformer. You shouldn't need to change anything in this script unless you've altered file naming conventions from the previous scripts, it will look for gaussian log files in 'nmrlog/*.log' and a file called population_information.txt

.. _nmr_processing_explanation:

Details on each script in NMR processing
=========================================
