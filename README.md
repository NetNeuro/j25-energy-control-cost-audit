# J25 electricity and heat control cost audit

Reproducibility materials for Auditing cost savings in learning assisted electricity and heat control with matched service and storage.

Authors: Anfal Hathah and Md Mottahir Alam. ORCID: https://orcid.org/0000-0003-2127-7183.

Complete source code, public datasets, fitted models, controller trajectories, saved LP solutions and tests: https://doi.org/10.5281/zenodo.23978238 (version 1.0.0).

The four-contract audit crosses exact hourly delivered heat and final thermal inventories. The reference results contain 4,032 controller rollouts and 9,976 audit LP solutions. The learned policy had a lower bill than Rule 100 but did not meet its thermal-service criterion.

Extract the complete Zenodo archive into a fresh directory. Keep J25_v0_8 and science_v05 as siblings. From the extracted root:

```bash
python verify_archive.py
python -m pip install -r J25_v0_8/requirements_v0_8.txt
python -m unittest discover -s science_v05/reviewer_project/tests
python -m unittest discover -s J25_v0_8/src -p "test_*.py"
python J25_v0_8/src/reproduce.py --quick --work-dir /new/path/repeat
```

The output directory must not already exist. Full reproduction commands, source provenance and component-specific licenses are included. Project code follows the included MIT license; datasets and third-party components retain their licenses. No new data capture is required.
