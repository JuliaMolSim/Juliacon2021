# Juliacon 2021 BoF: Building a Chemistry and Materials Science Ecosystem in Julia

This repo contains some notes and records from this BoF session! PR's to update it are welcome, but please get involved with the conversations and development efforts too (see below)!

## Staying in touch

* [JuliaMolSim](https://juliamolsim.github.io) github org
* [Join our Slack workspace](https://join.slack.com/t/juliamolsim/shared_invite/zt-tc060co0-HgiKApazzsQzBHDlQ58A7g)

## General Problems

* Handling units
  * Julia needs new units packages which don't overuse types
  * This is way more general than chem/mat. sci. (agreed)

## Structures and interfaces

* A common interface for atoms, molecules, lattices, crystals ?
* Common parameters (structures, basis sets, ...) ?
* Interesting external packages to integrate (ASE, Chemfiles, MolSSI, Lammps, ...) ?
* Inter-code communication ?

### What is needed to specify a model in a "universal" way?

Several concepts for generic interfaces were proposed, which I've split out into separate documents...

* [AbstractStructure.jl](abstractstructure.md)
* [AbstractTrajectory.jl](abstracttrajectory.md)
* [AbstractBasisSet.jl](abstractbasisset.md)
* [AbstractAtomicPotentials.jl](abstractatomicpotentials.md)

    

