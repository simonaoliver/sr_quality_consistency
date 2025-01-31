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

