# Executables

UM executables can be built from the rose/cylc suite, or users can use a pre-compiled SPACK (https://spack.io).

The SPACK executable has an advantage in terms of provenance and reproducability.  There are however slight differences
between the current SPACK-built and rose/cylc built UM version 13.5 executable, as seen in minor differences in the model output.
This is because the UM executable is sensitive to the order in which modules are loaded into the environment and there are subtle differences 
module load ordering.  This will be investigated further in the long term (it is a non-trivial issue).

For consistency we recommend that users either:

1) use the SPACK executable only, or

2) use rose/cylc built executables only.

i.e. If you are modifying the code and building your own executables we recommend that you build your own non-modified executable for use in comparisons.


