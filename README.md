# Integration of RISC-V Page Table Walk in gem5 SE Mode
This branch enables the use of page table walk in SE mode (RISC-V ISA).
The paper titled “Integration of RISC-V Page Table Walk in gem5 SE Mode” has been accepted in the proceedings of the Rapido’24 Workshop on Rapid Simulation and Performance Evaluation: Methods and Tools (HiPEAC 2024)[Paper](./Integration_of_RISC_V_Page_Table_Walk_in_gem5_SE_Mode.pdf)

## Differences
All the differences, compared to gem5 v23.0.1.0, are shown in ```gem5.diff``` file.

## Usage
The configuration file includes additional options:
```bash
  --workload WORKLOAD  Path of the binary to run
  --options OPTIONS    Options of the binary
  --use-arch-pt        Enable the use of page table in SE mode Default: False
  --dtb-size DTB_SIZE  Number of data TLB entries. Default: 64
  --itb-size ITB_SIZE  Number of instruction TLB entries. Default: 64
```
The most important option is ```--use-arch-pt``` that enables the use of the page table walk in gem5 SE.

An example of configuration script can be found in ```configs/example_RAPIDO24/riscv_demo_board.py```

## Example
The following command can be used to run a simulation with the demo board:
```
build/RISCV/gem5.opt \
    configs/example_RAPIDO24/riscv_demo_board_se.py \
    --workload <path/to/your/binary> \
    --options <options of your binary> \
    --use-arch-pt \
    --dtlb-size 1024 \
    --itlb-size 1024
```

## Citation

If you use this repository in your work, please cite:
```BibTeX
@inproceedings{mannino2024integration,
  title={{Integration of RISC-V Page Table Walk in gem5 SE Mode}},
  author={Mannino, Mirco and Huang, Yinting and Peccerillo, Biagio and Medaglini, Alessio and Bartolini, Sandro},
  booktitle={Proceedings of the Rapido'24 Workshop on Rapid Simulation and Performance Evaluation: Methods and Tools},
  pages={1--7},
  year={2024},
  doi={10.1145/3642921.3642926},
}
```

---

# The gem5 Simulator

This is the repository for the gem5 simulator. It contains the full source code
for the simulator and all tests and regressions.

The gem5 simulator is a modular platform for computer-system architecture
research, encompassing system-level architecture as well as processor
microarchitecture. It is primarily used to evaluate new hardware designs,
system software changes, and compile-time and run-time system optimizations.

The main website can be found at <http://www.gem5.org>.

## Getting started

A good starting point is <http://www.gem5.org/about>, and for
more information about building the simulator and getting started
please see <http://www.gem5.org/documentation> and
<http://www.gem5.org/documentation/learning_gem5/introduction>.

## Building gem5

To build gem5, you will need the following software: g++ or clang,
Python (gem5 links in the Python interpreter), SCons, zlib, m4, and lastly
protobuf if you want trace capture and playback support. Please see
<http://www.gem5.org/documentation/general_docs/building> for more details
concerning the minimum versions of these tools.

Once you have all dependencies resolved, execute
`scons build/ALL/gem5.opt` to build an optimized version of the gem5 binary
(`gem5.opt`) containing all gem5 ISAs. If you only wish to compile gem5 to
include a single ISA, you can replace `ALL` with the name of the ISA. Valid
options include `ARM`, `NULL`, `MIPS`, `POWER`, `SPARC`, and `X86` The complete
list of options can be found in the build_opts directory.

See https://www.gem5.org/documentation/general_docs/building for more
information on building gem5.

## The Source Tree

The main source tree includes these subdirectories:

* build_opts: pre-made default configurations for gem5
* build_tools: tools used internally by gem5's build process.
* configs: example simulation configuration scripts
* ext: less-common external packages needed to build gem5
* include: include files for use in other programs
* site_scons: modular components of the build system
* src: source code of the gem5 simulator. The C++ source, Python wrappers, and Python standard library are found in this directory.
* system: source for some optional system software for simulated systems
* tests: regression tests
* util: useful utility programs and files

## gem5 Resources

To run full-system simulations, you may need compiled system firmware, kernel
binaries and one or more disk images, depending on gem5's configuration and
what type of workload you're trying to run. Many of these resources can be
obtained from <https://resources.gem5.org>.

More information on gem5 Resources can be found at
<https://www.gem5.org/documentation/general_docs/gem5_resources/>.

## Getting Help, Reporting bugs, and Requesting Features

We provide a variety of channels for users and developers to get help, report
bugs, requests features, or engage in community discussions. Below
are a few of the most common we recommend using.

* **GitHub Discussions**: A GitHub Discussions page. This can be used to start
discussions or ask questions. Available at
<https://github.com/orgs/gem5/discussions>.
* **GitHub Issues**: A GitHub Issues page for reporting bugs or requesting
features. Available at <https://github.com/gem5/gem5/issues>.
* **Jira Issue Tracker**: A Jira Issue Tracker for reporting bugs or requesting
features. Available at <https://gem5.atlassian.net/>.
* **Slack**: A Slack server with a variety of channels for the gem5 community
to engage in a variety of discussions. Please visit
<https://www.gem5.org/join-slack> to join.
* **gem5-users@gem5.org**: A mailing list for users of gem5 to ask questions
or start discussions. To join the mailing list please visit
<https://www.gem5.org/mailing_lists>.
* **gem5-dev@gem5.org**: A mailing list for developers of gem5 to ask questions
or start discussions. To join the mailing list please visit
<https://www.gem5.org/mailing_lists>.

## Contributing to gem5

We hope you enjoy using gem5. When appropriate we advise charing your
contributions to the project. <https://www.gem5.org/contributing> can help you
get started. Additional information can be found in the CONTRIBUTING.md file.
