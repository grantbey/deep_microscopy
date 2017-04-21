# README

This is the shared code for the deep_microscopy project. The goal is to segment microscopy images for cell nuclei in the DAPI channel, then classify those nuclei as infected or uninfected using data from the green channel (stained for influenza NP and labelled with Alexa fluor 488) and finally quantify how often the protein stained in the red channel (Alexa fluor 647) relocates to the nucleolus upon infection.

### Files

data_proc.ipynb is the data processing notebook. Here the tif file is loaded and pixel values are normalized to E[0,1]. The binary masks for nuclei and infected cells are also loaded, and everything is saved to an h5py file. Additionally, the training image and both masks are divided into 100 equally sized tiles for training.

u-net-version_1.0.ipynb is the initial attempt to segment nuclei using only the blue channel data.

plotly_streaming.ipynb gets the run number and the plot.ly URL for the streaming plot. The `tls.embed()` call loads the plot, which then updates live with the training loss and jaccard index.