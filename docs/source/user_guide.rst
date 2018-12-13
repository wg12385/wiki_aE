.. _user_guide:


***************
User Guide
***************


.. _basics:

Basics
===================================

Commands you need to type into your terminal window (after logging in to BlueCrystal) are written in block quotes as below. Notes are preceeded by a #:

.. code-block:: bash

   type_this_into_terminal_window
   #Helpful extra instructions, do not type this into the terminal window


.. _install_bc3:

Install BlueCrystal3 step by step
===================================

**0** Get IT to allow you to use Gaussian on BlueCrystal, email hpc-help@bristol.ac.uk asking them to set up and give your account access to use Gaussian

**1** Get read access to this repository (email will.gerrard@bristol.ac.uk with your github account details or request access through github)

**2** Set up your environment:

   **2.1** Load the conda module

       .. code-block:: bash

         module load languages/python-anaconda-5.0.1-2.7

   **2.2** Create a conda environment

      .. code-block:: bash

         conda create --name myenv

   **2.3** Install openbabel and numpy

      .. code-block:: bash

         conda install -c openbabel -n myenv openbabel
         conda install -n myenv numpy scipy

   **2.4** Activate the environment you just made, this should put add "(myenv)" to the far left of where you input Commands

       .. code-block:: bash

         source activate myenv

**3** Set up Github and get a copy of auto-ENRICH:

   **3.1** Find your ssh key, we do this by first going to your home folder in BlueCrystal then opening .ssh/id_dsa.pub (a text file) containing your key

      .. code-block:: bash

         vim .ssh/id_dsa.pub

      .. figure::  _static/sshkey.png

         Example ssh key

   **3.2** Copy the key (all that text) then type :q! to exit

      .. code-block:: bash

        :q!
        #Close file

   **3.3** Login to Github.com then go to Settings - SSH and GPG keys - New SSH key and paste the key and give it a simple title like BlueCrystal3

      .. figure::  _static/ssh_github.png

         Navigate through github.com to input ssh key

   **3.4** Enable git

      .. code-block:: bash

         module load tools/git-2.18.0

   **3.5** Copy auto-ENRICH files, it'll make a folder called auto-ENRICH containing all the files

      .. code-block:: bash

        git clone --recurse-submodules git@github.com:wg12385/auto-ENRICH.git

**4** Automatically set up things so when you log in to be able to run auto-_ENRICH. If you don't want to do this type the commands in step **4.2** into your terminal everytime you want to run auto-ENRICH

  **4.1** Open .bashrc, this is a script that runs automatically when you log in to BlueCrystal3

      .. code-block:: bash

        vim .bashrc

  **4.2** Tell BlueCrystal to automatically load python and git and then activate your conda environment.

      .. code-block:: bash

        module load languages/python-anaconda-5.0.1-2.7
        module load tools/git-2.18.0
        source activate myenv

**5** Start using auto-ENRICH

  auto-ENRICH automates moving from a conformational search output to getting out NMR parameters. Save the output of your conformational search to one .xyz file (that contains lots of conformers) for a particular molecule

  **5.1** Make a folder with the molecule name and put your .xyz file in it, cd into that folder

  **5.2** Copy the preferences file from the auto-ENRICH folder then open it and decide what you want to run. If the auto-ENRICH folder is 2 directories above your molecules folder (which you are now in) type:

     .. code-block:: bash

      cp -rf ../../auto-ENRICH/ENRICH.prefs ./
      #The cp means copy, first place is where it's copying from,
      #the other is where its copying to, your current directory
      #If its more/less folders above use more/less ../'s before the auto-ENRICH
      #This applies for all that follows


  **5.3** Edit the preferences

    .. code-block:: bash

       vim ENRICH.prefs
       #Press the i key then edit the file
       :wq
       #Save and then close the file

  **5.4** Create geometry optimisation and frequency correction input files for Gaussian based on your choices in ENRICH.prefs by running xyz_to_opt.py script from the folder containing your .xyz file

     .. code-block:: bash

        python ../../auto-ENRICH/RUN/xyz_to_opt.py

  



--------------------------------

.. _install_grendel:

Install Grendel step by step
====================================





.. _faq:

FAQ
=============================
