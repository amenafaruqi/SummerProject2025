## Some brief notes to help understand these files

- All data is 2D, the grid is cylindrical (r, phi)
- "x" and "y" refers to the azimuthal and radial components, respectively
- The number suffixes for the dust files indicate the dust species. There are 42 total, logarithmically spaced from 10^-5 to 10^2 cm so use these to know what dust size you are looking at. 200 is just the timestep number.  
- `variables.par` contains the simulation parameters - check these for things like grid resolution, cell spacing, etc. 
- The `domain_*.dat` files list the spatial coordinates at the cell edges e.g. the radial extent of the disc is from 5 to 150 AU so all values in `domain_y.dat` should fall somewhere between 5 and 150. For `domain_y.dat` ignore the first 3 and last 3 values in any calculations - these are "ghost values" and lie outside the grid.
- The `*dens*.dat` files contain density values in units of Msol/AU^2. The data is in an array with dimensions of (number of radial cells) x (number of azimuthal cells).
- The `*vx*.dat` and `*vy*.dat` files contain velocity data. The data is in AU/yr. The vx data (azimuthal) will need the following reference frame transformation applied to it:
  ```
  v_phi = v_phi (from file + (omegaframe*R)
  ```
  where `R` is the radial location and `omegaframe` is specified in the `variables.par` file.

  
