# Satellite imagery analysis for land cover classification

## 1.Introduction

  By using remote monitoring  and leveraging publicly available datasets, we want to differentiate and if possible classify different types of land surfaces in order to help identify areas that are more likely to include tobacco fields.

## 2.Access satelitte imagery (sentinel2A, landsat)

  The instruction about how you can access and download the data from satellite, read on data.txt.

  1.Search and Download Sentinel 2A imagery using Sentinelsat API

    Run python sentineldownload_data.py

  2.Search and download landsat image using landsatxplore API

    Run python landsat_download.py

## 3.Data visualization the 4 bands(blue,green,red,NIR) ouf 12 and RGB true color image

    Run python visualize.py

    Run python RGB.py

## 4. Analysis of sentinel2A, Indices to make Vegetation Analysis Complete

  The use of remote sensing indices in order to obtain information for vegetation distributions, heath and patterns is a popular practice with applicability at different scales of detail.
  NDVI(Normalized Difference Vegetation Index) that are widely used to analyze vegetation but is sensitive to the effects of soil
   and atmosphere, that’s why it’s recommended to apply additional indexes for more accurate analysis of vegetation.

### 1. NDVI(Normalized Difference Vegetation Index)

  It describes the difference between visible and near-infrared reflectance of vegetation cover and can be used to estimate the density of green on an area of land and it varies from -1 to 1

    Run python NDVI.py

### 2.NDWI(Normalized Difference Water Index)

  Normalized Difference Water Index (NDWI) may refer to one of at least two remote sensing-derived indexes related to liquid water:

  One is used to monitor changes in water content of leaves, using near-infrared (NIR) and short-wave infrared (SWIR) wavelengths

  Another is used to monitor changes related to water content in water bodies, using green and NIR wavelengths

  Have a look on NDWI using NIR and Green. NDWI = ((Green – NIR) / (NIR + Green ))

    Run python NDWI.py

### 3. SAVI( Soil Adjusted Vegetation Index)

  It  was designed to minimize soil brightness influences. Its creator Huete added a soil adjustment factor L to the equation of NDVI in order to correct for soil noise effects (soil color, soil moisture, soil variability across region, etc.), which tend to impact the results. SAVI using NIR and Red, where L varies -1 to 1 whereas low green vegetation regions require L=1 otherwise L= 0 for high green vegetation. SAVI = ((NIR – Red) / (NIR + Red + L)) x (1 + L)

    Run python SAVI.py

### 4. ARVI(Atmospherically Resistant Vegetation Index)

  The Atmospherically Resistant Vegetation Index is the first vegetation index, which is notrelatively prone to atmospheric factors (such as aerosol). It  is basically NDVI corrected for atmospheric scattering effects in the red reflectance spectrum by using the measurements in blue wavelengths. ARVI = (NIR – (2 X Red) + Blue) / (NIR + (2 X Red) + Blue)

    Run python ARVI.py

### 5. EVI(Enhanced Vegetation Index )

  The Enhanced Vegetation Index was invented  to simultaneously correct NDVI results for atmospheric influences and soil background signals, especially in areas of dense canopy. The value range for EVI is -1 to 1, and for healthy vegetation it varies between 0.2 and 0.8. EVI contains coefficient C1 and C2 to correct for aerosol scattering present in the atmosphere, and L to adjust for soil and canopy background. C1=6 , C2 = 7.5, L=1. EVI = 2.5 x ((NIR – Red) / ((NIR) + (C1 x Red) – (C2 x Blue) + L))
  
    Run python EVI.py

### 6.GCI(the Green Chlorophyll Index)

  In remote sensing, the Green Chlorophyll Index is used to estimate the content of leaf chlorophyll in various species of plants. The chlorophyll content reflects the physiological state of vegetation; it decreases in stressed plants and can therefore be used as a measurement of plant health. GCI = (NIR) / (Green) – 1

    Run python GCI.py

### 7.SIPI(Structure Insensitive Pigment Index)

  The Structure Insensitive Pigment Index is good for analysis of vegetation with the variable canopy structure. It estimates the ratio of carotenoids to chlorophyll: the increased value signals of stressed vegetation. SIPI = (NIR – Blue) / (NIR – Red)

     Run python SIPI.py

## 5.Analysis of Sentinel in ptyhon with Google Earth Engine AP

  Import dataset from sentinel 2 using earth engine api and we clip our point of interest
  filter by date and sort according to cloud coverage. We now select the bands to compute the true colour map
  From the first data we selects the bands to generate the ndvi.We have to authenticate first on Google Earth Engine AP to get access
  Display on the map

    Run python sentinelGEEanalysis.py

## 6. Random forest classifier model

  Train a random forest locally using scikit-learn, to get land cover classes
  where are able to classify between vegetation, bare soil and water.
  We used the demo land cover labels dataset from google earth engine,see csv file at data folder
  We have to authenticate first on Google Earth Engine AP to get access.  
  Display on the classifiction map

    Run train.py

## Plot Normalised Difference Vegetation Index (NDVI) time series for AOI for each class of land cover

  Monthly NDVI time series that represent a complete crop phonological cycle
  NDVI method is applied according to its specialty range from –1 to +1
  We have to authenticate first on Google Earth Engine AP to get access

    Run NDVItimeseries.py
