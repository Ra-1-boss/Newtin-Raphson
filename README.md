# Newtin-Raphson
import math

# Define constants
TOLERANCE = 1e-5       # Accuracy within 10^-5
MAX_ITERATIONS = 100    # Maximum number of iterations

# Define the function and its derivative
def f(x):
    return 4*x + math.sin(x) - math.exp(x)

def df(x):
    return 4 + math.cos(x) - math.exp(x)

# Newton-Raphson method
def newton_raphson(x0):
    print("Iteration\tx\t\t\tf(x)\t\t\tError")
    
    xk = x0
    for k in range(1, MAX_ITERATIONS + 1):
        fxk = f(xk)
        dfxk = df(xk)
        
        if dfxk == 0:
            print("Zero derivative. No solution found.")
            return None
        
        xk_new = xk - fxk / dfxk
        err = abs(xk_new - xk) / abs(xk_new) if xk_new != 0 else abs(xk_new - xk)
        
        print(f"{k}\t\t{xk_new:.10f}\t{fxk:.10f}\t{err:.10f}")
        
        if err < TOLERANCE:
            print(f"\nRequired accuracy achieved in {k} iterations.")
            print(f"The root is approximately: {xk_new:.10f}")
            return xk_new
        
        xk = xk_new
    
    print("\nMaximum iterations reached without achieving desired accuracy.")
    return xk

# Main program
if __name__ == "__main__":
    x0 = 0.0  # Initial approximation
    print(f"Finding root of f(x) = 4x + sin(x) - e^x with initial guess x0 = {x0}")
    root = newton_raphson(x0)
