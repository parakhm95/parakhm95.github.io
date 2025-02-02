---
layout: distill
title:  The fragments of acados documentation
date: 2023-02-18 22:39:00
description: The non-desperate search through another ill-documented project with good examples
tags: research, ocp, nlp, optimisation, acados
categories: software
# thumbnail: assets/img/9.jpg
related_posts: false

authors:

- name: Parakh M. Gupta
  # url: "https://en.wikipedia.org/wiki/Albert_Einstein"
  affiliations:
   name: MRS, CTU-Prague

---

# Acados Default Documentation links

For Python: `https://docs.acados.org/python_interface/index.html#overview`
For Problem Formulation: `https://github.com/acados/acados/blob/master/docs/problem_formulation/problem_formulation_ocp_mex.pdf`

## ACADOS CPP

### Indices/Enumerators

ACADOS uses some strange pre-processor directives to enumerate indices used for the size of state and control vectors. They can be located in `acados_solver_<your_project_name>.h`. Here is what they mean:

`QUADROTOR_ODE_NX` : This is the size/length of the state vector of the model.  
`QUADROTOR_ODE_NY0` : We use `yref` to set elements of the cost function, and this is the length of `yref` for zeroth iteration which is the initial state.  
`QUADROTOR_ODE_NY` : Length of `yref` for iterations from `1` upto `N-1`.  
`QUADROTOR_ODE_NYN` : Length of `yref` for the last iteraton `N`, is smaller than `QUADROTOR_ODE_NY` by the size of control vector(`QUADROTOR_ODE_NU`) because control reference is not provided for the last shooting node.  
`QUADROTOR_ODE_N` : Number of shooting nodes / number of predictions.  
`QUADROTOR_ODE_NU` : Length of the control input vector.  
`QUADROTOR_ODE_NP` : Length of the parameters vector supplied to acados.  

