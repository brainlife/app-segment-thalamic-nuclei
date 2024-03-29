[![Abcdspec-compliant](https://img.shields.io/badge/ABCD_Spec-v1.1-green.svg)](https://github.com/brain-life/abcd-spec)
[![Run on Brainlife.io](https://img.shields.io/badge/Brainlife-brainlife.app.222-blue.svg)](https://doi.org/10.25663/brainlife.app.222)

# Segment thalamic nuclei 

This app will segment the thalamus into its multiple components using the developer version of Freesurfer’s segmentThalamicNuclei.sh function (http://freesurfer.net/fswiki/ThalamicNuclei). This app takes a Freesurfer segmentation in as an input and generates .mgz files with the appropriate thalamic segmentation inside the Freesurfer directory as an output. 

### Authors 

- Brad Caron (bacaron@iu.edu) 

### Contributors 

- Soichi Hayashi (hayashis@iu.edu) 

### Funding 

[![NSF-BCS-1734853](https://img.shields.io/badge/NSF_BCS-1734853-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1734853)
[![NSF-BCS-1636893](https://img.shields.io/badge/NSF_BCS-1636893-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1636893)
[![NSF-ACI-1916518](https://img.shields.io/badge/NSF_ACI-1916518-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1916518)
[![NSF-IIS-1912270](https://img.shields.io/badge/NSF_IIS-1912270-blue.svg)](https://nsf.gov/awardsearch/showAward?AWD_ID=1912270)
[![NIH-NIBIB-R01EB029272](https://img.shields.io/badge/NIH_NIBIB-R01EB029272-green.svg)](https://grantome.com/grant/NIH/R01-EB029272-01)

### Citations 

Please cite the following articles when publishing papers that used data, code or other resources created by the brainlife.io community. 

1. Iglesias, J. E., Insausti, R., Lerma-Usabiaga, G., Bocchetta, M., Van Leemput, K., Greve, D. N., van der Kouwe, A., Alzheimer's Disease Neuroimaging Initiative, Fischl, B., Caballero-Gaudes, C., & Paz-Alonso, P. M. (2018). A probabilistic atlas of the human thalamic nuclei combining ex vivo MRI and histology. NeuroImage, 183, 314–326. https://doi.org/10.1016/j.neuroimage.2018.08.012 

## Running the App 

### On Brainlife.io 

You can submit this App online at [https://doi.org/10.25663/brainlife.app.222](https://doi.org/10.25663/brainlife.app.222) via the 'Execute' tab. 

### Running Locally (on your machine) 

1. git clone this repo 

2. Inside the cloned directory, create `config.json` with something like the following content with paths to your input files. 

```json 
{
   "freesurfer":    "testdata/freesurfer/output"
} 
``` 

### Sample Datasets 

You can download sample datasets from Brainlife using [Brainlife CLI](https://github.com/brain-life/cli). 

```
npm install -g brainlife 
bl login 
mkdir input 
bl dataset download 
``` 

3. Launch the App by executing 'main' 

```bash 
./main 
``` 

## Output 

The main output of this App is is the Freesurfer directory containing the ThalamicNuclei*.mgz files. These can be fed into the 'Generate ROIs in dMRI Space' apps under the 'thalamic' options. 

#### Product.json 

The secondary output of this app is `product.json`. This file allows web interfaces, DB and API calls on the results of the processing. 

### Dependencies 

This App requires the following libraries when run locally. 

- Freesurfer: https://surfer.nmr.mgh.harvard.edu/fswiki/DownloadAndInstall
- FSL: https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FslInstallation
- jsonlab: https://github.com/fangq/jsonlab
- singularity: https://singularity.lbl.gov/quickstart
