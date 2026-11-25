<h1 align="center">BIDS Tracula (under development)</h1>

<p align="center">
  Reconstructs major white matter pathways with FreeSurfer TRACULA (bids/tracula v6.0.0-4 BIDS App) from a T1-weighted image, DWI and an optional FreeSurfer directory.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/bl.app.76"><img src="https://img.shields.io/badge/Brainlife-bl.app.76-blue.svg" alt="Run on brainlife.io"></a>
</p>

## At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Reconstructs major white matter pathways with FreeSurfer TRACULA (bids/tracula v6.0.0-4 BIDS App) from a T1-weighted image, DWI and an optional FreeSurfer directory.**

Arranges the T1w and DWI inputs into a one-subject BIDS dataset and runs the bids/tracula BIDS App (FreeSurfer 6 TRACULA, all stages) on it, reusing an existing FreeSurfer subject directory when given. The App is marked as under development. It needs a FreeSurfer license and can take up to a day of compute.

| | |
|---|---|
| **Inputs** | `neuro/anat/t1w` · `neuro/dwi` · `neuro/freesurfer` (optional) |
| **Outputs** | `raw` |
| **Container** | `bids/tracula:v6.0.0-4` |
| **Resources** | 8 CPUs · 24 h walltime |
| **Requires** | `FREESURFER_LICENSE` |
| **Run it** | [doi.org/10.25663/bl.app.76](https://doi.org/10.25663/bl.app.76) |

#### Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `t1` | `neuro/anat/t1w` | yes | T1 image |
| `dwi` | `neuro/dwi` | yes | DWI image |
| `freesurfer` | `neuro/freesurfer` | no | Optional FreeSurfer subject directory for the same subject; passed to TRACULA with --freesurfer_dir so recon-all is not rerun. |

#### Outputs

| Output | Datatype | Description |
|---|---|---|
| `tracula` | `raw` | TRACULA output directory for the subject as produced by the bids/tracula App. |

<!-- brainlife-app:end -->

## Running the App

### On brainlife.io

Open the App at [doi.org/10.25663/bl.app.76](https://doi.org/10.25663/bl.app.76), choose `neuro/anat/t1w`, `neuro/dwi`, `neuro/freesurfer` from your project and press **Execute**. The results are saved to your project as `raw`.

### Locally

You need [Singularity/Apptainer](https://apptainer.org/) (the App runs in `bids/tracula:v6.0.0-4`), [`jq`](https://jqlang.github.io/jq/), `FREESURFER_LICENSE`.

1. Clone this repository.
2. Create `config.json` with the paths to your inputs and the parameters:

   ```json
   {
       "t1": "/path/to/t1/t1",
       "bvals": "/path/to/dwi/bvals",
       "bvecs": "/path/to/dwi/bvecs",
       "dwi": "/path/to/dwi/dwi",
       "freesurfer": "/path/to/freesurfer/freesurfer"
   }
   ```

3. Run `./main`.

## Citing

If you use this App, please cite it, the software it builds on and brainlife.io:

- BIDS Tracula (under development). brainlife.io App. [doi:10.25663/bl.app.76](https://doi.org/10.25663/bl.app.76)
- Fischl. FreeSurfer. *NeuroImage* 62:774-781 (2012). [doi:10.1016/j.neuroimage.2012.01.021](https://doi.org/10.1016/j.neuroimage.2012.01.021)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## Authors

Maintained by [@soichih](https://github.com/soichih).
