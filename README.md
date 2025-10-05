# TRISO-fueled HPMR

The TRISO-fueled Heat Pipe Microreactor (HPMR) was developed based on the generic monolithic
HPMR design developed by Idaho National Laboratory The fundamental dimensions
and core configuration of the original design were retained, but several modifications were implemented to
align the design with the specific objectives of this study.

The developed model has the following key design parameters:

* Fuel: TRISO-fuel
* 235U-enrichment: 19.75 wt%
* Monolith material: graphite
* Reflector material: BeO
* Operating time: 3 years
* Operating power: 7.5 MWth

The major reference used to develop the provided models is the following:

* J. Ortensi, M. K. Jaradat, J. E. Hansel, and S. Terlizzi (2024). The Monolithic Heat Pipe Microreactor
Reference Plant Model. Technical report [INL/RPT-24-77914](https://doi.org/10.2172/2356755), Idaho National
Laboratory, Idaho Falls, ID.

Results obtained with the developed MSR model are summarized in the following publication:

* D. Hartanto, G. Radulescu, F. Bostelmann, W. A. Wieselquist (2025), SCALE Analyses of Scenarios in the TRISO-Based Heat Pipe Microreactor Fuel Cycle, [ORNL/TM-2025/3914](https://www.nrc.gov/docs/ML2517/ML25178C892.pdf), Oak Ridge National Laboratory, Oak Ridge, TN.

:warning: The models provided here might differ from the models used for the
studies summarized in the report since models are updated based upon feedback. :warning:

## Content

### Models

SCALE input and output files for the following models are provided:

* TRITON-Shift depletion models:
  * Full core with control drums facing outwards
  * Full core with control drums rotated based on critical search
* CSAS-Shift neutron transport models:
  * Full core with BOL fuel
  * Full core with EOL fuel

### File overview

```
.
├── full_core
│   ├── hpmr.ce_v7.1.csas6-shift.boc.fission_density.3dmap
│   ├── hpmr.ce_v7.1.csas6-shift.boc.fission_source.3dmap
│   ├── hpmr.ce_v7.1.csas6-shift.boc.flux.3dmap
│   ├── hpmr.ce_v7.1.csas6-shift.boc.inp
│   ├── hpmr.ce_v7.1.csas6-shift.boc.out
│   ├── hpmr.ce_v7.1.csas6-shift.eoc.fission_density.3dmap
│   ├── hpmr.ce_v7.1.csas6-shift.eoc.fission_source.3dmap
│   ├── hpmr.ce_v7.1.csas6-shift.eoc.flux.3dmap
│   ├── hpmr.ce_v7.1.csas6-shift.eoc.inp
│   ├── hpmr.ce_v7.1.csas6-shift.eoc.out
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search_step_0.f71
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search_step_0.inp
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search_step_0.out
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search_step_39.f71
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search_step_39.inp
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search_step_39.out
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search.eoc_core_decay.f71
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_crit_search.eoc_core_decay.ii.json
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay_1mtihm.f71
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay_1mtihm.ii.json
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay.f71
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay.ii.json
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.f71
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.inp
│   ├── hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.out
│   ├── origen_eoc_core_decay.inp
│   └── origen_eoc_core_decay.out
└── README.md
```

* inp: text input file
* out: text output file
* ii.json: inventory interface JSON file
* f33: ORIGEN binary library file
* f71: ORIGEN binary concentration file
* 3dmap: binary mesh tally file

### Inventory for accident progression

The inventory used for accident progression analyses is the core-average end of life (EOL) inventory that was calculated using a TRITON full core depletion calculation from beginning of life (BOL) to EOL. TRITON provides inventory for each of the depleted fuel mixture as well as for the weighted sum of these fuel mixtures (i.e., a core-average of all fuel mixtures). This core-average inventory at EOL was decayed with ORIGEN for 10 days. The inventory files of interest are the following:

* Core-average inventory normalized to 1 MTIHM
  * [II.JSON file](full_core/hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay_1mtihm.ii.json)
  * [F71 file](full_core/hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay_1mtihm.f71)
* Core-average inventory scaled to the actual core mass of 0.517594 MTIHM
  * Obtained from depletion with control drums facing outward
    * [II.JSON file](full_core/hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay.ii.json)
    * [F71 file](full_core/hpmr.mg_v7.1.t6-depl.control_drums_facing_outward.eoc_core_decay.f71)
  * Obtained from depletion with control drums critical search
    * [II.JSON file](full_core/hpmr.mg_v7.1.t6-depl.control_drums_crit_search.eoc_core_decay.ii.json)
    * [F71 file](full_core/hpmr.mg_v7.1.t6-depl.control_drums_crit_search.eoc_core_decay.f71)

## Related presentations

Analyses related to the this model were presented at a public workshop organized by the NRC.
Information about this meeting can be found [here](https://www.nrc.gov/pmns/mtg?do=details&Code=20250196)
and the meeting slides can be accessed [here](https://www.nrc.gov/docs/ML2508/ML25084A173.pdf).

------

# README.md from ROOT dir in repo - Public SCALE non-LWR Models for Volume 3

This repository contains SCALE models developed by ORNL for the US Nuclear Regulatory
Commission (NRC) project [Volume 3: SCALE Non-LWR Reactor Core Model Development & Assessment for Severe Accident Progression, Source Term, and Consequence Analysis](https://www.nrc.gov/docs/ML2003/ML20030A178.pdf).

Visit NRC's website describing this project and related projects:

* <https://www.nrc.gov/reactors/new-reactors/advanced/details.html#non-lwr-ana-code-dev>
* <https://www.nrc.gov/reactors/new-reactors/advanced/references/nuclear-power-reactor-source-term.html>

All models were developed based on publicly available information.
No proprietary information was used.

The input files and relevant output files of each reactor concept
are provided in separate subfolders. The basic models are provided
which can be used to reproduce results described in the corresponding
publications.

The general citation for this repository is the following:

* F. Bostelmann, D. Hartanto, A. Shaw, S. Skutnik, G. Radulescu, C. Celik, W. Wieselquist (2025), SCALE Non-LWR Models for NRC Volume 3, Public Repository, Oak Ridge National Laboratory. DOI: 10.13139/ORNLNCCS/2572299

:bangbang: **When using a model from this repository, cite the corresponding provided ORNL references.** :bangbang:

## Content

### Non-LWR models

SCALE models including input and output files for the following list of non-LWR models are contained in this repository. Analyses based on the developed SCALE models were presented in public workshops organized by the NRC.
Information on these workshops, the presentations, and the final reports can be found under the provided links.

##### Pebble-bed High Temperature Gas-cooled Reactor (HTGR)

* Model: PBMR-400
* Reference report: _S. E. Skutnik and W. A. Wieselquist (2021), Assessment of ORIGEN Reactor Library Development for Pebble-Bed Reactors Based on the PBMR-400 Benchmark, [ORNL/TM-2020/1886](https://info.ornl.gov/sites/publications/Files/Pub150728.pdf), Oak Ridge National Laboratory, Oak Ridge, TN._
* [workshop](https://www.nrc.gov/pmns/mtg?do=details&Code=20210770), [slides](https://adamswebsearch2.nrc.gov/webSearch2/main.jsp?AccessionNumber=ML21200A179), [video](https://youtu.be/I_7GIOeXVtw)

##### Heat Pipe Reactor (HPR)

* Model: INL Design A
* Reference report: _E. Walker, S. E. Skutnik, W. A. Wieselquist, A. Shaw, and F. Bostelmann (2021), SCALE Modeling of the Fast-Spectrum Heat Pipe Reactor, [ORNL/TM-2021/2021](https://www.osti.gov/biblio/1871124-scale-modeling-fast-spectrum-heat-pipe-reactor), Oak Ridge National Laboratory, Oak Ridge, TN._
* [workshop](https://www.nrc.gov/pmns/mtg?do=details&Code=20210696), [slides](https://adamswebsearch2.nrc.gov/webSearch2/main.jsp?AccessionNumber=ML21179C060), [video](https://youtu.be/8pRplj75NMw)

##### Fluoride salt-cooled High temperature reactor (FHR)

* Model: UC Berkeley pebble-bed FHR Mark 1 (PB-FHR-Mk1)
* Reference report: _F. Bostelmann, C. Celik, R. F. Kile, W. Wieselquist (2022), SCALE Analysis of a Fluoride Salt Cooled High Temperature Reactor in Support of Severe Accident Analysis, [ORNL/TM-2021/2273](https://info.ornl.gov/sites/publications/Files/Pub168374.pdf), Oak Ridge National Laboratory, Oak Ridge, TN._
* [workshop](https://www.nrc.gov/pmns/mtg?do=details&Code=20210774), [slides](https://adamswebsearch2.nrc.gov/webSearch2/main.jsp?AccessionNumber=ML21256A231), [video](https://youtu.be/YZDqCka_gm4)

##### Small Molten Salt-fueled Reactor (MSR)

* Model: Molten Salt Reactor Experient (MSRE)
* Reference report: _A. Lo, F. Bostelmann, D. Hartanto, B. Betzler, W. A. Wieselquist (2022), Application of SCALE to Molten Salt Fueled Reactor Physics in Support of Severe Accident Analyses, [ORNL/TM-2022/1844](https://info.ornl.gov/sites/publications/Files/Pub173113.pdf), Oak Ridge National Laboratory, Oak Ridge, TN._
* [workshop](https://www.nrc.gov/pmns/mtg?do=details&Code=20220713), [slides](https://adamswebsearch2.nrc.gov/webSearch2/main.jsp?AccessionNumber=ML22255A214), [video](https://www.youtube.com/watch?v=nHHV528O0p0)

##### Full-scale Molten Salt-fueled Reactor (MSR)

* Model: Molten Salt Breeder Reactor (MSBR)
* Reference report: _D. Hartanto, G. Radulescu, F. Bostelmann, W. A. Wieselquist (2025), SCALE Analyses of Scenarios in the Molten Salt Reactor Fuel Cycle, [ORNL/TM-2024/3659](https://www.nrc.gov/docs/ML2512/ML25128A289.pdf), Oak Ridge National Laboratory, Oak Ridge, TN._
* [workshop](https://www.nrc.gov/pmns/mtg?do=details&Code=20240552), [slides](https://adamswebsearch2.nrc.gov/webSearch2/main.jsp?AccessionNumber=ML24192A127), [video](https://www.youtube.com/watch?v=GJdNkSL2fxE)

##### Sodium-cooled Fast Reactor (SFR)

* Model: Advanced Burner Test Reactor (ABTR)
* Reference report: _A. Shaw, F. Bostelmann, D. Hartanto, E. Walker, W. Wieselquist (2023), SCALE Modeling of the Sodium-Cooled Fast-Spectrum Advanced Burner Test Reactor, [ORNL/TM-2022/2758](https://www.osti.gov/biblio/1991734), Oak Ridge National Laboratory, Oak Ridge, TN._
* [workshop](https://www.nrc.gov/pmns/mtg?do=details&Code=20220714), [slides](https://adamswebsearch2.nrc.gov/webSearch2/main.jsp?AccessionNumber=ML22262A252), [video](https://youtu.be/pinsryEwqC4)

##### TRISO-fueled Heat Pipe Microreactor (HPMR)

* Model: generic TRISO-fueled Heat Pipe Microreactor
* Reference report: _D. Hartanto, G. Radulescu, F. Bostelmann, W. Wieselquist (2025), SCALE Analyses of Scenarios in the TRISO-based Heat Pipe Microreactor Fuel Cycle, ORNL/TM-2025/3914, Oak Ridge National Laboratory, Oak Ridge, TN._
* [workshop](https://www.nrc.gov/pmns/mtg?do=details&Code=20250196), [slides](https://www.nrc.gov/docs/ML2508/ML25084A173.pdf), [video](https://youtu.be/i6yIupf9rB8)

### Inventory for consequence analysis

For each of the reactors, inventory for accident progression calculations with MELCOR was generated that is provided in this repository. To consider the most conservative conditions of the individual cores, core-average or system-average inventory files were generated as follows:

* HTGR and FHR: core-average inventory at the state of equilibrium operation
* HPR: core-average inventory at end-of-life
* SFR: core-average inventory at the end of an equilibrium cycle
* MSR: system-average inventory (considering the fuel salt inside the core and the loop) at end-of-life
* HPMR: core-average inventory at end-of-life

For use in MELCOR, the core-average or system-average inventory was decayed with ORIGEN for 10 days in order to allow consideration of accurate inventory as a function of time during accident progression. 10 days was deemed sufficient for this purpose.

The core-average or system-average inventory as a function of 10 days of decay is provided in the form of an ORIGEN concentration file (F71 file) and as JSON-formatted inventory interface (II.JSON). The README files in the individual sections provide links to the specific files.

It is noted that many of the inventory result files were generated with the TRITON reactor physics and depletion sequence. By default, this sequence normalizes the inventory to match 1 metric ton initial heavy metal (MTIHM). For easier use of the inventory files, the normalized inventory as well as the inventory scaled to the actual core mass is provided for most of the reactors in this repository.

## Acknowledgements

Support for this work was provided by the US Nuclear Regulatory Commission
Offices of Nuclear Regulatory Research and Nuclear Reactor Regulation.
Many ORNL staff members have contributed to the development of the
models provided in this repository through discussions about
presented results and support with modeling challenges.

## Inventory Interface File

This work has developed a new inventory interface (`ii`) file format for exchanging nuclide inventory data with the MELCOR team. It is a heirarchical description of the inventory in one or more zones, at one or more time points. Currently the `ii` (pronounced aye-aye) data is emitted in standard [JSON](https://www.json.org/json-en.html) format so that one can read the files outside of SCALE. We currently use `ii.json` as the extension for these files. In the future we may provide an [HDF5](https://www.hdfgroup.org/solutions/hdf5/) version as well to save disk space--these would have the extension `.ii.h5`. We made the decision to package relevant nuclear data with the inventory in the `ii` format because typically downstream operations would like to calculate decay heat, mass, activity, and other derived quantities from the number of atoms/moles of each nuclide. Instead of providing number of moles, grams, and activity for each nuclide, we provide the molar mass (grams/mol) and decay constant (1/s) for each nuclide. Including nuclear data also aids us in nuclear data uncertainty studies where we would generate hundreds of `ii.json` files for each realization of the nuclear data. Each one of these realizations is the initial condition for a MELCOR severe accident analysis realization. Although the variation of the inventory in moles has the implicit effect of variations in nuclear data, the direct effect on decay heat and activity requires the perturbed recoverable energy from decay values and the decay constants. Additional details on the format are provided in this copy of the SCALE Quality Assurance (QA) case for this feature: [SCL-2020-003](supplemental/scl-2020-003_inventory-interface.md).

## Scripts to Process the Inventory Interface File

A number of scripts are provided in the `supplemental` directory to process
the `ii.json` data file. Each data file is able to hold multiple "responses".
The simple `print_responses.py` lets you know which responses are available.

```
python3 supplemental/print_responses.py INL-A/full_core/depletion/INL-A_core_t6-depl_ce_v7.1.ii.json
```

The screen output should be:

```
available responses for file INL-A/full_core/depletion/INL-A_core_t6-depl_ce_v7.1.ii.json : AT_POWER
```

Many scripts take a file name and a response in order to produce output.

1. `example_out.py <file> <response>` - an example emitting all time-dependent nuclide data in a particular file for a particular response
2. `json2maccs.py <file> <response> <time_index>` - an example emitting the MACCS inventory data at a single time index
3. `json2melcor.py <file> --id <response>` - an example emitting the MELCOR decay heat data for all times
4. `json2melcor_msr.py <file> --id <response>` - an example emitting the MELCOR decay heat data for all times with MELCOR element classes modified for MSRs
5. `multiply_response.py <file> <response> <multiplier>` - multiply the response amount by the multiplier (useful because SCALE normalizes most of its data to 1 MTIHM)
6. `print_mass.py <file> <response>` - print total mass as a function of time (useful for checking total is expected, e.g. full core or single assembly)
7. `print_responses.py <file>` - print the available responses in the file
