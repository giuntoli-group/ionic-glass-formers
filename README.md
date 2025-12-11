# Ionic glass formers show an inverted relation between fragility and non-exponential alpha-relaxation

This repository contains the LAMMPS scripts and the data files used in the paper *Ionic glass formers show an inverted relation between fragility and non-exponential alpha-relaxation*

This repository contains the data files and input scripts used to run a complete LAMMPS workflow, starting from initial system configurations and ending with production simulations. The process is carried out in three stages: a soft-potential equilibration, a temperature-dependent relaxation, and a final production run.

The initial configuration for the four system types (`start_COM.data`, `start_PIL.data`, `start_IL.data` and `start_NEU.data`) is first supplied to `equilibration.in`, which performs an uncharged equilibration using a soft potential. This step produces relaxed structures named `relaxed_T.data`, where `T` corresponds to the target temperature for each of the types.

These relaxed files then serve as input for the relaxation stage. Depending on whether the system contains charges, either `relax_charged.in` or `relax_neutral.in` is used. Each relaxation script includes a temperature variable `T` (defaulted to 0.8). The relaxation procedure is repeated for every system type and every temperature of interest.

After relaxation, the resulting structures are passed to the appropriate production script, again selected based on whether the system is charged (`production_charged.in`) or neutral (`production_neutral.in`). These production scripts carry out the final simulations from the fully prepared configurations.

The scripts can be executed using the LAMMPS command:
```
lmp -in <script_name>
```

