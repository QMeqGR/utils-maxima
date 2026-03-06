# utils-maxima

This repo contains minor utilities that I find useful.

integration:

byparts(expr,x,a,db) -- integration by parts for an expression. User
inputs a, db parts of the expression.

matrix:

delrow(A,n) -- delete row n from matrix A

rowsum(A,n) -- compute sum of row n elements

rref(A) -- compute reduced row echelon form and drop zero rows

shanks:

psum(A,n) -- nth partial sum of a summed expression

shanks1(A,n) -- perform a single shanks transformation (nth partial sum)

shanks(A,n,m) -- perform a shanks transformation of order m

utils:

random_matrix(n,r) -- create n x n floating point matrix with elements
between -r and r.

diagonalize(M) -- diagonalize matrix M and return both eigenvalues and
eigenvectors. For 2x2 matrices this returns answers were the built-in
eigenvectors() call fails. For n >= 3 this function just calls the built-in
eigenvectors(). If you provide an additional argument 1, the eigenvectors
will be normalized.

LAPACK:

lapack_eigs(M) -- calls dgeev on matrix M. load(lapack) is required.

sort_evecs(eval,evec) -- Sort the eigenvalues and then the columns of
the eigenvectors. This function should be used only with the dgeev()
lapack function, not the eigenvectors() function.
