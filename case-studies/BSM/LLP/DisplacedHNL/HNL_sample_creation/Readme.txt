Author: Suchita Kulkarni
Contact: suchita.kulkarni@cern.ch

This folder will allow you to create your own madgraph sample for heavy neutral lepton decaying to e j j final state.

In order to create the sample you will need to create an LHE file using standalone madgraph installation. This LHE file is then input for pythia + delphes run. Pythia + delphes is run together by DelphesPythia8_EDM4HEP. Therefore you do not need to create a pythia output seperately. 

Please download madgraph version seperately and use the mg5_proc_card.dat from this directory to create your process. You can use the command 
./bin/mg5_aMC < mg5_proc_card.dat to create and LHE file. 

If you wish to create a sample where the HNL decays to e e nu final state change the following lines in mg5_proc_card.dat

generate e+ e- > ve n1, (n1 > e j j)
add process e+ e- > ve~ n1, (n1 > e j j)

to

generate e+ e- > ve n1, (n1 > e e nu)
add process e+ e- > ve~ n1, (n1 > e e nu)

The resulting events will be stored in  HNL_ljj/Events/run_01/unweighted_events.lhe.gz file.

Unzip it and give the path to HNL_pythia.cmnd file to generate the delphes root file.

To create delphes root file you need to do the following on your command line:

source /cvmfs/fcc.cern.ch/sw/latest/setup.sh
DelphesPythia8_EDM4HEP $DELPHES_DIR/cards/delphes_card_IDEAtrkCov.tcl edm4hep_output_config.tcl HNL_pythia.cmnd HNL_ejj.root

the resulting HNL_ejj.root is your EDM sample.
