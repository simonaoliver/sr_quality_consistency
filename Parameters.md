# 4 Applicable Parameter Thresholds {#4-applicable-parameter-thresholds}

## 4.1 Atmospheric Correction {#4.1-atmospheric-correction}

Atmospheric correction of the radiative transfer method involves simulating the relationship between the atmospheric parameters at the time of the satellite observation and the true reflectivity of the surface by simulating the radiation transmission process between the atmospheric–surface remote sensor. After determining the atmospheric parameter information, we can separate the respective contributions of gas at the ground from the radiation information obtained by the sensor and then obtain the surface reflectivity. The basic idea of atmospheric correction based on the radiation transmission model is to simulate the propagation of electromagnetic waves in the geogas system under various atmospheric parameter conditions (atmospheric AOT), atmospheric modes (related to atmospheric gas parameters), surface elevations, and satellite observation geometries (satellite zenith angle, solar zenith angle, and relative azimuth) through the radiative transfer  model. Using the results of the simulation, a lookup table of atmospheric radiation transmission parameters is constructed in conjunction with the spectral response function of the satellite sensor. (Advanced Remote Sensing (Second Edition), 2020\)

To achieve surface reflectance consistency, inputs to the radiative transfer model must reliably be within tolerance (to the true value) limits. The applicable parameters and their tolerances are specified below: 

## 4.1.1 Atmospheric parameters {#4.1.1-atmospheric-parameters}

1. **Solar Spectral Irradiance** (total solar irradiance of the integrated quantity) \- If the sensor calibration and radiometric correction is based on the same solar irradiance model as the atmospheric correction, then the atmospheric correction to bottom of atmosphere reflectance is not influenced.   
   1. The accuracy of surface reflectance estimation for radiance based satellite sensors depends on the choice of solar spectral irradiance  model used and here the CEOS recommended spectrum should be the baseline and if not used then clear information to indicate differences should be made available. If the sensor calibration and the radiometric correction is based on the same solar irradiance model (E0) as the atmospheric correction, then \- in theory \- the atmospheric correction to BOA\_reflectance retrieval is not influenced. Problems only arise when using different irradiance models.  
   2. Measure?  
   3. Tolerance?  
2. **Aerosol optical thickness** \- Aerosol optical depth (AOD) and aerosol optical thickness (AOT) are considered the same. Both are different from the Angstrom exponent which needs to be covered separately as a part of aerosol type. Aerosol information includes both aerosol optical depth and aerosol type model. Both impact the atmospheric correction.  
     
   Aerosol properties depend on the simulations. In reality one might have different proportions of different aerosols and even all of them distributed at different altitudes. The simplification of a three dimensional problem for optical EO simulations (optical sensors are not Lidar) are included in the uncertainties when compared to the reference. Its influence on atmospheric correction might not be so direct since we use the same simulated lookup tables (LUTs \- simulated aerosol) to retrieve an AOT value but use the same simulation to correct for it. Although this only applies if it is the same team producing the satellite product and performing the validation.  
     
   1. Definition \- optical thickness is the natural logarithm of the ratio of incident to transmitted radiant power through a material.  
   2. Measure – Angstrom Exponent  
   3. Tolerance – wavelength dependent?  
3. **Surface Pressure**

	\<TODO\>

4. **Surface Temperature**

\<TODO\>

5. **Water Vapor**

\<TODO\>

6. **Earth sun distance**

   \<TODO\>

7. **Ozone**

   \<TODO\>

8. **CO2**

\<TODO\>

9. **CO2**

	\<TODO\>

10. **Atmospheric model** \-  Aerosol type models include marine, coastal, rural and urban. If the Angstrom value is available, this may be used instead of the aerosol type model.   
    1. Tolerance as % deviation from reference (SI trace)  
    2. Profiles  
       1. Model atmospheres (6 available in MODTRAN)  
          1. Temperature  
          2. CO2 profile  
          3. H20 profile  
       2. 03 profile  
       3. Aerosols  
       4. Well mixed gases  
       5. Surface Type  
11. **Surface elevation** \- Resolution, RMSE and co-registration are important considerations.  
    1. Definition – Digital Surface Model   
    2. Measure \- meters  
    3. Tolerance – Resolution relative to input imagery  
       1. effective resolution of elevant model is at or better than the image pixel resolution  
       2. co-registation RMSE is \< (some function of the image resolution)   
