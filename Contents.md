# Quality and consistency of land surface reflectance in the solar reflective region

# 

Revision History

| Date | Version | Sections affected | Changes |
| ----- | ----- | ----- | ----- |
| 2023-xx-xx | 0.1(draft) | All | Draft release for internal review |
| 2024-12-17 | 0.2(draft) | All | Review and address comments \- clean copy |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

[**Background	2**](/Background.md)

[**1 Introduction	3**](#Introduction)

[1.1 Purpose	3](#1.1-purpose)

[1.2 Contributors	4](#1.2-contributors)

[**1.3 Definition : Consistency for two surface reflectance measurements	4**](#1.3-definition-:-consistency-for-two-surface-reflectance-measurements)

[1.4 Scope	4](#1.4-scope)

[**2 Steps/corrections needed to achieve consistency	5**](#2-steps/corrections-needed-to-achieve-consistency)

[2.1 General Steps	5](#2.1-general-steps)

[2.2 Harmonisation Steps	6](#2.2-harmonisation-steps)

[2.3 Homogenisation Steps	7](#2.3-homogenisation-steps)

[2.4 Validation Steps	7](#2.4-validation-steps)

[**3 Surface Reflectance Measurand	7**](#3-surface-reflectance-measurand)

[3.1 Foundations of measurand terminology	8](#3.1-foundations-of-measurand-terminology)

[3.3 Issues in application of terminology to  an explicit definition	11](#3.3-issues-in-application-of-terminology-to-an-explicit-definition)

[**4 Applicable Parameter Thresholds	12**](#4-applicable-parameter-thresholds)

[4.1 Atmospheric Correction	12](#4.1-atmospheric-correction)

[4.1.1 Atmospheric parameters	12](#4.1.1-atmospheric-parameters)

[4.1.2 Comparability of Radiative Transfer Codes	14](#4.1.2-comparing-radiative-transfer-codes)

[4.2 BRDF correction	14](#4.2-brdf-correction)

[4.3 Terrain Illumination	16](#4.3-terrain-illumination)

[4.4 Parameter Tolerance Summary	16](#4.4-parameter-tolerance-summary)

[**5 CEOS-ARD	17**](#5-ceos-ard)

[5.1 Threshold and Target Requirements from CEOS-ARD Product Family Specification	17](#5.1-threshold-and-target-requirements-from-ceos-ard-product-family-specification)

[**6 Discussion	17**](#6-discussion)

[**7 References	17**](#7-references)

[**9 Glossary of Terms	19**](#9-glossary-of-terms)

[**10 Appendix	21**](#10-appendix)

[10.1 SI Traceability notes	21](#10.1-si-traceability-notes)

# Background {#background}

The CEOS-ARD Surface Reflectance Product Family Specification (PFS)  provides a strong basis for interoperability. The CEOS-ARD Surface Reflectance Product Family Specification includes:

* General metadata requirements ensure traceability, machine readability, and accurate data collection times.  
* Per-pixel metadata addresses flags for no data, saturation, cloud presence, and other critical indicators.  
* Radiometric and atmospheric corrections focus on providing valid surface reflectance measurements and associated uncertainties.

Geometric corrections emphasize achieving sub-pixel accuracy for consistent geolocation across time.   However its non-prescriptive nature tolerates different approaches to the derivation of the ARD Surface Reflectance .

Every dataset producer has their own constraints, priorities and approaches when it comes to defining a Surface Reflectance processing chain, however studies (Claverie et al 2016 ,Main-Knorn et al. 2017 and Saunier et al. 2022\) have shown that using equivalent processing steps and model inputs results in surface reflectance products that are more consistent and able to be used for multi-provider analyses of various indices (Samain et al. 2006). Consistent Surface Reflectance measurements are crucial to optimizing results from multi-provider data integration and analysis.

Inconsistency in surface reflectance quantities and their impact on analyses are well documented (Claverie et al 2016, De Keukelaere et al 2018\)  and have also been expressed anecdotally by industry contacts, who have noted the need to independently reprocess data  to address  incompatibility of surface reflectance datasets for multi-sensor analyses from CEOS Agencies. This is something that CEOS should seek to resolve in service of its stated mission to promote the exchange of data. CEOS Agencies’ own efforts in producing NASA HLS (Claverie et al 2018\) and ESA Sen2Like (Saunier et al 2022\) demonstrate the need to improve the compatibility of measurements across providers to enable homogenisation and fusion.

# 1 Introduction  {#1-introduction}

## 1.1 Purpose  {#1.1-purpose}

This work seeks to describe a surface reflectance (Passive Satellite Viewed Bottom of Atmosphere Surface Reflectance) measurand (quantity), applicable steps, model parameters and their tolerance, required to achieve \-comparability between like bands from different sensors. The intent of this work is not to dictate a common process or toolset for the generation of consistent surface reflectance quantities. 

This paper serves as a reference for organizations considering reprocessing of Earth observation Collections of moderate resolution (1 m \- 100 m) passive optical satellite data collections (300-2500 nm) who are aiming to contribute to a virtual constellation of interoperable surface reflectance measurements.  It can also guide the processing of ARD products for higher-resolution passive optical data sets if they have comparable spectral and radiometric properties of reference moderate-resolution systems. This document emphasizes the reference missions from NASA and ESA, which have GSDs 10 m or coarser. However, a well-designed high-resolution system with the proper specifications (radiometric and spectral) should produce good surface reflectance data. 

Surface reflectance consistency provides for measurement level interoperability of  surface reflectance data products from multiple data providers for similar classes of sensor. If consistency is achieved, surface reflectance data products from multiple sensors, can be used together harmoniously in applications requiring a dense time-series of observations and enable meaningful interpretation of results. This work aims to uplift CEOS-ARD with a core focus on enabling consistent surface reflectance time-series from different sources. The authors recognize that not all applications of surface reflectance require the step indicated in the document, and its aim is to serve a general, rather than specialised use case where the proposed corrections obscure the phenomena under investigation.

## 1.2 Contributors {#1.2-contributors}

| Eric Vermote | NASA | eric.f.vermote@nasa.gov |
| :---- | :---- | :---- |
| Martin Bachmann | DLR | martin.bachmann@dlr.de |
| Peter Strobl | EC | Peter.STROBL@ec.europa.eu |
| Robert (Bob) Ryan | I2R | rryan@i2rcorp.com |
| Mary Pagnutti | I2R | mpagnutti@i2rcorp.com |
| Raquel delos Reyes | DLR | Raquel.delosReyes@dlr.de |
| Simon Oliver | GA | Simon.Oliver@ga.gov.au |
| Medhavy Thankappan | GA | medhavy.thankappan@ga.gov.au |
| Dani Schläpfer | ReSe | daniel@rese.ch |
| Rudolf Richter | DLR | Rudolf.Richter@dlr.de |
| Fuqin Li | GA | Fuqin.Li@ga.gov.au |
| David Jupp | CSIRO | David.Jupp@csiro.au |
| Cody Anderson | USGS | chanderson@usgs.gov |
| Sebastien Saunier | Telespazio | sebastien.saunier@telespazio.com |
| Ake Rosenqvist | JAXA | ake.rosenqvist@soloeo.com |
| Steve Covington | USGS | sjcovington@contractor.usgs.gov |
| Sabrina Pinori | Serco | sabrina.pinori@serco.com |
| Danika Wellington | USGS | dwellington@usgs.gov |
| Matthew Steventon | Symbios | matthew@symbios.space |
| Harvey Jones | Symbios | harvey@symbios.space |
| Nigel Fox | NPL | nigel.fox@npl.co.uk |

*Table 1\. Contributors to this manuscript*

## 1.3 Definition : Consistency for two surface reflectance measurements {#1.3-definition-:-consistency-for-two-surface-reflectance-measurements}

Surface reflectance measurements from different (satellite)s or sensors can be considered consistent when, for an invariant target and within a predefined range of conditions, they produce comparable results which match within their measurement uncertainties for the same target under predefined conditions.

## 1.4 Scope {#1.4-scope}

Inclusions

This work addresses sun induced Land Surface Reflectance measurement consistency from two or more satellite sensors within the following range of conditions: 

* Ground Sampling Distance (GSDs) and Instantaneous Field of View (IFOVs) of \~1 to 1000 m  
  * This GSD range is an order of magnitude estimate and somewhat arbitrary given target dependency (surface properties etc.). The exact limits are yet to be confirmed.  
* Wavelength between Ultraviolet to short wave infrared 300-2500 nm (Solar reflective region)  
* Solar elevation angles above approximately 15 degrees  
  * Landsat limits the solar elevation to \~15 degrees since it becomes harder to perform the atmospheric correction. One way to handle this is possibly in uncertainty if we can understand it well enough to quantify it. Low solar elevation angle data is important in the polar regions.  
* (off nadir) Observation angles above approx. 45(?) degrees?  
* outside of topographic or cloud (cast) shadows  
* target reflectance and atmospheric transmission sufficient to achieve an at-sensor radiance exceeding the NER to a level commensurate with required uncertainty.  Signal to Noise considerations – illumination and or sensor sensitivity considerations?

# 2 Steps/corrections needed to achieve consistency {#2-steps/corrections-needed-to-achieve-consistency}

## 2.1 General Steps {#2.1-general-steps}

To achieve consistency in satellite-derived surface reflectance measurements, several steps and corrections are needed:

1. **Radiometric calibration**: Ensure the satellite sensors' raw digital numbers (DNs) are accurately converted to physical units of top-of-atmosphere (TOA) radiance or reflectance. This includes development of processing dedicated to relative and absolute calibration (e.g., solar diffuser,  dark frame, flat fielding, linearity, conversion to SI units) with an appropriate assessment of uncertainty. Some missions are using vicarious calibration in order to estimate calibration parameters which are subsequently used as parameters in the radiometric processing.  
2. **Atmospheric correction**: Remove the effects of atmospheric scattering and absorption to estimate bottom-of-atmosphere (BOA) surface reflectance. In this case, we define satellite-derived surface reflectance as measured under natural solar illumination composed of direct and diffuse radiation. Surface reflectance is estimated using a radiative transfer method or empirical line method using TOA radiance or reflectance data \[6, 7\]. Atmospheric correction consists of:  
   1. Aerosol and atmospheric parameter retrieval: Accurately estimate atmospheric properties like aerosol optical thickness (AOT) and water vapor content. Regardless of the source of these parameters (eg. retrieved from auxiliary data (ECMWF) or estimated on a scene basis), it is crucial that these atmospheric properties possess the necessary spatial and temporal characteristics to ensure accurate atmospheric correction.   
   2. Cloud and cloud shadow masking: Implement robust (peer reviewed)  algorithms to detect and mask out clouds and their shadows.  
   3. Haze correction (optional)  
   4. Adjacency correction: Apply correction for adjacency where non-homogeneous surface effects are significant (optional).   
   5. Topographic slope correction: Apply correction for terrain effects, especially in areas with significant relief \[8\].  
3. **Surface Reflectance Validation against reference**: Compare satellite-derived surface reflectance with in-situ measurements or reference data to assess the accuracy. Comparisons should be made over various land covers and atmospheric and sun-sensor-view geometric conditions and care should be taken to ensure that the definition of SR used for the validation is consistent with that used for the satellite product. The accuracy evaluation will determine the need for adjustments. The significance of the differences will require an uncertainty in the in-situ measurements (or reference data) lower than the surface reflectance requirement we intend to validate. From ACIX exercises over land, an uncertainty lower than 5% relative to the reference SR.  
4. **Consistency checks**: Since different radiative transfer models and methods are used, compare results obtained using different atmospheric correction algorithms to ensure consistency. Inter-comparison exercises, that include the uncertainty of both sensors, should be performed throughout the life of a sensor under varying atmospheric conditions, land covers and processing updates. A subset of these intercomparisons should evaluate adjacency, BRDF and terrain effects.   
5. **Traceability to SI units**: Ensure derived surface reflectance values are traceable to the International System of Units for comparability across different sensors and platforms. An initial set of measurements to characterise the instruments characteristics impacting the observation e.g. stray light, linearity etc as well as radiometric gain,  should be made in a laboratory traceable to SI standards prior to launch. Post-launch steps should be made to assess and/or correct the sensor characteristics using on-board facilities if available and/or any associated comparison/vicarious calibration of its Level 1 product using appropriate CEOS recommended methods.  Following this to validate performance and assess consistency/evidence of traceability after launch, a subset of in-situ measurements (described in Step 3\) must be made with SI traceable instrumentation.

## 2.2 Harmonisation Steps  {#2.2-harmonisation-steps}

A harmonised satellite series is one where all the calibrations of the sensors have been done consistently relative to reference datasets which can be traced back to known reference sources, with evidence of associated uncertainty, in an ideal case back to SI. Each sensor is calibrated to the reference in a way that maintains the characteristics of that individual sensor such that the calibrated radiances represent the unique nature of each sensor. This means that two sensors which have been harmonised may see different signals when looking at the same location at the same time, the difference being related to known differences in the responses of each sensor such as differences in the sensor’s spectral response functions etc.(Fiduceo, 2024\). However, after accounting for any differences, the resultant  spectral radiance values will be consistent.   

To generate consistent interoperable data sets from different sensors, in addition to radiometric calibration and atmospheric correction, the following steps are needed.

6. **Geometric correction:** Ensure precise geolocation knowledge and if appropriate re-grid  (e.g., ortho-rectification, however if applied the resultant impact on radiometric uncertainty needs to be reported or assessed) and co-register images from different sensors or acquisition times. Align product pixel grids using similar raster/DEM reference..  
7. **BRDF correction:** Apply bidirectional reflectance distribution function (BRDF) corrections to account for variations in viewing and illumination geometry. A standard reporting geometry (adjusted to nadir view)  for the solar and viewing geometries needs to be defined or the potential variance accounted for and reported in the uncertainties (eg. as per Claverie et al. 2018).

The following additional homogenisation steps assume a reference dataset, and are therefore not considered applicable to the generation of consistent measures across multiple sensors  within this guidance.

## 2.3 Homogenisation Steps {#2.3-homogenisation-steps}

Unlike harmonisation, homogenisation is where all satellites are forced to look the same such that when looking at the same location simultaneously they would (in theory) give the same signal within uncertainties. In reality the signals from different sensors would be different and homogenisation is adding in corrective terms to each or one satellite to make them look the same and generally requires one sensor to be defined as the reference to which others are corrected to give similar values. It is likely that these corrective terms will not be 100% effective and that the process of homogenisation will add in scene dependent errors to the uncertainty budget which may be difficult to assess (Fiduceo, 2024). 

8. **Spectral band adjustment:** Account for differences in spectral response functions between sensors (if possible) for various landcovers by applying appropriate corrections or band-pass adjustments. The adjustment is often estimated with simulation as it depends on the land cover class. This auxiliary information should be available, and computed, or retrieved from a trusted external source (CLC),  in the harmonisation process.  
9. **Spatial resolution harmonisation:** Account for GSD and spatial resolution differences (e.g. point spread function) if a spatially homogeneous data set is desired. This process may also occur prior to the ortho-rectification process.  
10. **Polarization harmonisation correction (optional):** Account for sensor and scene polarization effects. 

## 2.4 Validation Steps {#2.4-validation-steps}

11. **Surface Reflectance Harmonisation Validation:** When multiple acquisitions from different sensors are possible over the same site at nearly the same time, comparisons between harmonised surface reflectance products should be made.  Such comparisons should also be made even when non-simultaneous but of course after applying the appropriate corrections associated with atmospheric conditions, view/illumination angles etc.  
    

By applying these steps and corrections, researchers can work towards achieving consistency between surface reflectance measurements from different satellite sensors, enabling more reliable multi-sensor and long-term Earth observation studies.

# 3 Surface Reflectance Measurand {#3-surface-reflectance-measurand}

This work strives to describe an idealised measurand in sufficient detail that it infers the set of necessary algorithmic components required to produce consistent and harmonised surface reflectance data (assuming input parameters and models are within some yet to be determined uncertainty), which is suitable for homogenisation and facilitates time-series analyses through additional steps (eg. band-pass adjustment). Efforts to describe the measurand have so far revolved around the Bidirectional Reflectance Factor (BRF) (as per the standard terminologies described as theoretical quantities in Nicodemus et al. 1977, and corresponding measurable quantities in Schaepman-Strub et al 2006).

## 3.1 Foundations of measurand terminology {#3.1-foundations-of-measurand-terminology}

Surface reflectance is the fraction of incoming solar radiation reflected from the Earth's surface to the satellite sensor. 

Descriptions of surface reflectance measures are often confused and even the often cited main literature is not consistent about the definitions. We try to rely our definitions on the original paper by Nicodemus 1977 who compiled the relevant physical quantities systematically. G. Schaepman-Strub tried to adapt the physical definitions for the remote sensing case which resulted in some ambiguities. The below from the ATCOR website (Definitions \- ATCOR) is used to clarify:

**1\. BRF or BRDF:** BRF is defined as a reflectance factor, i.e. the factor obtained if comparing what is observed in a true bidirectional measurement if compared to a perfect 100% lambertian target. BRDF is a true reflectance (distribution function) which is defined as the relation between reflected radiation to the incoming radiation at one angular configuration. The latter is the base quantity we use for modeling what's happening on the ground and is also the base quantity of atmospheric correction codes as we calculate/simulate the irradiance term to relate it with the measurement for getting a reflectance (there shouldn't be any white panels involved in physical atmospheric correction).

**2\. Directional vs. conical:** In theory, it holds true that there are (almost) no directional measurements, but for practical reasons, the small IFOV of the satellite is close to a infinitesimal angle of a directional measurement and in models it can be treated as such (i.e. conical variations are not considered). Therefore, using the 'D' for measurements seems to be appropriate as this has clearly to be distinguished from the field measurement situation where truly conical instruments are used for spectral data acquisition (i.e. what leads to 'C' type of quantities). It could be questioned if directionality can be achieved in practice. To explain further, a target illuminated by a collimated beam (i.e. parallel, directional) and measured with a device which also collects parallel beams in parallel by a lens and focuses on a detector, may be considered a true bi-directional measurement.

**3\. HDRF:** The term 'HDRF' is used by Nicodemus for a perfectly hemispheric diffusely illuminated target, and a directional observation. As such, the directional influence of the incident BRDF is to be corrected to get to a true HRDF. This is very hard to achieve and instead, semi-empirical models such as the modified Minnaert approach (Minnaert 1941\) to approximate a HDRF after atmospheric and terrain correction in ATCOR (ATCOR 2024). Schaepman-Strub used the term differently than Nicodemus: the illumination of their 'HDRF' can be arbitrarily distributed due to the sun position and the atmospheric state (what leads to confusion in literature). Such a quantity is not a consistent surface characteristic; in the ATCOR we call that quantity a 'bottom of atmosphere reflectance' without referring to the physical definitions to avoid a misconception.

**4\. BRDF \-Correction:** The most consistent quantity you can get after data processing is the BHR (bihemispherical reflectance), sometimes also called the spectral albedo as it is the relation between the hemispherically integrated reflected radiation to a perfectly diffuse irradiance \- and it has no angular dependencies. The BHR can be modeled by integrating the true HDRF over the hemisphere under the use of a BRDF model. Nadir normalization is not consistent, as the nadir reflectance depends on the position of the sun and hinders comparability. So, the goal of a complete atmospheric correction for best comparability between data products is to derive BHR values for each pixel \- that's what we try to achieve in our BREFCOR (ATCOR 2024\) model.

The result of first order atmospheric correction is best named 'bottom of atmosphere reflectance' and has lots of directional dependencies; if incidence BRDF is considered in topographic correction (ie. using the local solar incidence angle and diffuse irradiance models), the result is close to a true 'HDRF'. If observer BRDF correction was done, the result would be a BHR \- and only a BHR is well comparable amongst observation situations.

The most common remote sensing surface reflectance measurement is a hemispherical-conical measurement where the surface is illuminated from the entire hemisphere and the observation is measured over a conical solid angle (Schaepman-Strub et al 2006). 

From Schaepman-Strub et al. (2006), the idealised surface reflectance equivalence measure may be termed BRF – Directional incident and Directional excitant light and not hemispherical, nor conical in either direction. The rationale being that BRF is the base non quantifiable / non-measurable base from which all variants are derived. BRF represents a dimensionless reflectance for ‘directional’ source and ‘directional’ view. So, it is ‘bi-directional’ or DD. It is different from BRDF. BRF is the basic quantity from which others (like HDRF) are derived or defined. As Schaepman-Strub et al. 2006 highlights, BRF is not realisable. Instruments measure or emit in a solid angle. Types of solid angle are given codes like H and C. For example, hemispherical (H) view is a 2 pi steradians field of view.

* H is for hemispherical  
* C is for conical  
* D is for direct (not a solid angle)  
* RF is reflectance factor

Using H or C indicates that the BRF is integrated over a hemisphere or cone. The first code is ‘source’ and the second ‘view’ as in Schaepman-Straub et al. (2006).

* DDRF is bidirectional RF and is the same as BRF;  
* DHRF is for when BRF source is direct and view is integrated over a hemisphere;  
* HDRF is for direct view and BRF source is integrated over a hemisphere;  
* HHRF is for BRF integrated over both hemisphere source (eg sky radiation) and hemisphere view. HHRF is the same as BHRF or Bi-hemispherical reflectance factor.

Therefore, BRF is the basic entity to define or model. For example, in NBAR, four of the RFs above (DDRF, DHRF, HDRF, HHRF) are used in its radiative transfer equation (Li et al, 2010, equation 1). If the BRF is reciprocal, DHRF=HDRF for the same D angle.

*Figure1. Contributing components (theoretical after Nicodemus 1977\) to Bidirectional Reflectance Factor (BRF) applicable to the Li et al 2010 approach.*

3.2 Application of terminology practice

In practice and in the field, the direct radiation from the sun is usually approximated as direct (D) with very small cone (sun disk) and a radiometer with narrow field of view (eg 5 degrees) is considered as a direct (D) measurement and calibrated to a (D) radiance, although in practise many perform in-situ SR measurements by comparison to a nominally lambertian reflectance standard where the laboratory calibration of the ‘reflectance’ is the link to SI.  Note: It is in this laboratory calibration of the reflectance and its associated definition that many sources of error can occur. But some other space instruments can have (eg) CCRF etc.

The definition of BRF is chosen over others as the others follow from it by integration over solid angles such as hemispheres, cones etc.

BRF (DDRF), HDRF, DHRF and HHRF can be explained using the equation (1) in Li et al (2010) BRDF paper  

![][image1]

![][image2]is DDRF (BRF),  ![][image3]is HDRF, ![][image4] is DHRF and ![][image5] is HHDF. Geoscience Australia’s Nadir BRDF Adjusted Reflectance(NBAR) with Terrain Illumination Correction (-T) product represents DDRF (BRF)

| BRFs in the GA model (theoretical as in Nicodemus) XY X \= source FOV Y \= sensor FOV | Nicodemus 1977 Theoretical Uniform Sky Distributions *(never occurs in nature)* | Schaepman-Strub 2006 Describing  measurement in the real world | Measurable? \- as indicated by Schaepman-Strub | Validation |
| :---- | :---- | :---- | :---- | :---- |
| DD (weighted) | BRF  *Bi-directional Reflectance Factor*   *The current standard product from Geoscience Australia is nadir BRF at standard sun angle* | CC Biconical (CASE5) | Not **separately** measurable | ASD (type) measurements at the ground or low (hovering) drone equate fairly well with Lambertian reflectance in an image at the same time. In terms of BRDF model used in atmospheric correction:   ASD \~ fs x BRF \+ (1-fs) x BSA’ (0)   Fs is the fraction of direct solar radiation. BSA’ is reciprocal BSA at view angle (assumed nadir view). So this is a combination of a DD and a HD and 2 of the four quantities in combination. |
| HD (weighted) \~Narrow FOV ASD | BSA’  *Reciprocal Black Sky Albedo* | HC Hemispherical-Conical (CASE8) | Not **separately** measurable |  |
| DH | BSA *Black Sky Albedo* | CH Conical-Hemispherical (CASE6) | Not **separately** measurable | Albedo is measured at stations. The MODIS spectral albedo product can be expressed as :   Albedo= fs x BSA \+ (1-fs) x WSA   BSA is for the current sun zenith angle and WSA is as previously defined   There is no way to specifically ‘validate’ WSA separately |
| HH Sky radiation \+ total upwelling | WSA *White Sky Albedo* | HH or BHF Bi-Hemispherical (CASE9) | Not **separately** measurable |  |

*Table 2\. BRFs used in Geoscience Australia’s Nadir BRDF Adjusted Reflectance product demonstrating the theoretical and real world measurements and validation approaches.*

## 3.3 Solar Zenith Normalisation

For natural surfaces, the Lambertian equivalent reflectance (such as provided by USGS Landsat atmospherically corrected product) depends on sun angle and changes over time, even if the land cover does not. It is not an intrinsic reflectance or a suitable measurand and needs an additional step.  

Natural (especially land) surfaces have BRDF. As a result, the ‘Lambertian equivalent reflectance’ (![][image6] ) estimate of surface reflectance changes from scene to scene as the sun, view and relative azimuths of sun and view as well as fraction of diffuse radiation change. A time series of this reflectance estimate has variations even if there is no change in the land cover and even if the scenes are atmospherically corrected by physical methods. Atmospheric correction certainly removes sun and view angle effects from the atmosphere – but not those due to surface BRDF. A suitable ‘intrinsic’ measurand should therefore be based on BRDF. ‘BRDF’ here means a property of the surface. When it is represented by a specific reflectance factor, it will be called BRF. 

In the past, in order to estimate BRF models, it was assumed (eg in MODIS processing) that the Lambertian equivalent reflectance is the BRF at the current sun and view angles or![][image7]. This provided a method for estimating BRF and changing sun and view angles to standard values as was done in the MODIS NBAR product. Unfortunately, this equation is not correct if there is diffuse radiation. So, BRF and atmospheric scattering interact, and a modified model is needed to account for it. Various methods can be used to remove diffuse effects and measurands can then be defined in terms of this BRF. One proposed measurand has been![][image8] . This is BRF from nadir (zero zenith) view with a standard sun angle. It is the ‘normalised angles’ measurand. If the standard sun angle is the same over a time series, then (in theory) this measurand will not change if the surface (ie its BRDF) does not change. However, underlying this is the requirement to have a ‘suitable’ BRF model for the location and time of the area being processed. This is a big issue. 

BRDF models have been used to standardise view angles for many years. MODIS and VIIRS NBAR products are recent examples. But the standardisation of sun angle seems more controversial. However, by using view zenith of zero in the ‘normalised angles’ measurand above, you do not actually ‘change the view angle’. You only locally scale the data to a level that it would have at the different view angle. The same is true of the sun angle. But if preferred, alternative measurands that do not ‘change angles’ are (in terms of the MODIS kernel models) the fiso or the white sky albedo (WSA). fiso has been used previously to estimate NDVI free of view angle variations and spurious time effects. Perhaps there are also other choices. 

We believe that the critical underlying need for the work on BRDF to become routinely applicable is to establish agreed sources for ‘suitable’ BRF. In particular for Landsat and Sentinel-2. Landsat and Sentinel-2 cannot generate BRF models – so the models must be sourced elsewhere. The discussion of normalisation and measurands is important but it is equally important is to establish the suitable sources of BRF. We think it could have more attention at the CEOS meetings. 

## 3.3 Issues in application of terminology to  an explicit definition {#3.3-issues-in-application-of-terminology-to-an-explicit-definition}

Table 2 represents a mapping of the Li et al. 2010 method to the theoretical Nicodemis (1977) and real-world  Shaepman-Strub (2006) nomenclature. In itself, this mapping fails to address potential ambiguity relating to application of normalizing functions that are available in current products. An example of this lies in the solar zenith corrections which may normalise to a solar noon (eg. MODIS), 45 degrees (Li et al. 2010\) or be variable with latitude (Claverie et al. 2018). Further work is required to tighten the description of the idealised surface reflectance quantity \<TODO\>

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

# 6 Discussion {#6-discussion}

\< TODO \>

# 7 References {#7-references}

1. ATCOR. 2024\. Definitions – ATCOR. https://atcor.com/definitions/

2. Claverie, M., Ju, J., Masek, J.G., Dungan, J.L., Vermote, E.F., Roger, J.C., Skakun, S.V. and Justice, C., 2018\. The harmonised Landsat and Sentinel-2 surface reflectance data set. *Remote Sensing of Environment*, 219, pp.145-161.

3. De Keukelaere, L., Sterckx, S., Adriaensen, S., Knaeps, E., Reusen, I., Giardino, C., ... & Vaiciute, D. (2018). Atmospheric correction of Landsat-8/OLI and Sentinel-2/MSI data using iCOR algorithm: validation for coastal and inland waters. European Journal of Remote Sensing, 51(1), 525-542.

4. ESA, 2024\. FRM4VEG – Fiducial Reference Measurements for Vegetation. \[online\] Available at: [https://frm4veg.org/](https://frm4veg.org/) \[Accessed 9 July 2024\].

5. Fiduceo, 2024\. Glossary. \[online\] Available at: [https://www.reading.ac.uk/fiduceo](https://www.reading.ac.uk/fiduceo) \[Accessed 9 July 2024\].

6. IES, 2024\. Hemispherical-conical reflectance. \[online\] Available at: [https://www.ies.org/definitions/hemispherical-conical-reflectance/](https://www.ies.org/definitions/hemispherical-conical-reflectance/) \[Accessed 9 July 2024\].

7. Li, F., Jupp, D.L.B., Reddy, S., Lymburner, L., Mueller, N., Tan, P. and Islam, A., 2010\. An Evaluation of the Use of Atmospheric and BRDF Correction to Standardize Landsat Data. *IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing*, 3, pp.257-270.

8. Li, F., Jupp, D.L.B., Thankappan, M., Lymburner, L., Mueller, N., Lewis, A. and Held, A., 2012\. A Physics-based Atmospheric and BRDF Correction for Landsat Data over Mountainous Terrain. *Remote Sensing of Environment*, 124, pp.756-770. doi:10.1016/j.rse.2012.06.018.

9. Li, F., Jupp, D.L.B. and Thankappan, M., 2015\. Issues in the application of Digital Surface Model data to correct the terrain illumination effects in Landsat images. *International Journal of Digital Earth*, 8, pp.235-257.

10. Main-Knorn, M., Pflug, B., Louis, J., Debaecker, V., Müller-Wilm, U. and Gascon, F., 2017\. Sen2Cor for sentinel-2. In *Image and Signal Processing for Remote Sensing XXIII*, Vol. 10427, pp.37-48. SPIE.

11. Martonchik, J.V., Bruegge, C.J. and Strahler, A.H., 2000\. A review of reflectance nomenclature used in remote sensing. *Remote Sensing Reviews*, 19(1-4), pp.9-20.

12. Minnaert, M. "The Reciprocity Principle in Lunar Photometry", Astrophysical Journal, Vol. 93, 1941\.

13. Nicodemus, F.E., Richmond, J.C., Hsia, J.J., Ginsberg, I.W. and Limperis, T., 1977\. Geometrical considerations and nomenclature for reflectance. *US Department of Commerce, National Bureau of Standards*, Vol. 160\.

14. Samain, O., Geiger, B. and Roujean, J.L., 2006\. Spectral Normalization and Fusion of Optical Sensors for the Retrieval of BRDF and Albedo: Application to VEGETATION, MODIS, and MERIS Data Sets. *IEEE Transactions on Geoscience and Remote Sensing*, 44(11-1), pp.3166-3179.

15. Sandmeier, S. and Itten, K.I., 1997\. A Physically-Based Model to Correct Atmospheric and Illumination Effects in Optical Satellite Data of Rugged Terrain. *IEEE Transactions on Geoscience and Remote Sensing*, 35(3), pp.708-717. https://doi.org/10.1109/36.581991.

16. Saunier, S., Pflug, B., Lobos, I.M., Franch, B., Louis, J., De Los Reyes, R., Debaecker, V., Cadau, E.G., Boccia, V., Gascon, F. and Kocaman, S., 2022\. Sen2Like: Paving the way towards harmonization and fusion of optical data. *Remote Sensing*, 14(16), p.3855.

17. Schaepman-Strub, G., Schaepman, M.E., Painter, T.H., Dangel, S. and Martonchik, J.V., 2006\. Reflectance quantities in optical remote sensing—Definitions and case studies. *Remote Sensing of Environment*, 103(1), pp.27-42.

18. Vermote, E., Justice, C., Claverie, M. and Franch, B., 2016\. Preliminary Analysis of the Performance of the Landsat 8/OLI Land Surface Reflectance Product. *Remote Sensing of Environment*, 185, pp.46-56.

# 9 Glossary of Terms {#9-glossary-of-terms}

| Term | Definition | Source |
| :---- | :---- | :---- |
| Consistency (surface reflectance) | Two or more quantities are consistent if they are equal in magnitude, or within a certain range of a reference value that is deemed to be the true value of the measure that the quantities represent, or each of the quantities can be converted into one another through a consistent process. When two or more surface reflectance quantities over the same target area derived from observations made by different sensors, are equal in magnitude or within a certain range of the true surface reflectance over the same target area (the reference surface reflectance or known standard). | CEOS SR Equivalence, Quality and Consistency discussion group  |
| Homogeniszation | Unlike harmonisation, homogenisation is where all satellites are forced to look the same such that when looking at the same location at the same time they would (in theory) give the same signal. In reality the signals from different sensors would be different and homogenisation is adding in corrective terms to each satellite to make them look the same. It is likely that these corrective terms will not be 100% effective and that the process of homogenisation will add in scene dependent errors to the uncertainty budget which may be difficult to assess. | [Glossary \- Fiduceo (reading.ac.uk)](https://research.reading.ac.uk/fiduceo/glossary/) |
| Harmoniszation | A harmonised satellite series is one where all the calibrations of the sensors have been done consistently relative to reference datasets which can be traced back to known reference sources, in an ideal case back to SI. Each sensor is calibrated to the reference in a way that maintains the characteristics of that individual sensor such that the calibration radiances represent the unique nature of each sensor. This means that two sensors which have been harmonised may see different signals when looking at the same location at the same time, the difference being related to known differences in the responses of each sensor such as differences in the sensors spectral response functions etc. | [Glossary \- Fiduceo (reading.ac.uk)](https://research.reading.ac.uk/fiduceo/glossary/) |
| Collection | The ensemble of some products or auxiliary data  having a common focus or theme or purpose (e.g.  collection of land photos) | [https://ceos.org/document\_management/Working\_Groups/WGISS/Interest\_Groups/Data\_Stewardship/White\_Papers/EO-DataStewardshipGlossary.pdf](https://ceos.org/document_management/Working_Groups/WGISS/Interest_Groups/Data_Stewardship/White_Papers/EO-DataStewardshipGlossary.pdf)  |
| Like bands | Spectral bands (from different sensors) with similar characteristics (FWHM, band center wavelength) | This document |
| Uncertainty(of measurement) | Parameter, associated with the result of a measurement, that characterizes the dispersion of the values that  could reasonably be attributed to the measurand | [Guide to the expression of uncertainty in measurement \- JCGM 100:2008 (GUM 1995 with minor corrections \- Evaluation of measurement data](https://www.bipm.org/documents/20126/2071204/JCGM_100_2008_E.pdf/cb0ef43f-baa5-11cf-3f85-4dcd86f77bd6) |
| Radiometric normalization | Radiometric normalisation is a process which attempts to remove some of the variance seen in EO data to create values that are independent of view angle or atmospheric state or observing time etc. to give a uniform measure of a given variable across an image. It can be considered as a method to give what would have been observed by the same instrument under viewing identical conditions. | [Glossary \- Fiduceo (reading.ac.uk)](https://research.reading.ac.uk/fiduceo/glossary/) |
| Surface Reflectance |  |  |
| Consistency |  |  |
| Coherence |  |  |
| Continuity |  |  |
| Compatibility |  |  |
| Comparability  |  |  |
| Complementarity |  |  |
| Conformity  |  |  |
| Congruence  |  |  |
| Compliance |  |  |
| Correspondence |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

# 10 Appendix {#10-appendix}

## 10.1 SI Traceability notes {#10.1-si-traceability-notes}

- [SI traceability is the property of a measurement result that can be related to the International System of Units (SI) through an unbroken chain of comparisons, each with stated uncertainties1](https://www.meteoc.org/themes/level1-satellite-traceability/). It ensures that measurements are accurate, reliable, and comparable across different locations and times.  
- Earth observation satellite data sources are measurements of various geophysical parameters (such as temperature, humidity, radiation, etc.) that are obtained from sensors on board satellites orbiting the Earth. These measurements are used for various applications, such as weather forecasting, climate monitoring, disaster management, and environmental protection.  
- [SI traceability is applied to earth observation satellite data sources by establishing a robust metrological chain (infrastructure and methods) that links the satellite sensors to the SI through pre-flight and in-flight calibration and validation2](https://blogs.reading.ac.uk/weather-and-climate-at-reading/2021/metrology-earth-observation-and-climate-data/). This involves using reference standards, such as radiometers, spectrometers, and thermometers, that are traceable to the SI and can measure the incoming signals from the Earth and the Sun with high accuracy and low uncertainty. [These reference standards can be either on the ground, on aircraft, on balloons, or on other satellites3](https://www.npl.co.uk/earth-observation/truths/next-stage).  
- One example of a satellite mission that aims to provide SI traceability to earth observation data is TRUTHS (Traceable Radiometry Underpinning Terrestrial- and Helio- Studies), proposed by the UK and implemented  by ESA (European Space Agency). [TRUTHS is designed to be a ‘calibration laboratory in space’ that can measure the solar and Earth radiation with unprecedented accuracy and stability, and transfer this traceability to other satellites and sensors4](https://www.esa.int/Applications/Observing_the_Earth/TRUTHS_a_new_potential_ESA_Earth_Watch_mission)[5](https://www.npl.co.uk/earth-observation/truths/more-about-the-mission). TRUTHS is expected to improve the confidence in climate-change forecasts and reduce the uncertainty in climate models.

Many papers report the “accuracy” of a measuring instrument despite the fact that accuracy qualifies a single measurement and cannot qualify a measuring instrument.\[[Metrology part 1: definition of quality criteria \- PMC (nih.gov)\]](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7889530/)

Reference approaches available in [JCGM 200:2012 International vocabulary of metrology \- Basic and general concepts and associated terms (VIPM) (bipm.org)](https://www.bipm.org/documents/20126/2071204/JCGM_200_2012.pdf/f0e1ad45-d337-bbeb-53a6-15fe649d0ff1) without specific reference to reflectance definitions.

From 20 May 2019 all SI units are defined in terms of constants that describe the natural world. This assures the future stability of the SI and opens the opportunity for the use of new technologies, including quantum technologies, to implement the definitions. \[[The SI \- BIPM\]](https://www.bipm.org/en/measurement-units/)

The SI is defined in terms of a set of seven defining constants. The complete system of units can be derived from the fixed values of these defining constants, expressed in the units of the SI.

The seven defining constants are:

* the caesium hyperfine frequency ΔνCs  
* the speed of light in vacuum *c*  
* the Planck constant *h*  
* the elementary charge *e*  
* the Boltzmann constant *k*  
* the Avogadro constant *N*A, and  
* the luminous efficacy of a defined visible radiation *K*cd

The numerical values of the seven defining constants have no uncertainty

The definitions of the base units specify the exact numerical value of each constant when its value is expressed in the corresponding SI unit.

All units of the SI can be written either through a defining constant itself, or through products or quotients of the defining constants.

\[[Defining constants \- BIPM\]](https://www.bipm.org/en/measurement-units/si-defining-constants)

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAnAAAABDCAYAAAAcYjiJAAAZDklEQVR4Xu2dX3rauNuGbZKu6DvCkLlmE7ODYtJddAMNpmfdwhxOg3PYDfT41yZ0JUlAnx7JMkKWbAmSNKTPfV1c0xhZlkSm3H1f/ckyQgghhBBCCCGEEEIIIYQQQgghhBBCCCGEEEIIIYQQQgghp48Q9WN5/Sj++Vecue8RQgghB1EWmSiqtXCvnyp5UYqqfjv9sVnX1bZY3AlpBLn7Xgy/qmKzWN2Jjx8/jtz33jLrVbUpFrey3+Lgfo8mpcDYuddjEHX5eHW7Ef++QoG7nI7EZPHzoH6Bs8lMXF3fHnz/EJfTMzG5+nFw/euquD+fzsSX79/fue9Jsb6XvxCou/N6/9+9KL+Lzj2EEPLbKfEXVVEd/Bfja0aI9Vb2UKy22zfRP/lFs82Lhbh7gv4I8WuznORitdmKj+JwoTkFhOxlPl6I283x4wbk79Umz2fi+nGTVF9dZo///Pvvq5K3y/MzkY+vxDchzt33UhHi7mGUvxdfH9LGpY8P787EaPxJfBdPI1Gf/zoXZ7KNT1UfIYT8FuQXkYDg1EJ4/8IV67r9l+g6UCYFsb7Z4j/qj0JxUAQphTLPlaC+xLOeE8ioEi4pb76+yM9qO5fv44/FbOEt4yKFcOMK4XyU48b2c7dfs9XTfTG/FJCt5XQkrjdq3DqiKtarzXwyUv0b63HrlPFxeTYSkMJ/RVw0TQrz43I6fVXRNzk2UrhmQeGSv1Pyff3Z3242UZIHIRxJIRQRZYeAEEK2vt4/Btp3c2/a91PKdIyUIdr24d25+PGwK88IHCFvmHVVBCXHh/wLQWSlkp9ocI+Khr0QkLeqyPr65fQhLHqRdOvbHlVfFIhazaXE3anv72GpkZ/1Ns/LqLLA1C//FFXeoO4pV9H9h7zl2czbLlHPttls1aZU61m2DYmeixI2KXEfI8VlCDl+m5Ecv9j6IJFoQxaZzp2PpDjNruPHTcobomXC0x6xKjcZ6mpSqqsy24REzwXz2SBxiOrFSlwKchwfz0az6LpNe7J/4iJ8kLfPF2dK3r55ZOv8TH4ms6/tOJ+N4iJrsh0PkLgfUqiEVS+uf5DXs4/fOs/yAXn7fHGu5O2LR8zeoa/vnfYFRM9FCdv4k5I49z1CyBsjWeDqUkhXiS4PcA/+415/LsS6EkXgef7IXCGqdVqfDG19e8Im67s7rL5U6jLbVtLgjOD0kSxwdSnLZ1F12+CechWf0ptA+CBpDr7IHARuoY11sE1ybDZ5Xhw1L8wmWeDqUpbPo58/krI3u47/4p1CUD3C54vMQeAWt5votiMlivLPsSghWeDqUpbPo9si//9/uIAE/d0VKl9k7mw0Flc/4wRJjsvD1Y9HjONO4Ory4Vw+7+O3riz6EHeLhwsIX/mlI2+yffduZA7t+/TjIap94DyxPCEnQV2Voih0+LgoT3NuFITB7sOx6b9EgVPPNa8Y6ZF/4e3dA7lxing5pp/WM/cwkTm73X6hi2OvvkYoIB1doUtDrJfbsihUnUgf4pK6jK9jR1wgWTraNSw0KQIHMcycz23oPtyTO/dAttxyLhC+mUf4dGRu91yf0PVhBMqNgGGOXL2ct+1EmjVGbFIEDvKYOWMRug9yZdJl+jUWkCe3nAvu8QmfjsyN2+f5hG4ISJOK4DlRL6RLJ/hccqRlrw6ae5cicBDJbG8cx4P31fPs4Uy2729HqExkDrJmZEsLXVwEDkDWVHSsibZB6HB591Lj3ityuOdsJP+R82U/+gZ5wzw2yNeXJrXpE7oh3p0jgvdfp/zN50txMW1S6u8/4XehI5CEvEr0F3WhVu+ZCE2KFDwR1v/onlfRLyqtMDQrEFWU6chJ+ikCd2gqVN2TkHY9tp+41yeKpv32GKuU8MC4h7Dr20nGzRb13R1QnwHSUq7we7rcTnJd/7qW//iosELQEThZRj0vQhhTBA6kpkIB0q6xQgkgZeivT/TwfKRAd2NrUsaRAver2iC65wqaEUOsVEWZLHLxRIrAAZXC9UQWfajFCFbKcwhIGSTNJ3oqFTvezXlD3bgG2TLXhhC/lo/u4gg9120kFte3AgsWpuo5V4NC5ZIicEDNyfNEGkNA0kYQ2I7A6RQo5pR9ayQL1zCvDdfssiHEXfWAPiONaq4hfTqyUp5DIH16JttnJM0g/+64x8KG/TlsN8kp0b/U4o39xRFaBMfi038/8f13jzL/e1CpYEoced34xANRmtRU4O/GFaFQpKkPK50ZfIVkBrKXJT6vIWmsj+1nSOB87ce1Q7cY8da3LLY+0YpB3JRNBEvfiyiHrivTYuQRtT6Ba1Og1mfbeVmC5JKaCgWQRHVPoE6XPoFzI3NaQLP4uj0Ch3lpSqqsqJx+TvcLso3guWPWHT+vFKkImadeH5BDRNNMO4foEzi02Y7MratxUioX+ATOFSlEx9DHodSmSYHij8GXXhzgrQf3zq7jI1AhgZNj/IC67Mgcro2vfoq/Y+eveQTuXNb5/mt8yjIkcGtsB3KW70XmcG386Yf4vy/dLUJCuAKHeXFY3JCVuzrkZ3fPRQzkJPB90UIKYlKAr4w9EdJi0xWVFFIicFqMlABGoyOfySnKo/oZEji3njbSd+Dvgae+bVXkev5bpGTY3Ki0pU6d4meIjZrfJlGi5ols9QmcS0oETotV2jYluCcmxakkrIlM9Qvc/nU3pTqET+CwTxykypYZ9zkhUiJwSrCymdrKxH3PBWVjUpwqzdoIVL/A7V93U6ox+AROi+FOpLTAjZNXn6ZE4GQ/HzFnrW9bEyOSJt0bEjidWt1dF56U6hCuwO22FwkLpkmZmrRrSODk///3mO9mp0/dlGoMrsC1YmjVAYH79L8H7yIKQl4V7n5gLz2p/ikIpPqSUpM+UgROpTK9z3MXAUhha35Gutp/j0T2B+V0SluL4VP00yfswBVQX2QP10zb0aa+sXHr0wKGa3GC4VLiS6jZFsROReLP2DJkpb7f9+tOifglCdy68goj6rAXEcjx2q6an3GPWpAw0JZ5PmnFFKhIIzbvtdBiN9sTSDcihwUNapWplDHImrvvG2RNyWITbUP0DWnNvYhcjdWa+xG5EEkCt66i60VZLEgYSp/OR3LcLDGDUI0X+xvMarGbKRnclfPPlevj17J4RN3/NFIkx64jdCqqlpDaNCQJ3Lp6VFG/nhWoaNvl2bStr420OVE1LXazNn1qxMqWN1z7+nMjvslrF2dzce2kLu9UxO6HrLuRQAidNSfOB9K0H86n7XPvFsUDhMqNqpl93IxUaaHrzpUbAnUjamd+RvTN3m9O/s7fq3lyVkSOkFeLKx6hCM1rxhUhHdlyxSmdFIGTtOnGdWVH4nbtUFEtq02QZfseE1lTaW1PWvUp+hlahaqFbddu9/fCl2oHISHs1AdZiBRNiFdZ48twJzt2BA7pT5OKrMtm/zKPeEGgnmMVKp5vTkSQn9t2rtqqrxuB0xG3SVtfm7Jtflb3eJ41mSBiuBOB0CpUiIgROCWU1nYiAPPhyp4UZe2sQjURuZ3Q6Q1/0Z+Y9GKSwEkxxMkIkDI5fhszfj6w5QdWoBqBQ1nfM6YYN0ugQqtQVcSqKQc5TJlbZ0BUy16FqiJylkhhPhyiXDh9Yf/OYZIEri4fkeJEO+Q4Pl56Pm9I3sVU/cNHty2wClVH4HYChzJKvhrMHLm+aBwEz16FikUNRujuqvLhctWNxEHyLi5U+xrp869C1cK2EzgVSUuYW2dwV6HqenaLGrQojhl9I6dCIcqy/RJuIyxARXya67vXvjCo1avN9TIwXwpf5qG5Y08B6kcfGjERRdFNZZr3yoRjllIErmrGsKjqvb4WzXgpcXIWG2gB02Pnjg+OuHJFOqafMdjiaNOIp7c9QAkkPmdrDLXA+YXfrc/IDEAduBcLGuqqEhAxLW1a4HypVrFeb03f1auQ9eqKOyKEOkJi5yNJ4FQETPcL7Tf3QKQgjPjZFTEldPOJuqdYrPbu0alMXKp1tM1qA/Z6yyFWTrvW1ayJ6BViZtVnQL3Y4HcWODrLndtmhE6JdobfLSmIEalTQ5LAqUhYM346paylUcra9a3+eTRHhE6MUNYZN122iczp+2+Ee1SWET9XPiGMetzGZtyse6rNXTUVo8lC1MulqGX/50gp25HLZfGI6J49tw1CN5th7PRctvF4lpw6NSQJnEqh6r7c6nE0kvZYSKFERBBz8yZX+0dliXrundu2ruYP+vd6rO795qwYhfxBTN9/7R69hegb5rvZgqdSqGp+31j81CnwNjJXSPn6+bgVWOQwsSJi6n2In2dum/zs7u322QsRPtR34nZ5oRY03Hz+LOrLd+Ly+n6vXjm2nbltELr37wv8z6M+u68/H8X3hJQsIb8NJRDdlFwLvrCVfKBcEz2xU2f6fp0SDEV2lCygqsAzjkVFtYr++tG2nXSkRayOxQhcVaQ9F/2qIWuNaMX0MxYtjv0p0BBoU2Z9zojK+WQwBkhWhulsGSK/uj1YqarSpYFUo0mZauHxlwG/4ySGncCtVRo05tmIEprVpOibe58Sv4i5cz4QRfOnYLsnMag5dE+4se8hQMrK67uoNqjtRZpFElhJivSpfZ8Sv4i5cy5qUUOzuhh11M797kkMZvXpc23sewgQSqwclZwhfbpw9nETnv3eYrm5vBC+FGzKSQyI1JkNf5E+Xfxw29d/EkMICJqJ3H3+61KsrLl3wnsSw/r+rEhbxUrIqyEUiXFBOVc+fMLmi7QhFYj7D5GFGFA3/uNeNxjxMT+r1F7CthvHAsEpq7AkD9KI81A/DW10rtyPBLqYcTnk4HedHj0OW9Sw2MCN0IVwU5Eu63q5RRTJNyfuuVFyuVioSGvssyf5bjEG5q2F+pW6SMGgImvWdicq+lTMOpKESI4rer8DSNPNfHhbj+lo0i5GgMyF0qCpixSwpUh5vcE/SDfzufoc1X3rlY74XW82e6KGNKbaSLdnHtpLgujbxdmkbeOo9M+Rg8SpRQpfb8XHb/syNgQEzMxrW9c6JfvV2n6kD5UyPZ+0adaz0j9HDnKlFil8/Sm+RKwyNduMYE6cHIP7W+uILdnG+3z8XvznLKaQn13yKlZCXg1IYbli5gPlXBnQqbNdCs8VJXVNpdzU/yjPJnB9KTzgzt16aYFLnVOI/rTz4mpEDvW4DfUTqHE2n2fkfDOkan3z7VzsNrnifghG4NQebgnCo1OjRVDg8qI8SEqfAkTLQqtGQ0CoMJ+vXsrPuszF9q4S88A/quTYq7l/Q2OFdLAZH11/syqwLjeLYEo1rd1PDVKe00qLJtKxwwKXK9G6WS7FXI7bBuO29Aso5AtjECNxRuAwp25vlemkFBg7uyzQKdVicLuQl0IL3Ehs5D+Jbj4vRS4F7vF2GWzf5RT9fej0y2Va3aqomxE2kyo9n5bi6np/sUgfWuBG4nH7S7VvJAXuQbYvNLfuciqlzEmF+jACd1t/EBfTxf6iBNnGL9+7koaIXeoqVkJOCl+kDbipM1fo9M86GoRXjCg+B79b4F4avbHvYXPjCCGEEPJG0Km7rhAgsmQLHMRh/2drrpyag/Z7BA7YqV233W8NREJ9qWxCCCGE/FmYKNr+xWaSvXoPZ1O615vFEW0ErFnsYFXxopi5Yb8rEvjcqFSk+awYgSOEEEIIIYQQQgghhBBCCCGEEELeEthSRG+6m4nZAqtnh1eREkIIIYSQVwK291DHbxFCCCGEkNPA7PvmXieEEEJODut0BnHo0VivDWwsXFTdDVNjURv9YhWuZ7Pb5uiuZqUuzirtHy+c+oD/6FfZHh5/ivyqqw3ORjWH1aeSBzay1WegtivVzZmcg8/AcV5zdU7m7l77ZW+6i2fgoPqYegkhhJBXjxK4yBMXXjs4xaAq8uYUha58pYDjtPoEDUd39b1vUAKnjqE6rj2/G3UmKk6I8AhYLEYAQ4KGo6cmo/D7hwJ5m5T7h84TQgghJ81bETjIm4ogBoRKrG/aSFj0mamytnng0HufwOF8VRxTtVfuDQicPkO1e/apAVImOyeK2f7h9iEQNcOh965Q9QmcWNcbdX4tPsOiEEW5EFtxI4YicKjTRN6UyB0RmSWEEEJeDW9G4G7KrU6bdkVJn33aiNta9jVBqHCvkrI/WOD6Dqn/JaWoWKzUOEB289nu0PsQJmXqrggNCRzOX50qkdbX1eHyWREUSgNWoKIs/mheXMRACCHkTRASOFx/qqPL3DNuh7Dm5UUBmSp0dKYjSb7IHL78q4RD133ljxU4XPeJYSo4dB7z6twIYQhRz7aziMPsDeJXtckgZZ55b25kri6zDQ60d8XMB8oubrd7EhYSOAikagMhhBBCNAGBMwKlXsceHZYicDiDNdt7/u6ItRA3ZdakRx1JMnPi7kQrSkbo4DB22T5U6k5J2I5jBA7RQLxlXgudo40SKpcUgWtTkAnPhWjNVpuOlLVz4iyxdYWuD0TVXDEMCZxKucq3TQTOXLdR+71hgUUWn8olhBBCThafwLVnzz4RKQIH1LO7UhkEkqZEz01zipttKaXlDl/7rcDddMRriAnER95jy84xAmfm1tnXDiVF4NrnRpQFkF1IGSStK3D1BvPYbFEyc9uiBE7KWibLQtbsaz6BMynUrJiJlSdyalKli+s79WxsF4K6Q7JHCCGEnDw+gdPCdbjAWSnQ8EvKz+6ODknp25DAmblvmSVKuBaaKxfiqQUO0qWiYZEiZaPqc8fSeTWRqk7d5rm+93z0CRzmvrmROdQdmivnkiJwhpv5SOAZt852IEocrRTrqsz0HDtPHYQQQsibwCdwVQERiI+YDZESgZPSoMr27Ue3S5nqOW8hgdPldtd3KdW0uWdPLXCVSjWW0SLVR0oEzqQ4+8rWMzlmkCFZpk/g1Bw267ovpdrHIQJnIm2uOELWcM38rAVueJEDIYQQcrL4BK6AHHlTmIUzH06KVsT8uCSBW1eBZ+/QqdGdmPkibUCLXdmWa8WvR2B8oG53Y+BjBE6dzenMqTuUFIFTzx1YDIA0KwTX1KdXmd7tz1WTsgaxW212ixBCc+VCYCWqWhFqlXcFDqnT0USJc1tGL37YtM81qVxE5UyZEVKos+vefhJCCCEnjU/gcLmoEAnDF60tXjuBQ6QsdnFDksDJ9tjP9qVS1apTKyIWWoWqhW0ncKpMt6+DPPUqVDvVKPu4TRVKmxSBy63tQNbVDDd17pEStbVTsKFVqBApI3Aoo+TQs1I1RMwqVEjeKC8tWdMRODuFqiJ5VvtQRkUCb3lkFiGEkDeMT+CqUs+BK6pa7Z1mrheNwCFKBoGybuklSeBUChUyVuw9W0laqduDhQmdiFhgH7j10swZ0/XZ0lLWa4G2QcLqqpJDkUth3Bew59gHrppP8INQ+6dZfcylrGCS/lrek0eKZorALfFcJY963zZzHfJVzHBSQa32cnP7GtoHTkmb7MfMqQ8geoa+ICKXz/cFUIvZ8D5wUm4384n+XcQLq0vdRQwq8jcrRCPw8vdSpYijRZIQQgg5SXwCF8IIXFW4qdTnB9E0s5oU6VO1NYiFb7+3GPTZplpYqsn+/S99EsNE9qs84qiqQzGrSXV/J52+pmwPYkBUDn356InKHXISgw9fRI4QQgj5I0gROGzvUVbVXmTsJVARP2vOW9PejhC1ixQiz0KFsJRNxAlCZkfo9Fmo4cPnn0PgAPqgheplxhgpU7MfHBYw5IG5eYechYp76rk+QQHyh7NQEbXDmPpkMFngMEdOpW6HyxJCCCFvCiVwmdmCon/1p16dqlJaL4oWOOkDUh2R6oTAbbHYISBFZYFtSPziZWMEbo15d/acOqQwi93cORsdsWvGK1bgrPENCiHKNc/LnXqfEwgc2ryVY1uWuYDAzVWevNt3cxi9m/p0gVhNKi2CWARhBG40Kb0CaFKqWTNOsQKn7+NqU0IIIW+GfhEjhBBCCCGvDgocIYQQQsiJQYEjhBBCCDkxKHCEEEIIIa+ddgK491UEV452y/LF15/x4sIHQgghrw1G4AghhBBCTgwKHCGEEELIiUGBI4QQQgg5MShwhBBCCCGEEEIIIYSQU2S91EdjFVX3SKinAsdqTfJMHaeFI630YfKF93grQgghhBDSA84BLXBGatY98/QpmeOA9mLRCps6m3WyO6uVEEIIIYQkkj+zwOU42N0SOEIIIYQQciTPLXAqApftUqju+0CI9XZS6E1pi3Ihyz5fewghhBBCTp7nFjgg1rWaa5d55r6tq2Kb57vrdZltOUeOEEIIIaSHIYFTc9aQBt0d29R9RaRI6zkWLyASp0JxbVkVoStX7fO1wGWD9RFCCCGE/LEMCdxTgmibepYlZ3lWipWVMtUp15ICRwghhBAS4rkEzrfaFNG1hZ4Mp64JUW8RvbPnvKlonxWRI4QQQgghFlg8AIGDMD11xMukQs3ihcqz/xskLytKsUKhdb3FHnFuhI4QQgghhDRMimJvHlshfy7rp4vEratyO7eeUZSVEjW7DCSvLAtRtG1g6pQQQggh5NWC9Kme70ZhI4QQQgg5CdrVrYy4EUIIIYScBnqOHFOmhBBCjuf/AfIVJFvXunvYAAAAAElFTkSuQmCC>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFMAAAAVCAYAAAA6s9JxAAACaElEQVR4Xu1XDc6sIAz0XD0Q5+E0XMbD9DFFVn5aQY2+fImTbHYXpJRpO8Vl+fDhw4fzWINnRwu3438Vqyf2YX3/PMzY9D9t/iAkOci/dyYv2ejMDbdsZXI+Us7mczPgNeTsF3vt/BNgDkLoXd9nweT1jESpkA/iiIvPLS6oz52A2BNSYe89cHT92f149SZBbcYGh/+kPjsCZAT2QpEdsBdjeMneWdzxfRop8/SsXJqMveMQBwlKtfZNMnHOZVQJZeNAlhGSbVIbcrZoB9J0Rsryopi3a2EfY7O+agBBbmuYOLfIkRI0YIobaf8FGWeifUjm7lT9MSRhAr0t5dCzKDNNEmoLvBWkIZl5YTkGMmeF9ojMFPVu/EgSRqjsTZXdMX6BReCzX5fJTBq2N4hsqBT5ESzyMV7akUbVlH1wJA5imsi+WiW4yp6suygZpQTlhMh+WUHSNLtCp0OjBQq0BmR13o70uDekOkXdJjPpek0mhjt7k6jJrKsz/e59sUguEY2mhbi3oRGdddA4qASmFPc2i7JOgcxy3JAHQOzhlVUrt7yHBNLtNiwSUkUQp/n4vb0MZJ9btImnIG7qfpt1BzuBLjuBXMJuu7S38+lNpr4qtQ1xH3ebJJDYK+c4EiykIDg+Bagms7+ORfYYMoOf8qHebgMryEtK9eudtYIl2tPYSk6TjFlARn5NJMmVYGQvXYnsZzTJ6lB2MAsBh9siRwPiy/tqOzfEwPYMEExkDvTXnXtntzNuyfLRa2iFtttqINHQC+QMUHZxlFc7fwXp1ZUuVEev948AbwM49A0t/QCUutPeDz/U+AcrLA1YD7NrJQAAAABJRU5ErkJggg==>

[image3]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAATCAYAAABGKffQAAAAeklEQVR4Xt1QQQ7AIAjzXTyo7/E1fIbHMAvLNg3zvKwJEqFiaWt/h7s6UxVQZ/40tMNFUq/5Rq918W5Pwno/QUeQDkzl0g0FibgaaSfGWZBjqvSbrOMhwv8Sg5yT3UiSV2JjEwhChFaLEaFv8+UE6pPh0VovQSfKrQscumpf1knAJvgAAAAASUVORK5CYII=>

[image4]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAwAAAAVCAYAAAByrA+0AAAAiUlEQVR4Xu2Syw3AIAxDM1cGyjxMk2UYxo2hf5GqSD32HUNsXFORnzEmAnPgPn9AUeqEQGP7PksB6pz7t3gxqAqvh1p5jlHLtQk3ybMDDnZ9nlGQds/DeJ79cDOI/bGgueuRGd7E4+WVEPQbUB182TROJxZMN1d49rGEecXo+hLmnfpX2FDaxoAFvqhoaMZZv+kAAAAASUVORK5CYII=>

[image5]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAATCAYAAACtHkzTAAAAe0lEQVR4XrVQwQ3AIAhkLgZiHqZhGYe5gkSsxqSPtpcYAgJ3B9H/AAwRTk8MER/wfsO3MBUwJz+LrvxNGdqmKBOaeTiRVF6IhnIRCZFUwxjw/6z1aZ6csN68bPSG3IAWh+P9SF4QHlOwm9g8tfRznxF87H72eiEclNoDLj4cbvDGbtvtAAAAAElFTkSuQmCC>

[image6]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABUAAAATCAYAAAB/TkaLAAABYElEQVR4Xt2Tr2vDQBTHT1REVkZMtDATqBlMNDZ+ZjIQMSYjp8oxO1FOjf4LqxhsopC51gxiBjGDmEDMRGTERMTEd+/aJO1dLmLQie0DD3LvvXzzflwYfgGmO47BPxCtsggiOMNwwMAY2YkHvin1NCNG0WJ5CffqCXklTxWKVYixFLZCrL/07C4d0erlGkPDy1EgK3YgMtVvQhNNwUcM49tUdcvInUOiPqIfV/rGYbMx+LviJQospvSxWaIHjCiiyczezi0+dBLls4/huUDaVJkJOHLG0oJIyZUciCbgNiUNXPDXesufBdZzD/aUI9YWn88dOPNcddbsRZvWlwKutavCOvVw85hjewkUcohJ/9Ja0W3rI47uikxE8CcC5jpb0RghVefeF2q0j5Xf27pkJ7oJYTEXiw8t2oO8s/6qPtDSRPNcQ6IlHi5ofrTF7ux0qO1m663R3dWyOn/UMfg7ot/8ALD/hUy7VQAAAABJRU5ErkJggg==>

[image7]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAHYAAAAXCAYAAADeD7vuAAAE8ElEQVR4Xu1ZPWjbWhS+QwaNGj30QQUZniGLIUMMXeqthg72KPBQSoeH8VQ6BJMtdDCiw8NT8aoMD9yh4NFZAupQ8FJwhoCXDB4yaMigwcPpuT/y/ZUtmjzaGH8gYh1dnXvu/c7fVQjssZMgpmCP3cCe2B3FntgdxZ7YHcWeWBXXEcSpKXwCuB1B46Cpif5MYr+GQAixr85kPWTScTwnIcgRiJvIMUZe1cFCGbyA6Lh4OxqHHn/vWQjxrfm0DFKo+Xxe78U5zO7N5w/D7DQA1SeLV/KbEZobL8hWwcnNyZywd0xyoyPdIXKEpArRjbzPLtpAvFAK1khh2qvDMsOf2RzOkXzSioHelsZqDqNXdchW+PtuDCESHJzNzVEPQxpD91Le/rHEVpGk8KsqWTCSVIoYsQppi0EVidUJsxxEYDKIQErn0H+OkdRLlBHiyaAGtY+SBDaH1wV7ZBFStDOA8IuMJ2b3yxEslVGPAXIyXOssReziv/cyFREPgtYI5tT7/kfoUSajcQ1Ms1WFxDw1mySSI5VAqsdI10DTWIXpHmtrWsLwxIysJYxe4jzHqs4NWE2h6xFoX6jxnTAZeWNasQGrJUzP2lD1PdSVQuWA81A/S7T028D11z5xy7YTmybQvxKv32NKafnODXSCbb6safblSn0UC2ucuQ08OjePsfUQg2iKDOLXDvlVFzzzXXG5ItuF5eeG9W5+NT6XjNcUneMQHezNGOZpxuxKVzyTEBJA/4ccyhxGBMQWYrmHargdQp0a56hbjwZ0CDWd5tGopmY1DVOS1fFrUMcy67RlN0/xZmpMep5F9vwsQDsq0P+uCAsholubD52oRdfShLhU88R1+Kgjj8xJx+c/RNCoe8LWIWzeSCxrKIjeRsNqXFi3HguUKH37RSpGo9X7tQ0mgTmQSI1w6jBa3aYQxGoEzKBfIVA5nUmRSKtqHduI+xiaaGNTTcMiKLx/plK2CZc0a9RhmHfhqLPtd/nv732oGE5WkliRol7HuphN1ix33vvFVEyj0ZDoNdaoryzlWpHI9dhSE66I5fOFX+So9KKJ8/vQvZKyjRA2nl9LET2SENKAUcnjkpk1aKAFwtmSnm9llFLEZmwh6LXYKFGS0x9jePt3BYu3XD6NLGekPAB5Z6vfc1I5SYJkg0jmQKrMcTwqwvwjnUNNj7xx8jtjVs+ymzEEvanWqLih2CYinHbUNGbTqwjrapkjjtTBMybqOJ3C8g6j9XkfknQOFa8O/W+2NbR5ymt3wcpFfWgNIX6HHeOBD7XOEJI7fVR0VFDbfgl5VDouhTAz4vMnzFuZ7C+oFbxbCJbWPO0cCNcjaD/jOrzDtvIAlA8oZsbRnS69fA81mr5R5h+/FWNEhhCRRR1Xh6ojheTfcP1hg9lSqcLM4CGHetRzE7scMfb1Nt1GaHaSTxZ8s8vWvsXAqN0qrs+hutWZ6HwyA1mwdNCyqHfANrLt51jWpuMhfLrlrPrYafh3gqc9IzILgcR0XE6dQfIhKPVVadLh0bUY5A1hDocO2ohhGt6oFRuzLV+eeH0p473rVtvZbT41bP5WvAamYbZu/Gs5Nq2rJxgQdvmzwImdQFRCBw20bc5CGzO1W7dXggdgX22xnTDroevjwBNEif/uyGbuYf0F11Nm32i/s2Uu9t+dhiayid1jJ7AndkexJ3ZH8RN/nLt9KDyWgQAAAABJRU5ErkJggg==>

[image8]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFAAAAAUCAYAAAAa2LrXAAADgUlEQVR4Xu1YPWjbQBS+oYNGjx5SqCFDDVkEHRLokoyGDvFWgYeQKRhPoUMx3UIGIzp5KqabOwTcIaCl4CwBL4UuBWcweMngUUMGDxle3/1Iunt3lqW6oRn8gbD17t3P++579yMGW2wERg1blMOWwA2xJXBDbAncEM+HwLsQ/BcNGMa0YAWuA2CMQXBNC3TEMOk1hR+r+BB8ncKSupTCAgaHJmXmmxqU69ERtexyxgKIdKdZ6PDJnnpvrjnPIXxDbQmWML86h6MdrLdzCpEiWI6hDuHM9NYx6VREX8OrPpy/rYr//mdXHyXws2tMskOBEQQ0QE5sy6BHBZCQJutQEsM9ZtWTiIzAl99QJR7WfchsEjFEJz40emNYoHQueHvHQ6Ei0b+zbYX7PhzgmGoffylDDKP3Ho6xCUOrnzKIwTsbp282gaicOqOpMbfIoQHMe3VLEdZEaMisU+i+YuB1JlqpKun54F9O03fRh9eGCVfsXr76Fl+OrPHAbRs8K7byYOwA+vfqv1kEKo1JOuKbOds8AHMgpiIlrACwbWvwmBJV5kH7ltgx2AqSNX7MTNNLPkmYxlzxeepDRCf2eOBhCA0+qdqk/A24MGqfZBuEQElM7trGvYTa8n2kaklbe6GmPI4lDN857DdSKVZ9fKppSuYB2z12tJssNWvIX4dJhy8FMmaTQJG+pmqSDUOHnr6cTGcq8bbWrKPphB0OcH/LMD7zHMFzRdeg+5sYV0CM8fUFmFr7NwTqy5XBjCygapKdZsGQTYYSlQAJM4hFv5Cmb0IgCahbdSjtcQxsv28QnYeyKew+WWSPHuNKAunGoKyCsNRqqXTuqCPbsq0UbgXy/oLvmgHkpmCtkznI3URI22WxkkDnrqnOhglcKqXvCTHrodZAkmqCQF2t8QgCr0h7Gp7sGJOzBtIZyzaLQFncawg/9hg2Qnoe5M7aMILq7zOotEYQ4w68nI3gdBeJ6GRnLzfo2JaYxo6DdC+bKlcsRcBvI0nWqCiTg7DjUR3Ya0Smumznfgm+o24ukmPMjWa7G0CT3zywDW+3Cd0fWoKntyWqekog4jH/Kmf5F4RYR1WmFpPJE0PcRAqnFi4PLXuH5oqbfKil57MiKOsvsVhzE/kvyLsLa0gO4vhr+eIu3d7Hg3fRjxGIsv4CmDEDdQvheCYEQqGvMdmavOLs+eSwv8b8AYrGEHz/S0r5AAAAAElFTkSuQmCC>
