# Residential heat-pump controller cost audit

Reproducibility materials for **Auditing building-controller cost savings in
residential heat-pump systems with matched heat service and final storage**.

Authors: Anfal Hathah and Md Mottahir Alam.
ORCID: https://orcid.org/0000-0003-2127-7183.

The current complete public-data archive is Zenodo version 1.2:
https://doi.org/10.5281/zenodo.24109049. No earlier Zenodo release is required.

## Files

- `J25_Reproducibility_Code_v1_2.zip`: executable source, tests, configurations
  and source manifests, including the extension and S17 analysis. Download the
  full Zenodo package for raw profiles, fitted models and numerical arrays.
- `J25_Supplementary_Analysis_Code_v1_0.zip`: a self-contained reproduction of
  main Table 11 and Supplement S17 with selected audit records, fixed settings,
  paired-bootstrap code and results. This same ZIP is included in Zenodo 1.2.
- `CITATION.cff`, `LICENSE.txt`, `THIRD_PARTY_NOTICES.txt`, `SHA256SUMS.txt`:
  citation, rights and checksums.

## Reproduce

Download all files from Zenodo version 1.2 into one directory, then run:

```bash
python prepare_package.py --out J25_Reproduction
cd J25_Reproduction
python verify_package.py
python -m pip install -r J25_v0_8/requirements_v0_8.txt
python J25_v0_8/src/verify_science.py
python J25_Supplementary_Analysis_v1_0/analyze.py --output s17_repeat
```

For only the added regime and uncertainty analysis, extract the supplementary
analysis ZIP and run `python analyze.py --output regenerated_results` from its
directory after installing its requirements.

## Evidence and scope

The controller campaign covers 87 test homes and 6,496 rollouts. All 17,375
distinct dispatch LPs passed the numerical checks. The 36-home replication
was repeated from regenerated models before the 33-home extension.

In replication, service and storage explain 0.77% of fixed-COP MPC savings
in nominal replays and 27.33% under conversion stress, or 16.17% pooled
(95% descriptive interval 8.47–22.83%). The learned scorer's share is 0.20%
(−0.31–0.82%). With adaptive MPC as reference, the scorer costs 1,520.30 units
more. Combined 69-home contract shares are 15.72% and 0.10%.

The 2,464 extension trajectory arrays and 6,843 extension LP arrays are
regenerated from archived inputs and scripts; expected hashes and original
verification receipts are supplied. The archive README explains fresh-output
directories and the complete controller, audit and dynamic-study commands.

Results use simulated public profiles, assumed equipment and tariffs, one
source weather year and weekly inventory resets. The audit accounts for
electricity cost under the stated model; heat-service attribution does not
measure occupant welfare. Scientific limitations remain part of the record.

## Rights

Project code uses the included MIT license. CityLearn, ResStock/EULP and
BOPTEST components retain their original licenses and attribution.
