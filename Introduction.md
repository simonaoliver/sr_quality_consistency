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