12. **Satellite observation geometries** \- Should be well characterised as these impact on the amount of atmosphere a sensor sees and therefore the proportional representation of atmosphere in the radiative transfer model. In order to accurately retrieve consistent surface reflectance, the satellite and solar geometries must be accurately represented as input parameters to radiative transfer/BRDF/solar zenith normalisation etc.  
    1. Satellite view zenith and azimuth angles  
    2. Definition  
    3. Measure – Angle / degrees  
    4. Tolerance –eg. \<0.1 degree  
       1. Solar zenith angle  
       2. Relative azimuth  
          

## 4.1.2 Comparing Radiative Transfer Codes {#4.1.2-comparing-radiative-transfer-codes}

\<TO DO\>

6S MODTRAN and LibRadTran intercomparison \- [gmd-13-1945-2020.pdf (copernicus.org)](https://gmd.copernicus.org/articles/13/1945/2020/gmd-13-1945-2020.pdf)

ACIX- Radiative Transfer codes tend to agree well within the 1% level (except for those that do not account for polarization), as demonstrated during a previous benchmarking exercise on RT simulations \[[Remote Sensing | Free Full-Text | Atmospheric Correction Inter-Comparison Exercise (mdpi.com)\]](https://www.mdpi.com/2072-4292/10/2/352) However, for a reflectance of 0.3, a 1% uncertainty in the transmission can result in an uncertainty of 0.003 in the surface reflectance, while an uncertainty of 1% on the path radiance can also add up to 0.001.  i.e. The effects of radiation polarization in the atmosphere must not be ignored in the selected radiative transfer model [(5) (PDF) Validation of a vector version of the 6S radiative transfer code for atmospheric correction of satellite data. Part I: Path Radiance (researchgate.net)](https://www.researchgate.net/publication/6861202_Validation_of_a_vector_version_of_the_6S_radiative_transfer_code_for_atmospheric_correction_of_satellite_data_Part_I_Path_Radiance)

[(5) (PDF) Validation of a vector version of the 6S radiative transfer code for atmospheric correction of satellite data. Part II. Homogeneous Lambertian and anisotropic surfaces (researchgate.net)](https://www.researchgate.net/publication/6256939_Validation_of_a_vector_version_of_the_6S_radiative_transfer_code_for_atmospheric_correction_of_satellite_data_Part_II_Homogeneous_Lambertian_and_anisotropic_surfaces)

Accounting for radiation polarization requires the utilization of rigorous vector radiative transfer (RT)equations based on the Stokes parameters formal-ism.   
(5) (PDF) Validation of a vector version of the 6S radiative transfer code for atmospheric correction of satellite data. Part I: Path Radiance. Available from: https://www.researchgate.net/publication/6861202\_Validation\_of\_a\_vector\_version\_of\_the\_6S\_radiative\_transfer\_code\_for\_atmospheric\_correction\_of\_satellite\_data\_Part\_I\_Path\_Radiance \[accessed Nov 13 2023\].

## 4.2 BRDF correction {#4.2-brdf-correction}

## Pro:

- When compiling time series, the BRDF correction will widely improve the resulting product, as the resulting BOA product is homogeneous in a way that all angular effects are suppressed. Thus the data is ready for analysis for most applications without the need for further pre-processing and harmonisation steps.  
- This allows for the consistent integration of data coming from other missions with similar spectral and geometric properties (Landsat & S-2), and also when combining data from diverse sensors (e.g., for the NOAA AVHRR heritage data with AM / PM orbits and thus different illumination geometries), and also helping to solve some issues when  integrating red & NIR bands from high spatial resolution sensors with wide FOV sensors   
- Even when compiling time series data from a single sensor over longer time intervals, als a BRDF correction step improves the differences originating from the changing solar illumination geometry over the year

Con:

- Especially for snow\&ice applications, and also for advanced vegetation applications, the angular reflectance behavior is part of the signal used for the retrieval of thematic products (L3+). Thus including a BRDF correction within the L2A atmospheric correction processing step might render the generated product as not useful for these applications, with the need of an additional L2A product without BRDF correction.  
- Even though some missions can derive the BRDF kernels from their own time series data (e.g.,  MODIS having a wide FOV and high temporal resolution), many other missions rely on assumptions on the kernels to be used, which depends on the surface type, vegetation status (NDVI-dependent BRDF kernels). Having a wrong assumption on the surface type and thus BRDF kernel, the data products can be flawed.  

Issues reg. selection of the “reference” view & illumination geometry:

- As the normalization is relative to a chosen view and solar illumination geometry, the selection requires a careful selection of this geometry, best across missions:  
  - For view angle, nadir is commonly used and poses for missions without large off-nadir angles no problems  
  - For the solar angles, the selection is more difficult:   
    - A fixed solar illumination geometry (zenith & azimuth) with a relative high solar elevation angle is easiest to use, but this might pose unrealistic conditions for targets at high northern / southern latitudes where such solar elevation angles are rarely / never observed  
    - Selecting zones for solar elevation angles is closer to the actual conditions, but then causes the issues of having offsets between these zones, making the comparison between zones difficult  

Terrain correction & BRDF correction:

- It is worth pointing out that terrain correction and BRDF correction are interdependent, as selecting either the surface normale or the actual tilted slope as reference for the normalization

## 4.3 Terrain Illumination  {#4.3-terrain-illumination}

1. Implications of definition  
   1. Lambertian surface not appropriate  
      1. Rationale:  
      2. Therefore: Terrain Illumination must be included.  
   2. Diffuse Reflectance  
   3. Angular 

## 4.4 Parameter Tolerance Summary {#4.4-parameter-tolerance-summary}

below example only

Add some nominal ranges from the outset. 

Make a note of the general nadir case.

|  | quantity | input | measure | tolerance |
| :---- | :---- | :---- | :---- | :---- |
| θS | solar zenith angle |  |  |  |
| φS | solar azimuth angle |  |  |  |
| θV | sensor view zenith angle |  |  |  |
| φV | sensor view azimuth angle |  |  |  |
| θt | slope angle |  |  |  |
| φt | aspect angle of the slope |  |  |  |
| it | incident zenith angles between the sun directions and surface normal |  |  |  |
| φi | azimuth angle for incident direction in the slope geometry |  |  |  |
| et | exiting zenith angles between the  view directions and surface normal. |  |  |  |
| φe | azimuth angle for exiting direction in the slope geometry |  |  |  |
| tS | direct transmittance in the solar direction |  |  |  |
| tV | direct transmittance in the view direction |  |  |  |
| td(θS) | diffuse transmittance in the solar direction |  |  |  |
| td(θV) | diffuse transmittance in the view direction |  |  |  |
| S | the atmospheric albedo |  |  |  |
| TS | total transmittance in the solar direction |  |  |  |
| TV | total transmittance in the view direction |  |  |  |
| LTOA | Sensor radiance at top of atmosphere |  |  |  |
| L0 | path radiance |  |  |  |
| E0′ | Solar exoatmospheric irradiance (earth-sun distance adjusted). |  |  |  |
| ρS | the surface reflectance (the BRF or bi-directional reflectance factor which is *π* times the BRDF) |  |  |  |
| ρadj | average reflectance of adjacent objects |  |  |  |
| ρm | the atmospherically corrected Lambertian reflectance |  |  |  |
| Eh | total irradiance on a horizontal surface |  |  |  |
| Ehdir | the direct component of irradiance on a horizontal surface |  |  |  |
| Ehdif | the diffuse component of irradiance on a horizontal surface |  |  |  |
| E | total irradiance on an inclined surface |  |  |  |
| Edir | direct component of irradiance on an inclined surface |  |  |  |
| Edif | diffuse component of irradiance on an inclined surface |  |  |  |

# 5 CEOS-ARD {#5-ceos-ard}

## 5.1 Threshold and Target Requirements from CEOS-ARD Product Family Specification {#5.1-threshold-and-target-requirements-from-ceos-ard-product-family-specification}

* 1.12 \- Radiometric Accuracy \- “The metadata includes metrics describing the assessed absolute radiometric uncertainty of the version of the data or product, expressed as absolute radiometric uncertainty relative to appropriate, known reference sites and standards (for example, pseudo-invariant calibration sites, rigorously collected field spectra, PICS, Rayleigh, DCC, etc.)”  
* 2.13 \- Aerosol Optical Depth Parameters \- “To be determined.”  
* 3.1 \- Measurement – “Surface Reflectance measurements are SI traceable.”  
* 3.3  \- Measurement Normalisation  \- “Measurements are normalised for solar and viewing conditions (i.e., nadir view angle and average solar angles). This may include terrain illumination and/or Bi-Directional Reflectance Function (BRDF) correction.”  
* 3.4 \- Directional Atmospheric Scattering \- “Corrections are applied for aerosols and molecular (Rayleigh) scattering.”  
* 3.5 \- Water Vapour Corrections \- “Corrections are applied for water vapor.”  
* 3.6 \- Measurement Normalisation \- “Data is corrected for ozone”
