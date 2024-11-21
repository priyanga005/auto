import numpy as np

def auto_correlation(x):
    """
    Compute the auto-correlation of a signal.
    
    Parameters:
    x : list or array
        Input signal.
    
    Returns:
    r : array
        Auto-correlation of the signal.
    """
    n = len(x)
    # Zero-pad the signal for proper correlation computation
    padded_x = np.pad(x, (0, n-1), mode='constant')
    r = np.correlate(padded_x, x, mode='full')
    return r[len(x)-1:]  # Return only the non-negative lags

# Example usage
x = [1, 2, 3, 4]  # Input signal
result = auto_correlation(x)

print("Input Signal (x):", x)
print("Auto-correlation Result:", result)
