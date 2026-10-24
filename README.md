# auditeeg

**Auditing the evaluation of EEG decoding.**

auditeeg is an open-source framework for auditing how decoding scores are obtained in electroencephalography (EEG) and brain–computer interface (BCI) research. Rather than proposing another decoder, it measures how much of a reported score is produced by the evaluation itself: the way data are split and preprocessed, the defaults of benchmark software, and the rules by which results are selected and reported.

## Approach

Each audited mechanism is defined as a pair of evaluations on identical data and identical splits that differ in a single factor: a clean version and a flawed version. The difference between the two is tested over participants with paired, non-parametric statistics and corrected for multiple comparisons. Where possible, a mechanism is also detected statically, from a split manifest or from the installed code, without training any model.

The framework is model-agnostic. Pipelines from scikit-learn, pyRiemann, braindecode and SpeechBrain-MOABB can be audited directly, and tools in any other language can be audited through a file-based interface that exchanges split manifests and per-trial predictions.

## Scope

The audit covers four levels of an EEG decoding study:

- **Evaluation protocol** – information from test data reaching the model, and test data that do not match the population or setting of the claim;
- **Model selection and reporting** – choices made with the test score, and the statistics used to support a claim;
- **Signal validity** – non-neural or stimulus-locked signals that can carry the class label;
- **Toolchain** – silent defects and defaults of widely used benchmark libraries.

Paradigms studied so far include motor imagery, P300 event-related potentials and steady-state visual evoked potentials, under within-session, cross-session and cross-subject evaluation.

## Status

A manuscript describing the framework, its catalogue of audited mechanisms and the empirical results is in preparation. The full toolkit, documentation and audit catalogue will be released on this site upon acceptance of the manuscript.

The package name is reserved on PyPI (`pip install auditeeg`). The current placeholder release (0.0.1) contains only the statistics module.

## License

auditeeg is released under the BSD 3-Clause License.
