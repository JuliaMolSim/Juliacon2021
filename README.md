# Juliacon 2021 BoF: Building a Chemistry and Materials Science Ecosystem in Julia

This repo contains some notes and records from this BoF session! PR's to update it are welcome, but please get involved with the conversations and development efforts too (see below)!

## Staying in touch

* [JuliaMolSim](https://juliamolsim.github.io) github org

* [Join our Slack workspace](https://join.slack.com/t/juliamolsim/shared_invite/zt-tc060co0-HgiKApazzsQzBHDlQ58A7g)

  

## Structures and interfaces

* A common interface for atoms, molecules, lattices, crystals ?
* Common parameters (structures, basis sets, ...) ?
* Interesting external packages to integrate (ASE, Chemfiles, MolSSI, Lammps, ...) ?
* Inter-code communication ?
* Your points here ...

### What is needed to specify a model in a "universal" way?
* AbstractStructure.jl? (maybe even this is not a good name)
    * What is needed?
        * atomic/particles positions
        * atomic/particles kind (not only atomic number if you want to support coarse-grained simulations, or different ions, or different isotopes, …)
        * periodic or not?
            * support different cell shapes for periodic systems (orthorhombic, triclinic, truncated octahedra?)
            * support partially periodic systems (e.g. periodic along x and y only)
        * Array of structs versus struct of arrays
        * Two representations and a dual interface?
    * existing packages: Molly.jl, JuLIP.jl, ... others ? 
    * atoms, flexible AtomType
    * boundary conditions / periodicity
    * connectivity?
        * multiple layers: bonds, residues, chains, groups, …
    * atomic properties (pseudos, basis set, velocities, extensible)
    * extensible for special cases (e.g. non-spherical particles/bodies, …)
    * associated visualization tools? yes please
    * Possible consumers
        * visualisation
        * IO
        * follow-up simulations (e.g. MD)
        * 'Periodic table data' - useful to have a canonical source of e.g. atom masses (there is: [PeriodicTable.jl](https://github.com/JuliaPhysics/PeriodicTable.jl))
       * DataBase of SMILES and Identifiers [ChemicalIdentifiers.jl](https://github.com/longemen3000/ChemicalIdentifiers.jl )
    * Possible implementations
        * ASE
        * chemfiles
        * RDKit ([RDKitMinimalLib.jl](https://github.com/eloyfelix/RDKitMinimalLib.jl) provides direct access to RKit without using PyCall)
    * Selling point / goals:
        * Composability between existing packages
        * Modularity rather than large and complicated packages
        * Automatic differentiation / sensitivity analysis through the full pipeline
        * Rapid development: Same code structure for simplified problems and full-fletched applications
        * Easy and unified introspection

* AbstractTrajectory.jl?
    * Representation of simulation time; tracking of atoms
    * Possible consumers: 
        * High performance molecular-dynamics trajectory analysis might be a good 'sell' for Julia's speed. See https://www.mdanalysis.org/ for the SOTA Python package.

* AbstractBasisSet.jl (also maybe not a good name? AbstractOrbitals.jl ?)
    * specifying basis sets, molecular orbitals, etc. in a transferable way...
    * https://cclib.github.io/ exists for reading (vacuum) calculations in Python
    * Simultaneous periodic electronic-structure (plane-waves, muffin-tin orbitals) & molecular vacuum methods (Gaussian Type Orbitals) ?
    * Possible consumers:
        * Post-HartreeFock Quantum-Chemistry methods
        * Quantum Monte-Carlo (molecular Hamiltonian)
        * Quantum chemistry by quantum computing (variational quantum eigensolvers, unitary coupled cluster etc.)

* AbstractAtomicPotentials.jl (also perhaps a terrible name) interface for interatomic potentials and force fields (AbstractForces.jl / AbstractPotential.jl / name?)
    * getting energies and forces from underlying force field
    * maybe taking inspiration/making sure it is compatible with existing force field sharing methods: [OpenKIM](https://openkim.org/), [OpenFF](https://openforcefield.org/), [MMSchema](https://molssi.github.io/mmschema/)

* General problems
    * Handling units
        * Julia needs new units packages which don't overuse types
        * This is way more general than chem/mat. sci. (agreed)


#### How are you doing this sort of thing in Julia right now (if you are)?
What Julia packages already implement (parts of) this functionality? Could we "pull out" that functionality to be the beginning of another, more universal package?

#### How do you do it in other languages?
* ASE...
* pymatgen
* Atomsk

