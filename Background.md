# Background {#background}

The CEOS-ARD Surface Reflectance Product Family Specification (PFS)  provides a strong basis for interoperability. The CEOS-ARD Surface Reflectance Product Family Specification includes:

* General metadata requirements ensure traceability, machine readability, and accurate data collection times.  
* Per-pixel metadata addresses flags for no data, saturation, cloud presence, and other critical indicators.  
* Radiometric and atmospheric corrections focus on providing valid surface reflectance measurements and associated uncertainties.

Geometric corrections emphasize achieving sub-pixel accuracy for consistent geolocation across time.   However its non-prescriptive nature tolerates different approaches to the derivation of the ARD Surface Reflectance .

Every dataset producer has their own constraints, priorities and approaches when it comes to defining a Surface Reflectance processing chain, however studies (Claverie et al 2016 ,Main-Knorn et al. 2017 and Saunier et al. 2022\) have shown that using equivalent processing steps and model inputs results in surface reflectance products that are more consistent and able to be used for multi-provider analyses of various indices (Samain et al. 2006). Consistent Surface Reflectance measurements are crucial to optimizing results from multi-provider data integration and analysis.

Inconsistency in surface reflectance quantities and their impact on analyses are well documented (Claverie et al 2016, De Keukelaere et al 2018\)  and have also been expressed anecdotally by industry contacts, who have noted the need to independently reprocess data  to address  incompatibility of surface reflectance datasets for multi-sensor analyses from CEOS Agencies. This is something that CEOS should seek to resolve in service of its stated mission to promote the exchange of data. CEOS Agencies’ own efforts in producing NASA HLS (Claverie et al 2018\) and ESA Sen2Like (Saunier et al 2022\) demonstrate the need to improve the compatibility of measurements across providers to enable homogenisation and fusion.
