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

- Replace **FairShip/python/shipStrawTracking.py** with **src/shipStrawTracking.py** from this repository.
- Run tracks pattern recognition on the simulated MC sample:
```bash
python $FAIRSHIP/macro/ShipReco.py -f ship.conical.Pythia8-TGeant4.root -g geofile_full.conical.Pythia8-TGeant4.root --realPR=FH
```
The PatRec output files:

recohists.root  
ship.conical.Pythia8-TGeant4_rec.root

- Run PatRec metric calculation:
```bash
python $FAIRSHIP/python/shipStrawTracking.py -f "ship.conical.Pythia8-TGeant4_rec.root" -g "geofile_full.conical.Pythia8-TGeant4.root" -o 'output.root'
```
The output file:
output.root

- Open **output.root** and look for **TracksPassedU** histogram. 
