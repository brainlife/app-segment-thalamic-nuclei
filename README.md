<h1 align="center">Segment thalamic nuclei</h1>

<p align="center">
  A segmentation of the thalamus into its nuclei, added to an existing FreeSurfer output with FreeSurfer 7.1.0 <code>segmentThalamicNuclei.sh</code>.
</p>

<p align="center">
  <a href="https://github.com/brainlife/abcd-spec"><img src="https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg" alt="ABCD Spec v1.1"></a>
  <a href="https://doi.org/10.25663/brainlife.app.222"><img src="https://img.shields.io/badge/Brainlife-brainlife.app.222-blue.svg" alt="Run on brainlife.io"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-lightgrey.svg" alt="MIT license"></a>
</p>

> 📍 **This branch, `v1.0`, is the brainlife.io App Segment thalamic nuclei** ([doi:10.25663/brainlife.app.222](https://doi.org/10.25663/brainlife.app.222)).

## 🧠 At a glance

<!-- brainlife-app:begin (generated from the App manifest; edit the manifest, not this block) -->

> **Segments the thalamus into its nuclei with FreeSurfer 7.1.0 segmentThalamicNuclei.sh on an existing FreeSurfer output and returns the FreeSurfer directory with the thalamic nuclei segmentation added.**

Copies the input FreeSurfer subject directory and runs segmentThalamicNuclei.sh (probabilistic atlas built from histology) to add ThalamicNuclei volumes to mri/. Use it when an analysis needs thalamic nuclei such as the LGN, for example the visual white matter ROI Apps. The input must be a completed recon-all output.

| | |
|---|---|
| 📥 **Inputs** | `neuro/freesurfer` |
| 📤 **Outputs** | `neuro/freesurfer` |
| 🐳 **Container** | `brainlife/freesurfer:7.1.0` |
| ⚙️ **Resources** | 2 CPUs · 20 GB memory · 0.75 h walltime |
| 🔑 **Requires** | `FREESURFER_LICENSE` |
| 🔗 **Run it** | [doi.org/10.25663/brainlife.app.222](https://doi.org/10.25663/brainlife.app.222) |

#### 📥 Inputs

| Input | Datatype | Required | Description |
|---|---|---|---|
| `freesurfer` | `neuro/freesurfer` | yes | The path to the freesurfer datatype |

#### 📤 Outputs

| Output | Datatype | Description |
|---|---|---|
| `output` | `neuro/freesurfer` | Output freesurfer datatype including thalamic nuclei segmentation |

<!-- brainlife-app:end -->

## 🔬 How it works

The App copies the input FreeSurfer subject directory and runs FreeSurfer's [`segmentThalamicNuclei.sh`](https://surfer.nmr.mgh.harvard.edu/fswiki/ThalamicNuclei), which segments the thalamus into its nuclei with a probabilistic atlas built from ex vivo MRI and histology (Iglesias et al., 2018). The `ThalamicNuclei*.mgz` volumes are written into the `mri/` directory of the copy. Use it when an analysis needs thalamic nuclei such as the lateral geniculate nucleus (LGN), for example the visual white matter ROI Apps.

## 🚀 Running the App

### ☁️ On brainlife.io

Open the App at [doi.org/10.25663/brainlife.app.222](https://doi.org/10.25663/brainlife.app.222), choose a completed FreeSurfer (`neuro/freesurfer`) output from your project and press **Execute**. The FreeSurfer directory with the thalamic segmentation is archived to your project as a `neuro/freesurfer` dataset tagged `thalamic_nuclei`. Its `ThalamicNuclei*.mgz` files can be fed into the *Generate ROIs in dMRI Space* Apps under the thalamic options.

### 💻 Locally

You need [Singularity/Apptainer](https://apptainer.org/), [`jq`](https://jqlang.github.io/jq/) and a [FreeSurfer license](https://surfer.nmr.mgh.harvard.edu/registration.html). `main` runs `run.sh` inside the `brainlife/freesurfer:7.1.0` container.

1. Clone this repository and check out the App's branch: `git checkout v1.0`.
2. Create `config.json` with the path to your FreeSurfer subject directory:

   ```json
   {
       "freesurfer": "/input/freesurfer/output"
   }
   ```

3. Export your FreeSurfer license and run the App:

   ```bash
   export FREESURFER_LICENSE="$(cat ~/freesurfer/license.txt)"
   ./main
   ```

## 📦 Outputs

`output/output/` is a copy of the input FreeSurfer subject directory with the thalamic nuclei segmentation added:

```text
output/output/
└── mri/
    ├── ThalamicNuclei.*.mgz    thalamic nuclei segmentations
    └── …                       the rest of the FreeSurfer subject directory
```

## 🩺 Troubleshooting

- **The segmentation fails early**: the input must be a completed `recon-all` output.

## 📚 Citing

> [!TIP]
> If you use this App in your work, please cite the App, the software it builds on and brainlife.io (below). GitHub's **Cite this repository** button gives the App citation in APA and BibTeX.

- Iglesias JE, Insausti R, Lerma-Usabiaga G, Bocchetta M, Van Leemput K, Greve DN, van der Kouwe A, Alzheimer's Disease Neuroimaging Initiative, Fischl B, Caballero-Gaudes C, Paz-Alonso PM. A probabilistic atlas of the human thalamic nuclei combining ex vivo MRI and histology. *NeuroImage* 183:314–326 (2018). [doi:10.1016/j.neuroimage.2018.08.012](https://doi.org/10.1016/j.neuroimage.2018.08.012)
- Segment thalamic nuclei. brainlife.io App. [doi:10.25663/brainlife.app.222](https://doi.org/10.25663/brainlife.app.222)
- Fischl. FreeSurfer. *NeuroImage* 62:774-781 (2012). [doi:10.1016/j.neuroimage.2012.01.021](https://doi.org/10.1016/j.neuroimage.2012.01.021)
- Hayashi S, Caron BA, Heinsfeld AS, et al. brainlife.io: a decentralized and open-source cloud platform to support neuroscience research. *Nature Methods* 21:809–813 (2024). [doi:10.1038/s41592-024-02237-2](https://doi.org/10.1038/s41592-024-02237-2)
- Avesani P, McPherson B, Hayashi S, et al. The open diffusion data derivatives, brain data upcycling via integrated publishing of derivatives and reproducible open cloud services. *Scientific Data* 6:69 (2019). [doi:10.1038/s41597-019-0073-y](https://doi.org/10.1038/s41597-019-0073-y)

## 👥 Authors

- Brad Caron

**Contributors:** Soichi Hayashi

## 💰 Funding

[![Wellcome-226486/Z/22/Z](https://img.shields.io/badge/Wellcome-226486%2FZ%2F22%2FZ-purple.svg)](https://wellcome.org/)
[![NIH-NINDS-U24NS140384](https://img.shields.io/badge/NIH_NINDS-U24NS140384-green.svg)](https://reporter.nih.gov/project-details/11261037)
[![NIH-NINDS-UM1NS132207](https://img.shields.io/badge/NIH_NINDS-UM1NS132207-green.svg)](https://reporter.nih.gov/project-details/11411328)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://reporter.nih.gov/project-details/10262925)
[![NIH-NIBIB-R01EB030896](https://img.shields.io/badge/NIH_NIBIB-R01EB030896-green.svg)](https://reporter.nih.gov/project-details/10428625)
[![NIH-NIMH-R01MH126699](https://img.shields.io/badge/NIH_NIMH-R01MH126699-green.svg)](https://reporter.nih.gov/project-details/10460628)
[![NIH-NIDCD-R01DC020088](https://img.shields.io/badge/NIH_NIDCD-R01DC020088-green.svg)](https://reporter.nih.gov/project-details/11140284)
[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-2203524](https://img.shields.io/badge/NSF_BCS-2203524-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2203524)
[![NSF-IIS-1636893](https://img.shields.io/badge/NSF_IIS-1636893-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-OAC-2148729](https://img.shields.io/badge/NSF_OAC-2148729-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148729)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NSF-IIS-2148700](https://img.shields.io/badge/NSF_IIS-2148700-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=2148700)
[![NSF-OAC-1916518](https://img.shields.io/badge/NSF_OAC-1916518-blue.svg)](https://www.nsf.gov/awardsearch/showAward?AWD_ID=1916518)

<sub>brainlife.io is publicly funded, and acknowledging that support helps keep it running. This App was developed with support from Wellcome, the U.S. National Institutes of Health (including the BRAIN Initiative BRAIN CONNECTS program: The Axonal Projectome EXchange, U24NS140384, and the Center for Mesoscale Connectomics, UM1NS132207) and the U.S. National Science Foundation.</sub>

## ⚖️ License

[MIT](LICENSE). FreeSurfer is distributed under its own [license](https://surfer.nmr.mgh.harvard.edu/fswiki/FreeSurferSoftwareLicense).
