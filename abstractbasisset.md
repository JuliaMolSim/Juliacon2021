# AbstractBasisSet.jl (also maybe not a good name? AbstractOrbitals.jl ?)

* specifying basis sets, molecular orbitals, etc. in a transferable way...
* https://cclib.github.io/ exists for reading (vacuum) calculations in Python
* Simultaneous periodic electronic-structure (plane-waves, muffin-tin orbitals) & molecular vacuum methods (Gaussian Type Orbitals) ?
* Possible consumers:
  * Post-HartreeFock Quantum-Chemistry methods
  * Quantum Monte-Carlo (molecular Hamiltonian)
  * Quantum chemistry by quantum computing (variational quantum eigensolvers, unitary coupled cluster etc.)