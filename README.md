The files in this repository were used to generate animations from some classic paintings, according to some rules. The code is written as Mathematica notebooks and the final animation was produced with image magick.

The Mathematica notebooks have several sections with different numerical methods for differential equations (HeatAnimation.nb), cellular automata (AutomatonOverPainting.nb) and another for the convection-diffusion equation (TransportAnimation.nb)

# How To

To begin with, choose some image, save it to this folder, and update the folder paths on the notebooks, as appropriate. Also, create a subfolder where the frames will be saved.

Run the notebook, then run the following terminal commands, to generate the animations.

I always replicate the first image, so it stays longer on screen. Run this command
```
cd figs/; for i in {1..9}; cp scream_rule30_001.png scream_rule30_001_$i.png; done
```
To generate a gif from the figures, convert from image magick is used:
```
convert figs/scream_adim_* scream.gif
```
Then you can remove the original figures
```
rm figs/scream_adim_*
```

# Notes

Some comments on basic methods for differential equations:

1. The Euler method is straightforward, but it requires very small time steps, or the algorithm will diverge fast, I have found useful the rule of thumb dt < dx^2/4
2. The Alternating Direction Implicit method is stable for much larger values of dt. It has to solve dN (d=2, the dimensionality, N=size of matrices) systems of equations with tridiagonal matrices, which have a linear complexity. But it is only valid for linear equations (such as the heat equation).
3. The Adams-Bashforth method is an explicit method more suitable for nonlinear systems, but it shows some of the instabilities of the Euler method.
4. In linear systems, the implicit step can be performed by solving a linear system of equations. In nonlinear systems, one has to use iterative methods, such as Newton's method, or others, increasing the complexity of the algorithm.

