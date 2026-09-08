# Copernicus 2016_2017

This directory is designed to retrieve Sentinel-2 L2A Bottom of Atmosphere imagery for 2016 and 2017. This is necessary because ESA/Copernicus hosts corrected imagery in the Copernicus Browser, but GEE does not see/support those data years.

CDSE_S2_C1_NCA_2016_2017.ipynb: We scrape Copernicus for our three tiles: T11TNJ; T11TNH; T11TPH. We retain our relevant bands, 2-12 + SCL, and the metadata necessary to recreate the QA60 bitmask.
CDSE_2016_2017_QA60_bitmask.ipynb: We rebuild the QA60 bitmask, and upload it to our GCS bucket so that we can see it as an image collection to run harmonics on. 
RGB_SCL_QA60_Diagnostic16-17.ipynb: writes figures comparing randomly sampled days per month to show masking gains by including QA60 - confirming that it is a necessary feature in our masking logic.
STEP_S2_C1_GCS_EE_ImageCollection_QA60_Rebuild.ipynb: Append QA60 to existing image collection.
STEP_S2_C1_GCS_EE_ImageCollection.ipynb: Upload image collection without QA60 - oops! can be deleted

There are multiple versions in here for a reason. At first, I uploaded without QA60 - needed to rebuild and append that to uploaded tiles. 

