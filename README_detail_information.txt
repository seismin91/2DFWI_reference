[Verification of Full waveform inversion program]
- To check applicability of your full waveform inversion code, you may run your FWI code with parameters mentioned below.
- Before implementing your FWI code test, verification of your linearized wave equation solver may be helpful for developing reliable inversion code.
 - Warning : Index in Python start from 0, but that in MATLAB may start from 1.

1. Modeling parameters
- nx		: 401
- nz		: 176
- nt		: 2001
- dx		: 20 m
- dz		: 20 m
- dt		: 0.002 (2 ms)
- Maximum frequency : 18 Hz
- Wavelet	: Ricker

- Num. of sources	: 101
- Source positions on x-grid  : 0 + 4*ishot (ishot = 1, nshot. ex, 0, 4, 8, 12, ..., 400) 
- Source depths on z-grid	: 2 (all sources were deployed at same depth)
   
- Num. of receivers : 401
- Receiver positions on x-grid : 0 + 1*ircv (ircv = 1, nrcv. ex, 0,1,2,...,400)
- Receiver depths on z-grid	: 2 (all receivers were deployed at same depth)

- Free surface : OFF (Top, bottom, left and right sections of model has absorbing boundary conditions)
- Data type : float64 (in MATLAB, it may double...?)

2. Full waveform inversion parameters
- Objective function	: L2-norm (J = 0.5 * ||u-d||^2)
- Optimization scheme	: Preconditioned steepest descent method
- Step length : 20 m/s
- Minimal and maximal velocity constraints	: 1,500 m/s and 4,800 m/s 
- Number of iterations : 50
- Gradient and Pseudo Hessian should be tapered by water masker in attachment
- After applying the water masker to pseudo hessian, its maximum value scaled by 1e-2 should be added to avoid the division by zero
- Updating direction is computed by diving gradient by pseudo hessian. After that, Updating direction should be normalized by its maximal absolute value. 







