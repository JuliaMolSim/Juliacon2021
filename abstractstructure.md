# AbstractStructure.jl (name TBD)

Idea is to create a generalized interface that simulation packages could all hook into, potentially with multiple "backends" that use e.g. ASE, rdkit, etc.

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

    

  #### How are you doing this sort of thing in Julia right now (if you are)?

  What Julia packages already implement (parts of) this functionality? Could we "pull out" that functionality to be the beginning of another, more universal package?

  #### How do you do it in other languages?

  * ASE...
  * pymatgen
  * Atomsk

