# J25 electricity and heat control cost audit

Reproducibility code for **Auditing cost savings in learning assisted electricity and heat control with matched service and storage**.

Authors: Anfal Hathah and Md Mottahir Alam. ORCID: https://orcid.org/0000-0003-2127-7183.

The audit crosses exact hourly delivered heat and final thermal inventories between two recorded policies. Saved LP primal and dual solutions support numerical checks before the electricity-cost gap is separated into native dispatch regret, service and final-storage terms.

## Files

- `J25_Reproducibility_Code_v1_0_0.zip`: 73 source, test and scientific-configuration files with a SHA256 manifest. Extracting the ZIP preserves the package paths used by the programs.
- Complete public data, fitted models, controller trajectories, audit solutions and executable source: https://doi.org/10.5281/zenodo.23978238.
- `CITATION.cff`: software citation metadata.
- `LICENSE.txt` and `THIRD_PARTY_NOTICES.txt`: component-specific license terms.

The source ZIP preserves the directory layout while keeping large numerical arrays out of Git history. The complete Zenodo archive includes the same source code.

## Reproduce

Download and extract `J25_Public_Data_Reproducibility_v1_0_0.zip` from Zenodo into a fresh directory. Keep `J25_v0_8` and `science_v05` as siblings. These directory names identify the frozen experiment; the public release is 1.0.0.

From the extracted root:

```bash
python verify_archive.py
python -m pip install -r J25_v0_8/requirements_v0_8.txt
python -m unittest discover -s science_v05/reviewer_project/tests
python -m unittest discover -s J25_v0_8/src -p "test_*.py"
python J25_v0_8/src/reproduce.py --quick --work-dir /new/path/quick_repeat
python J25_v0_8/src/recompute_audit.py --quick --work-dir /new/path/audit_repeat
python J25_v0_8/src/verify_science.py
```

Output directories must not already exist. The inner README gives full-repetition commands and instructions for the separate dynamic FMU study. Install the pinned dependencies before loading the fitted models. The primary public-profile experiment requires no FMU runtime or new data capture.

## Recorded evidence

The reference results contain 4,032 policy rollouts, including 2,688 rollouts on 36 additional public building profiles, and 9,976 distinct saved audit LP solutions. All 28 original tests and eight audit tests passed. Six new-cohort episodes repeated exactly, and four audit cases covering 56 policy contrasts were re-solved. A second full campaign was not run.

The learned controller had a lower bill than Rule 100 but did not meet its thermal-service improvement criterion. The audit is offline model-based accounting, not a causal effect or field certificate. The additional profiles share source climates and annual weather sequences.

## License

Project code follows the included MIT license. CityLearn, ResStock/EULP and BOPTEST materials retain their original licenses and attribution, including CC BY 4.0 where applicable. See the notices and source manifests in the complete archive. The deposit contains reproducibility materials rather than the manuscript or author-only documents.
