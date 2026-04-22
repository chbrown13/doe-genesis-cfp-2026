Pyomo Overview
Pyomo is a Python-based open-source software package that supports a diverse set of optimization capabilities for formulating and analyzing optimization models. Pyomo can be used to define symbolic problems, create concrete problem instances, and solve these instances with standard solvers. Pyomo supports a wide range of problem types, including:

Linear programming
Quadratic programming
Nonlinear programming
Mixed-integer linear programming
Mixed-integer quadratic programming
Mixed-integer nonlinear programming
Mixed-integer stochastic programming
Generalized disjunctive programming
Differential algebraic equations
Mathematical programming with equilibrium constraints
Constraint programming
Pyomo supports analysis and scripting within a full-featured programming language. Further, Pyomo has also proven an effective framework for developing high-level optimization and analysis tools. For example, the mpi-sppy package provides generic solvers for stochastic programming. mpi-sppy leverages the fact that Pyomo's modeling objects are embedded within a full-featured high-level programming language, which allows for transparent parallelization of subproblems using Python parallel communication libraries.

Pyomo Home
About Pyomo
Download
Documentation
Performance Plots
Pyomo was formerly released as the Coopr software library.

Pyomo is available under the BSD License - see the LICENSE.md file.

Pyomo is currently tested with the following Python implementations:

CPython: 3.10, 3.11, 3.12, 3.13, 3.14
PyPy: 3.11
Testing and support policy:

At the time of the first Pyomo release after the end-of-life of a minor Python version, we will remove testing for that Python version.

Installation
PyPI   PyPI version PyPI downloads
pip install pyomo
Anaconda   Anaconda version Anaconda downloads
conda install -c conda-forge pyomo
Tutorials and Examples
Pyomo — Optimization Modeling in Python
Pyomo Workshop Slides
Prof. Jeffrey Kantor's Pyomo Cookbook
The companion notebooks for Hands-On Mathematical Optimization with Python
Pyomo Gallery
Getting Help
To get help from the Pyomo community ask a question on one of the following:

Use the #pyomo tag on StackOverflow
Pyomo Forum
Developers
Pyomo development moved to this repository in June 2016 from Sandia National Laboratories. Developer discussions are hosted by Google Groups.

The Pyomo Development team holds weekly coordination meetings on Tuesdays 12:30 - 14:00 (MT). Please contact wg-pyomo@sandia.gov to request call-in information.

By contributing to this software project, you are agreeing to the following terms and conditions for your contributions:

You agree your contributions are submitted under the BSD license.
You represent you are authorized to make the contributions and grant the license. If your employer has rights to intellectual property that includes your contributions, you represent that you have received permission to make contributions and grant the required license on behalf of that employer.
Related Packages
See https://pyomo.readthedocs.io/en/latest/related_packages.html.
