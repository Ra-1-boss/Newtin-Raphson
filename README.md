# Newtin-Raphson
import math

TOL = 0.000001  # setting the tolerance
N = 50  # setting the maximum number of iterations

x0 = float(input("Enter the initial approximation: "))
print("iter.\txk\t\t\tf(xk)\t\t\tError")

xk = x0
fxk = 4*xk + math.sin(xk) - math.exp(xk)
for k in range(1, N+1):
    xp = xk
    fxp = fxk
    dfxp = 4 + math.cos(xp) - math.exp(xp)
    xk = xp - (fxp/dfxp)
    
    fxk = 4*xk + math.sin(xk) - math.exp(xk)
    
    err = abs(xk - xp)/abs(xk)
    
    print(f"{k}\t{xk:.16f}\t{fxk:.16f}\t{err:.12f}")
    if err < TOL:
        break

if err < TOL:
    print("Required accuracy achieved; Solution is convergent.")
else:
    print("The Number of iterations exceeded the maximum limit.")
