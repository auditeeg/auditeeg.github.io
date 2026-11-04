# auditeeg

**Auditing the evaluation of EEG decoding.**

auditeeg is an open-source framework for auditing how decoding scores are obtained in electroencephalography (EEG) and brain–computer interface (BCI) research. It measures how much of a reported score is produced by the evaluation itself: the way data are split and preprocessed, the defaults of benchmark software, and the rules by which results are selected and reported.

## Principles

auditeeg follows five principles, CLEAN:

- **Counterfactual** – every flaw is measured against its clean twin on the same data and the same split;
- **Lifecycle-wide** – the audit spans the whole study, from design and data acquisition to reporting;
- **Evidence-based** – effects are tested over participants, and every number is traceable to a result file and a code version;
- **Actionable** – every audited flaw comes with a remedy and a check, cheap static checks first;
- **Non-intrusive** – the authors' own pipeline is audited as it is, and other tools through split and prediction files.

## Approach

Each audited mechanism is defined as a pair of evaluations on identical data and identical splits that differ in a single factor: a clean version and a flawed version. The difference between the two is tested over participants with paired, non-parametric statistics and corrected for multiple comparisons. Where possible, a mechanism is also detected statically, from a split manifest or from the installed code, without training any model.

The framework is model-agnostic. Pipelines from scikit-learn, pyRiemann, braindecode and SpeechBrain-MOABB can be audited directly, and tools in any other language can be audited through a file-based interface that exchanges split manifests and per-trial predictions.

## Scope

The audit follows the life cycle of an EEG decoding study, from study design and data splitting through preprocessing, model training and model selection to claims and reporting. At each stage it covers information from test data reaching the model, signals that are not neural but carry the class label, choices made with the test score, claims that do not match the evaluation, statistics used to support a claim, and pipelines that run differently from what was stated. Concrete cases observed in widely used benchmark software and in published studies are recorded alongside each flaw.

Paradigms studied so far include motor imagery, P300 event-related potentials and steady-state visual evoked potentials, under within-session, cross-session and cross-subject evaluation.

## Status

A manuscript describing the framework, its catalogue of audited mechanisms and the empirical results is in preparation. The full toolkit and documentation will be released on this site upon acceptance of the manuscript, together with a curated, continuously updated catalogue of evaluation flaws.

The package name is reserved on PyPI (`pip install auditeeg`). The current placeholder release (0.0.1) contains only the statistics module.

## Team

- Rolly Maulana Awangga – rollymaulanaa@student.telkomuniversity.ac.id
- Prof. Dr. Suyanto, S.T., M.Sc. – suyanto@telkomuniversity.ac.id
- Bedy Purnama, S.Si., M.T., Ph.D. – bedypurnama@telkomuniversity.ac.id

School of Computing, Center of Excellence Artificial Intelligence for Learning and Optimization, Telkom University

## License

auditeeg is released under the BSD 3-Clause License.
