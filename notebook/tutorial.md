# LC-MS/MS Metabolomics Tutorial (Galaxy)

## 🔬 Project Description
This repository follows the Galaxy tutorial for LC-MS/MS-based metabolomics analysis.
The goal is to understand the processing pipeline of raw mass spectrometry data and extract meaningful biological insight.

## 📁 Folder Structure
- `raw_data/`: Raw mzML files or data obtained from the Galaxy server
- `notebooks/`: Notes, markdown files, and Jupyter notebooks
- `results/`: Output from data processing, figures, tables

## Tutorial Source
Based on the Galaxy Training Network tutorial:
👉 [LC-MS analysis (Metabolomics)](https://training.galaxyproject.org/training-material/topics/metabolomics/tutorials/lcms/tutorial.html#preprocessing-with-xcms)

## Questions:
What are the main steps of untargeted LC-MS data processing for metabolomic analysis?

How to conduct metabolomic data analysis from preprocessing to annotation using Galaxy?

## Objectives:
To comprehend the diversity of LC-MS metabolomic data analysis.

To get familiar with the main steps constituting a metabolomic workflow for untargeted LC-MS analysis.

To evaluate the potential of a workflow approach when dealing with LC-MS metabolomic data.

## Galaxy Login and History Setup
- Go to [Galaxy Europe](https://usegalaxy.eu/)
- Create an account or log in
- Create a new history: `LCMSMS Tutorial`
- ![Login to Galaxy](Images/new.jpg)

## Step 1: Importing the lc-ms data into galaxy
-Importing via links
Copy the link location
Click galaxy-upload Upload Data at the top of the tool panel

Click on Collection on the top

Select galaxy-wf-edit Paste/Fetch Data
Paste the link(s) into the text field

Change Type (set all): from “Auto-detect” to mzml

Press Start

Click on Build when available

Enter a name for the collection

sacurine
Click on Create list (and wait a bit)

or

As an alternative to uploading the data from a URL or your computer, the files may also have been made available from a shared data library:

Go into Libraries (left panel)
Navigate to the correct folder as indicated by your instructor.
On most Galaxies tutorial data will be provided in a folder named Libraries - GTN - Material
- Metabolomics Mass spectrometry: LC-MS analysis

Click on Add to History galaxy-dropdown near the top and select as a Collection from the dropdown menu
In the pop-up window, choose

“Select history”: the history we want to import the data to (or create a new one)
Click on Import

## Step 2: Data preparation for XCMS: MSnbase readMSData
- Launch the pre-defined workflow from tools menu typing Msnbase
  we get a Dataset collection containing 9 dataset. The datasets are some RData objects with the rdata.msnbase.raw datatype.
- Now that we have prepared the data, we can begin with the first XCMS extraction step: peakpicking. However, before beginning to extract meaningful information from the raw data, we may be interested in visualising your chromatograms. This can be of particular interest if you want to check whether we should consider discarding some range of your analytical sequence (some scan or retention time (RT) ranges).

To do so, we can use a tool that is called xcms plot chromatogram tool that will plot each sample’s chromatogram (see dedicated section further). However, to use this tool, we may need additional information about your samples for colouring purpose. 

Thus, we may need to upload into Galaxy a table containing metadata of our samples (a sampleMetadata file).

##Step 3 : Importing a sample metadata file
 - A sampleMetadata file corresponds to a table containing information about the samples (= sample metadata).

A sample metadata file contains various information for each of your raw files:

--Classes which will be used during the preprocessing steps
--Analytical batches which will be useful for a batch correction step, along with sample types (pool/sample) and injection order
--Different experimental conditions which can be used for statistics
--information about samples that you want to keep, in a column format
--The content of your sample metadata file has to be filled by you, since it is not contained in your raw data. Note that you can either:

how to Upload an existing metadata file:
Use a template to create one (because it can be painful to get the sample list without misspelling or omission)
Generate a template with the xcms get a sampleMetadata file tool tool
Fill it using your favorite table editor (Excel, LibreOffice etc.)
Upload it within Galaxy

For this Tutorial

open xcms get a samplemetadata file from tools and load the xcms get a sampleMetadata file tool with the following parameters: param-collection “RData file”: the sacurine.raw.RData collection output from MSnbase readMSData 

##From this tool, we obtain a tabular file (meaning a tab-separated text file) with a first column of identifiers and a second column called class which is empty for the moment (only ‘.’ for each sample). You can now download this file by clicking on the galaxy-save icon.

Tip: Changing the datatype
Click on the galaxy-pencil pencil icon for the dataset to edit its attributes
In the central panel, click galaxy-chart-select-data Datatypes tab on the top
In the galaxy-chart-select-data Assign Datatype, select your desired datatype from “New Type” dropdown
Tip: you can start typing the datatype into the field to filter the dropdown menu
Click the Save button

## Step 4:Getting an overview of your samples’ chromatograms
the sampleMedata file we previously uploaded to add some group colours to your samples when visualising your chromatograms. The tool automatically takes the second column as colour groups when a file is provided.

Hands On: xcms plot chromatogram
xcms plot chromatogram tool with the following parameters:
“RData file”: sacurine.raw.RData (collection)
“Sample metadata file”: sampleMetadata_completed.tsv you uploaded previously