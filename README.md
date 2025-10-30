# models-by-amber
Physics models found by AMBer, an autonomous model builder, as described in [2506.08080](https://arxiv.org/abs/2506.08080). Please used the bibtex citation provided below when using models from this repository.

## File Format
Model files are txt files containing a json dictionary with the following fields:
- "representations": A matrix encoding the representations of all particles under the non-Abelian and Abelian symmetries. There is a sublist for each particle. In each sublist, the non-Abelian symmetry is one-hot encoded, while the Abelian symmetry charge is given directly from 1-N, where N is the order of the Abelian symmetry.
- "associations": A list identifying which particles are packed together in multiplets. Using the "particles" index below, those with the same non-zero integer are in the same multiplet. 0 indicates the particle is in a singlet.
- "fixed_flavon_vevs": A list mapping flavons to their VEV alignment (see below)
- "n_params": Number of free parameters in the model, referenced as n<sub>p</sub> in [2506.08080](https://arxiv.org/abs/2506.08080).
- "param_dict": A dictionary where the keys are the free parameters of the model and the values are the best fit values found by AMBer.
- "ZN_symmetries": A list of the order of the Abelian symmetries in the model.
- "particles": A list identifying the particles in the model, can be used to index the representation matrix.
- "eff_flav": Number or flavons that contribute to the Lagrangian.
- "flavons_not_present": A list of flavons specified by the model but not contributing to the Lagrangian.
- "total_chisq": The chi-squared fit AMBer found for this model, the value used in the reward function in [2506.08080](https://arxiv.org/abs/2506.08080).
- "m_b": The effective electron neutrino mass.
- "m_bb": The effective Majorana mass.
- "Sum(m_i)": The sum of the neutrino masses.
- "m1": The lightest neutrino mass.


## Read-in Code
The notebook modeltxt_To_LatexTable.ipynb converts a model file into latex code that displays the model in a human readable format. This notebook can also serve as an example for how to interact with model files so that a user can write their own model processing code.

## non-Abelian Encoding

### A4
In the "representations" matrix, the A4 representations are one hot encoded according to:
(1, 1', 1", 3)

### T19
In the "representations" matrix, the T19 representations are one hot encoded according to:
(1, 1', 1", 3<sub>1</sub>, 3̅<sub>1</sub>, 3<sub>2</sub>, 3̅<sub>2</sub>, 3<sub>3</sub>, 3̅<sub>3</sub>)

## VEV Alignment Mapping
The "fixed_flavon_vevs" list indicates the VEV alignment of the flavons, with integers mapping to VEV alignments following:
- 1: flavon is in a singlet
- 2: (1, 0, 0)
- 3: (1, 1, 1)
- 4: (0, 1, 0)
- 5: (0, 0, 1)
- 6: (0, 0, -1)
- 7: (1, ω<sup>2</sup>, ω)
- 8: (1, ω, ω<sup>2</sup>)

ω = exp(2πi/3)

## Citation
```bibtex
@misc{baretz2025aiassistedneutrinoflavortheory,
      title={Towards AI-assisted Neutrino Flavor Theory Design}, 
      author={Jason Benjamin Baretz and Max Fieg and Vijay Ganesh and Aishik Ghosh and V. Knapp-Perez and Jake Rudolph and Daniel Whiteson},
      year={2025},
      eprint={2506.08080},
      archivePrefix={arXiv},
      primaryClass={hep-ph},
      url={https://arxiv.org/abs/2506.08080}, 
}
