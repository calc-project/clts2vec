# CLTS2Vec

This lightweight Python package provides a robust tool for translating sounds into phonological feature vectors. It is described in detail in our submitted paper "A Generative System for Translating Sounds to Phonological Feature Vectors".

## Installation

Make sure you have cloned into this repository, and `clts2vec` is your current working repository. Then, you can simply install all dependencies by running:

```
clts2vec$ pip install -e .
```

If you wish to reproduce the evaluation from our paper, you also need to download the evaluation data from Lexibank. For this, simply run:

```
clts2vec$ make download
```

This will clone the [`lexibank-analysed`](https://github.com/lexibank/lexibank-analysed) dataset into the `eval` directory.

After running the evaluation scripts, you can clear the data from your disk by running the command:

```
clts2vec$ make clear
```

## Usage

The core of this package is the `parse` function, which translates a valid IPA symbol to its corresponding feature vector:

```python
>>> from clts2vec.parse import parse
>>> parse("t")
(1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, -1, 1, -1, -1, -1, -1, -1, 0, 0, -1, -1, -1, 1, -1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0)
```

A more readable string representation of the feature vector can be obtained with the `vec_to_str` function:

```python
>>> from clts2vec.parse import parse
>>> from clts2vec.utils import vec_to_str
>>> vec_to_str(parse("t"))
'+cons,-syl,-son,-cont,-delrel,-lat,-nas,-voi,-sg,-cg,-pharyngeal,-laryngeal,+cor,-dorsal,-lab,-hi,-lo,-back,0_front,0_tense,-round,-velaric,-long,+ant,-distr,0_strid,0_hitone,0_hireg,0_loreg,0_rising,0_falling,0_contour,0_backshift,0_frontshift,0_opening,0_closing,0_centering,0_longdistance,0_secondrounded'
```

## Evaluation

The `eval` directory provides the code that was used for the Evaluation section in the paper. If you wish to reproduce our results reported in the paper, make sure that you have installed the dependencies and downloaded the data (see above). Then, you can simply run all evaluation scripts - with each file corresponding to a subsection of the paper with the same name.
