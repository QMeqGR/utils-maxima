# utils-maxima

This repo contains minor utilities that I find useful.

**integration:**

The elementary integration by parts formula is

```math
\int a\, db = a b\, - \int b\, da
```

The following functions perform integration by parts:

byparts(a,db,x) -- integration by parts for an expression. User
inputs a, db parts of the expression. Does not evaluate the
integrate(b*diff(a,x),x) integral.

byparts2(a,db,x) -- integration by parts for an expression. User
inputs a, db parts of the expression. Evaluates the
integrate(b*diff(a,x),x) integral.

byparts3(a,db,x,l,u) -- integration by parts for an expression
with limits. User inputs a, db parts of the expression and upper and
lower limits. Does not evaluate the integrate(b*diff(a,x),x) integral.

byparts4(a,db,x,l,u) -- integration by parts for an expression
with limits. User inputs a, db parts of the expression and upper and
lower limits. Evaluates the integrate(b*diff(a,x),x) integral.

int_bp(expr,x) -- more sophisticated integration by parts that tries
every single multiplicative factor as db and the rest as a, and then
return a list with output of each db tried (only unique entries are
shown). Optional limit arguments can be added: int_bp(expr,x,xlo,xhi).


example:
```
(%i4) k: x^2*exp(3*x);
                                     3 x  2
(%o4)                              %e    x
(%i5) int_bp(k,x);
                  3 x     2 
                %e    (9 x  - 6 x + 2)
(%o5)          [----------------------]
                          27 
```

**matrix:**

delrow(A,n) -- delete row n from matrix A

rowsum(A,n) -- compute sum of row n elements

rref(A) -- compute reduced row echelon form and drop zero rows

**shanks:**

psum(A,n) -- nth partial sum of a summed expression

shanks1(A,n) -- perform a single shanks transformation (nth partial sum)

shanks(A,n,m) -- perform a shanks transformation of order m

**utils:**

random_matrix(n,r) -- create n x n floating point matrix with elements
between -r and r.

diagonalize(M) -- diagonalize matrix M and return both eigenvalues and
eigenvectors. For dimension $n=2$ this code uses the simple, fast
method that one would use by hand. For $n>=3$ this code uses a
modified version of the built-in eigenvectors(), called
eigenvectors_fix(). This is essentially the eigenvectors() function in
share/matrix/eigen.mac but with algsys replaced with linsolve.
The output in any case represents the eigenvectors as column vectors
rather than row vectors. If you provide an additional argument
1, the eigenvectors will be normalized.

**LAPACK:**

lapack_eigs(M) -- calls dgeev on matrix M. load(lapack) is required.

sort_evecs(eval,evec) -- Sort the eigenvalues and then the columns of
the eigenvectors. This function should be used only with the dgeev()
lapack function, not the eigenvectors() function.
