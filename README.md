SIPs is a parallel sparse eigensolver for real and symmetric generalized eigenvalue problems. 
Motivated by quantum chemistry and material science applications, where a large portion of eigensolutions are required, SIPs was initially developed in 2007.<sup>1</sup> 
Built on top of [PETSc](https://www.mcs.anl.gov/petsc/) and [SLEPc](http://slepc.upv.es/) libraries, SIPs solves the eigenvalue problem with distributed spectrum slicing method. 
Thanks to improvements in the robustness and efficiency of the underlying mathematical libraries,<sup>2</sup> a later implementation of SIPs demonstrated scalability of the eigensolver beyond 200,000 cores for matrices with more than 500,000 rows.<sup>3</sup> 
A more recent implementation of SIPs is now available in [SLEPc](http://slepc.upv.es/) package and it is integrated into a branch of [SIESTA](https://departments.icmab.es/leem/siesta/), an initio molecular dynamics package. [ELSI](https://wordpress.elsi-interchange.org/) developers also provide an interface to SIPs eigensolver and other solvers for quantum chemistry applications.<sup>5</sup> 

## References
1. Zhang, H.; Smith, B.; Sternberg, M.; Zapol, P.  
SIPs: Shift-and-Invert Parallel Spectral Transformations.  
[ACM Trans. Math. Softw. 2007, 33, 9–es. DOI=10.1145/1236463.1236464](https://dl.acm.org/citation.cfm?doid=1236463.1236464)
2. Campos, C.; Román, J. E.  
Strategies for Spectrum Slicing Based on Restarted Lanczos Methods.  
[Numer. Algorithms 2012, 60, 279–295. DOI=10.1007/s11075-012-9564-z](https://link.springer.com/article/10.1007%2Fs11075-012-9564-z)
3. Keçeli, M.; Zhang, H.; Zapol, P.; Dixon, D. A.; Wagner, A. F.    
Shift-and-Invert Parallel Spectral Transformation Eigensolver: Massively Parallel Performance for Density-Functional Based Tight-Binding.  
[J. Comput. Chem. 2016, 37, 448–459. DOI=10.1002/jcc.24254](https://onlinelibrary.wiley.com/doi/abs/10.1002/jcc.24254)
4. Keçeli M.; Corsetti F.; Campos C.; Román, J. E.; Vázquez-Mayagoitia Á;  Zhang, H.; Zapol, P.; & Wagner A, F.  
SIESTA-SIPs: Massively parallel spectrum-slicing eigensolver for an ab initio molecular dynamics package. (under review, 2018)

5. Yu, V. W.; Corsetti, F.; García, A.; Huhn, W. P.; Jacquelin, M.; Jia, W.; Lange, B.; Lin, L.; Lu, J.; Mi, W.; Seifitokaldani, A.; Vázquez-Mayagoitia, Á.; Yang, C.; Yang, H.; Blum, V.  
ELSI: A Unified Software Interface for Kohn-Sham Electronic Structure Solvers. http://arxiv.org/abs/1705.11191 2017, 1–55.
