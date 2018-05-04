SIPs (Shift-and-Invert Parallel spectral transformations) originally
refers to Zhang _et. al._ implementation of a parallel spectrum slicing eigensolver for real and symmetric generalized eigenvalue problems.<sup>1</sup>
Motivated by material science and quantum chemistry applications, SIPs was built on top of [PETSc](https://www.mcs.anl.gov/petsc/)<sup>2</sup> and
[SLEPc](http://slepc.upv.es/)<sup>3</sup> libraries and it solves the eigenvalue problem with distributed spectrum slicing method. 2007 implementation<sup>1</sup> took care of organizing subgroups of MPI communicators, selection of the shifts, bookkeeping and validation of eigensolutions, and balancing parallel workload while relying on PETSc and SLEPc interfaces to [MUMPS](http://mumps.enseeiht.fr/)<sup>4</sup> and [ARPACK](http://www.caam.rice.edu/software/ARPACK/)<sup>5</sup> for parallel direct solver and
shift-and-invert Krylov subspace implementations, respectively.

In 2012, SLEPc developers Carmen Campos and Jose E. Roman created a new implementation of
the single-communicator spectrum slicing method in SLEPc using Krylov-Schur instead of ARPACK.<sup>6</sup> In 2014, a new version of SIPs was implemented based on the new solver in SLEPc and Keçeli _et. al._ demonstrated the scalability beyond 200,000 cores for matrices with more than 500,000 rows using Argonne's Leadership supercomputers.<sup>6</sup> In this study [PT-Scotch](https://www.labri.fr/perso/pelegrin/scotch/)<sup>8</sup>
was used for parallel sparse matrix block ordering, which offered better strong scaling performance in symbolic factorization.

In 2016, Carmen Campos and Jose. E. Roman implemented multiple-communicator spectrum-slicing method in SLEPc providing a more robust and generally applicable eigensolver with an intuitive and
well-documented API. In collaboration with Fabiano Corsetti and SLEPc developers, M. Keçeli integrated this solver into a branch of an ab initio molecular dynamics package [SIESTA](https://departments.icmab.es/leem/siesta/).
Keçeli _et. al._ demonstrated improved performance of the spectrum slicing eigensolver (referred to as SLEPc-SIPs) compared to default ScaLAPACK eigensolver for various types of problems. In this study, new methods are implemented in this interface to improve load-balance by adjusting slice boundaries based on approximate knowledge of the eigenvalues.

An interface to SLEPc spectrum slicing (SLEPc-SIPs) eigensolver has been also added to [ELSI](https://wordpress.elsi-interchange.org/) by Victor
Yu in collaboration with Murat Keçeli. This interface allows an easier integration of the spectrum slicing eigensolver into other electronic structure codes.


## How to use?
The most recent implementation of the multi-communicator spectrum slicing eigensolver is available in [SLEPc](http://slepc.upv.es/) library. SLEPc also contains many other scalable eigensolvers for linear or nonlinear eigenvalue problems and all are accessible for C, C++ and Fortran codes.


## Acknowledgements
This study is based upon work supported by Laboratory Directed Research and Development (LDRD)
funding from Argonne National Laboratory, provided by the Director, Office of Science,
of the U.S. Department of Energy under Contract No. DE-AC02-06CH11357.

2006-2007 SIPs work was supported by an LDRD project led by Peter Zapol.
2014-2017 SIPs work was supported by an LDRD project led by Albert F. Wagner.
The work of C. Campos and J. E. Roman was supported by the Spanish Ministry of Economy and Competitiveness under grant TIN2016-75985-P (including European Commission FEDER funds).


## References
1. Zhang, H.; Smith, B.; Sternberg, M.; Zapol, P. 2007. SIPs: Shift-and-Invert Parallel Spectral Transformations.
ACM Trans. Math. Softw., 33, 9–es.
[DOI=10.1145/1236463.1236464](doi.org/10.1145/1236463.1236464)
2. Balay, S., Buschelman, K., Eijkhout, V., Gropp,W., Kaushik, D., Knepley, M., Mcinnes, L.C., Smith, B., and Zhang,H. 2006. PETSc users manual. Tech. Rep. ANL 95/11—Revision 2.3.1, Argonne National Laboratory.
3. Hernandez, V., Roman, J. E., and Vidal, V. 2005. SLEPc: A scalable and flexible toolkit for the solution of eigenvalue problems. ACM Trans. Math.
Softw. 31, 351-362. [DOI=10.1145/1089014.1089019](doi.org/10.1145/1089014.1089019)
4. Amestoy, P.R.; Duff I.S.; and L’excellent, J.-Y. 2000. Multifrontal parallel distributed symmetric and unsymmetric solvers. Comput. Meth. Appl. Mech. Eng. 184, 501–520.
Soft. 31, 3 (Sept.), 351–362.
5. Lehoucq, R.B.; Sorensen, D.C.; and Yang, C. 1998. ARPACK Users’ Guide: Solution of Large- Scale Eigenvalue Problems with Implicitly Restarted Arnoldi Methods. SIAM, Philadelphia.
6. Campos, C.; Román, J. E.
Strategies for Spectrum Slicing Based on Restarted Lanczos Methods.
Numer. Algorithms 2012, 60, 279–295.
[DOI=10.1007/s11075-012-9564-z](doi.org/10.1007/s11075-012-9564-z)
7. Keçeli, M.; Zhang, H.; Zapol, P.; Dixon, D. A.; Wagner, A. F.
Shift-and-Invert Parallel Spectral Transformation Eigensolver:
Massively Parallel Performance for Density-Functional Based
Tight-Binding. J. Comput. Chem. 2016, 37, 448–459.
[DOI=10.1002/jcc.24254](doi.org/10.1002/jcc.24254)
8. Chevalier, C.; Pellegrini, F. 2008. PT-Scotch: A tool for efficient parallel graph ordering. Parallel Comput. 34, 318.[DOI=10.1016/j.parco.2007.12.001](doi.org/10.1016/j.parco.2007.12.001)
9. Keçeli M.; Corsetti F.; Campos C.; Román, J. E.; Vázquez-Mayagoitia
Á;  Zhang, H.; Zapol, P.; & Wagner A, F.
SIESTA-SIPs: Massively parallel spectrum-slicing eigensolver for an ab
initio molecular dynamics package. (Accepted to Journal of
Computational Chemistry, 2018)
