# InSAR-Tropospheric-Filtering
## NASA Space Apps Challenge 2022 - InSAR Change Detectives Submission

## Concept:

We can apply statistical ideas to our filtering approach. Atmospheric interference changes at a much faster pace than geological phenomena like a fault creep. It is also always present, unlike an earthquake which may be thought of as a one-time event. This means that atmospheric noise is high-frequency and can be expected to vary between every single measurement.

Atmospheric noise likely lowers the coherence of data within the region as well. Then, we can compare readings from different measurements, and if they differ significantly, throw away the less coherent version.

If the occurrence of a major "one-time" event occurs between readings, then this filtering method should be applied separately to readings before and after the event, to not filter the event itself.

## Step-By-Step Filtering Procedure:

 - load all the netCDF data within a folder inside several arrays
 - create new arrays for the filtered data and copy the first file's data into it (as a starting point)
 - break each file's data into small "cells" - a narrow range of latitude/longitude values
 - compare the filtered data cells with the next file's cells, measure the cosine similarity between them
 - if they are too dissimilar, and the next file's cell is more coherent than the filtered data cell, overwrite the filtered cell with the other data
 - repeat for every file loaded into the notebook

## Advantages Of This Approach:

 - targets all forms of high-frequency noise
 - does not blur or crop the data, simply selects the "best" data
 - does not require weather data to work
 - simple to understand and implement

## Tools Used:
 - Python - Google Colab Notebook
 - netCDF4-python: allows us to read & write to netCDF files containing all the critical InSAR data
 - Panoply: used to visualize netCDF files, understand the file structure & data, and create plots to validate our code

Run my code here (Google Colab)! https://drive.google.com/file/d/1Ol0NSInEkUansEyhNXDG47qiFW0dTjLc/view?usp=sharing 
