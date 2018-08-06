# Optimization of the SHiP Spectrometer Tracker geometry

# Manual instructions
- Install FairShip using instructions https://github.com/ShipSoft/FairShip. We take the branch with updated MC simulation https://github.com/DaniilSu/FairShip/tree/optimal-geometry. 
- Change geometry parameters in **FairShip/geometry/geometry_config.py** file.
- Run MC simulation of 1000 events, for an example:
```bash
python $FAIRSHIP/macro/run_simScript.py --caloDesign=3 --tankDesign=6 --muShieldDesign=9 --nuTauTargetDesign=3 --nEvents 1000
```
The simulation output files: 

geofile_full.conical.Pythia8-TGeant4.root  
pythia8_conf.txt  
ship.conical.Pythia8-TGeant4.root  
ship.params.conical.Pythia8-TGeant4.root
