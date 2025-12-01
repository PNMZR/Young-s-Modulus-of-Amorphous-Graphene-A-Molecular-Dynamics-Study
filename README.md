# Instructions for Readers
>
> Created by Rong Zhao
>
> Email: zhaorong1016.sripe@sinopec.com
>
> July 2024

The following instructions explain the source code accompanying the paper titled "Young’s Modulus of Amorphous Graphene: A
Molecular Dynamics Study" by Rong Zhao. Both the source codes are included in the download. Alternatively, it can be obtained by emailing the authors: zhaorong1016.sripe@sinopec.com.

## Source files

The source files `generate_initial_a_G.py` and `x_uniaxial_tension_2d.lammps` are found in the `src/initial_a_G` and `src/input_file` subdirectories, respectively.

- `generate_initial_a_G.py`: Python source code for generating 10 initial amorphous graphene (a-G) samples with a particular vacancy concentration. This code needs a file named `graphene_24x24.data`, which is in the `initial_a_G/pristine_graphene`  subdirectory.
- `x_uniaxial_tension_2d.lammps`: LAMMPS input file for uniaxial tensile loading of 10 a-G samples along x direction.

## Other subdirectories

- `final_a_G`: XYZ-coordinate files of final a-G samples (LAMMPS data format) are saved in this subdirectory.

- `lammpstrj`: particle trajectory data during uniaxial tension tests are saved in this subdirectory.

- `log_file`:  log files are saved in this subdirectory.

- `potential`: Environment-Dependent Interatomic Potential (EDIP) file (C.edip).

- `stress_strain`: stress-strain data are saved in this subdirectory.

## Useage

1. Change the current folder to the `src/initial_a_G` subdirectory, then run the Python file named `generate_initial_a_G.py`.
   - The prerequisites for this code are [NumPy](https://numpy.org/) and [ovito](https://docs.ovito.org/python/index.html) Python modules. Before execution of this code, you should set the values of variables `count` (line 24) and `vacancy_percent` (line 25). For example:
    ```python
   count = 10*10  # 6*6, 8*8, 10*10, 12*12, 14*14, 16*16 ...
   vacancy_percent = 0.10  # 0.00, 0.02, 0.06, 0.10, 0.14, 0.18, 0.22, 0.26 ...
      ```
2. Change the current folder to the `src/input_file` subdirectory, then run the input script named `x_uniaxial_tension_2d.lammps`.

    - To execute, use the syntax `mpiexec -np 4 lmp -in x_uniaxial_tension_2d.lammps` from the command prompt in Windows or `mpirun -np 4 lmp -in x_uniaxial_tension_2d.lammps` from the command prompt in Linux.
