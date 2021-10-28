# EQSAM

The EQuilibrium Simplified Aerosol Model is a framework to parameterise the water uptake of atmospheric aerosols, which usually include mixtures of semi-volatile and non-volatile aerosol compounds. 

Version 4 for climate simulations (EQSAM4clim) extends the orginal EQSAM version of [Metzger et al. (2000](https://dspace.library.uu.nl/handle/1874/646), [Metzger et al. (2002)](https://doi.org/10.1029/2001JD001102) to nanometer-sized aerosols [(Metzger et al., 2016a)](https://doi.org/10.5194/acp-16-7213-2016). EQSAM4clim is based on a compound specific single-solute coefficient, which was introduced in [Metzger et al. (2012)](https://doi.org/10.5194/acp-12-5429-2012) to accurately parameterise the single solution hygroscopic growth, considering the Kelvin effect. The unique, since fully analytical approach accounts for the water uptake of concentrated nanometer-sized particles up to dilute solutions, i.e. from the compounds relative humidity of deliquescence up to supersaturation (Köhler theory).  

EQSAM4clim extends the single solute coefficient approach of [Metzger et al. (2012)](https://doi.org/10.5194/acp-12-5429-2012) to multicomponent mixtures, including semi-volatile ammonium compounds and major crustal elements. The advantage of EQSAM4clim is that the entire gas–liquid–solid aerosol phase partitioning and water uptake including major mineral cations [(Sect. 2.3)](https://www.atmos-chem-phys.net/18/16747/2018/#Ch1.S2.SS3 "https://www.atmos-chem-phys.net/18/16747/2018/#Ch1.S2.SS3") can now be solved analytically without iterations. This can potentially  significantly speed up computations on climate timescales [(Appendix B)](https://www.atmos-chem-phys.net/18/16747/2018/#section8 "https://www.atmos-chem-phys.net/18/16747/2018/#section8").  

![](https://acp.copernicus.org/articles/18/16747/2018/acp-18-16747-2018-t05.png)[Table 5](https://www.atmos-chem-phys.net/18/16747/2018/#Ch1.T5)  CPU times of [Metzger et al. (2018](https://doi.org/10.5194/acp-18-16747-2018)). EMAC @ 96 CPU cores, [Cy-Tera](https://www.cyi.ac.cy/). 

Note that EQSAM4clim has the advantage of being a short Fortran 90 code with approximately 850 lines, including comments (or about eight pages; see [Appendix of Metzger et al., 2016a](https://doi.org/10.5194/acp-16-7213-2016)). 

For comparison, ISORROPIA II roughly counts 36 300 lines (or approx. 360 pages). This is about one-third of the entire source code of the EMAC underlying climate code (ECHAM5.3.02), which has about 119 900 lines of Fortran 90 code (also including comments). 

It should be emphasized that ISORROPIA II was developed for air quality rather than climate modeling, and we offer EQSAM4clim as an alternative for computationally demanding climate or NWP simulations.

# Selected Results

EQSAM4clim has been implemented in the global chemistry climate model EMAC and compared to ISORROPIA II on climate timescales [(Metzger et al. (2018)](https://doi.org/10.5194/acp-18-16747-2018). The global modeling results show that (I) our EMAC results of the AOD are comparable to modeling results that have been independently evaluated for the period 2000–2010, (II) the results of various aerosol properties of EQSAM4clim and ISORROPIA II are similar and in agreement with AERONET and EMEP observations for the period 2000–2013, and (III) the underlying assumptions on the aerosol water uptake limitations are important for derived AOD calculations. Sensitivity studies of different levels of chemical aging and associated water uptake show larger effects on AOD calculations for the year 2005 compared to the differences associated with the application of the two gas–liquid–solid partitioning schemes. 

Overall, our studies demonstrates the importance of aerosol water for climate and NWP simulations.

### AOD results for the year 2005
![https://www.atmos-chem-phys.net/18/16747/2018/acp-18-16747-2018-f12](https://acp.copernicus.org/articles/18/16747/2018/acp-18-16747-2018-f12-web.png)

[Figure 12](https://acp.copernicus.org/articles/18/16747/2018/acp-18-16747-2018-f12.jpg) of [Metzger et al. (2018](https://doi.org/10.5194/acp-18-16747-2018)). EMAC model AOD results for the year 2005 (annual mean) based on ISORROPIA II (a, c)  and EQSAM4clim (b, d). (a, b) No aging and  (c, d)  aging cases. AERONET ground station observations are included as squares (same color scale).  (e, f) Satellite observations by MODIS  (e)  and MISR (f)  (550 nm, annual mean 2005). MODIS monitors the ambient AOD from space and provides data over the oceans and, except deserts, also over continents ([http://modis-atmos.gsfc.nasa.gov/](http://modis-atmos.gsfc.nasa.gov/)). The MISR aerosol product is available globally (products can be obtained from [http://disc.sci.gsfc.nasa.gov/giovanni](http://disc.sci.gsfc.nasa.gov/giovanni). 

With [Metzger et al. (2016b)](https://www-cdn.eumetsat.int/files/2020-04/pdf_science_cal_val_pmap_presentation.pdf), we have further evaluated the Polar Multi-sensor Aerosol product version 2 (PMAp2) of the Meterological Operational Satellites (MetOp) A and B on global scale using MISR-Terra, MODIS-Aqua/Terra, AERONET, CASTNET, EMEP and EMAC data [(EUMETSAT ITT 15/210839)](https://www.eumetsat.int/PMAP). 

Our cross-platform analysis comparison based on a 0.5 hour temporal collocation window and a 30~km radius for the spatial collocation relative to AERONET station observations, and a fairly high spatial (0.1° by 0.1°) and high temporal model resolution (hourly output globally), reveals best the differences and similarities between the various AOD products, which are most likely caused by various cloud masking assumptions. 

![ Spacial AOD distribution of the re-gridded Metop PMAp2 AOD versus MISR, MODIS (Aqua, Terra) and EMAC results with overlaid AERONET station observations (squares)](https://www-cdn.eumetsat.int/files/2020-04/img_science_cal_val_pmap_2_lrg.jpg)

Figure 2 of [Metzger et al. (2016b)](https://www.eumetsat.int/PMAP): Spacial AOD distribution of the re-gridded Metop PMAp2 AOD versus MISR, MODIS (Aqua, Terra) and EMAC results with overlaid AERONET station observations (squares).

The best agreement is found for the Caribbean, NE America, European and Asian stations, while generally, the PMAp2 AOD time-series are supported by our model result, which are mostly in good agreement with independent AOD (AERONET, MODIS, MISR), and aerosol composition (CASTNET, EMEP) observations. 

# Selected References

## EQSAM (v1)
- Metzger, S., Gas/Aerosol Partitioning: "A simplified Method for Global Modeling", Ph.D. Thesis, University Utrecht, September 2000 ([Abstract](https://ui.adsabs.harvard.edu/abs/2000PhDT.......328M/abstract) / [Full Text pdf, 45 MB](https://dspace.library.uu.nl/handle/1874/646)).
 <br/>

- Metzger, S., Dentener, F., Pandis, S., and Lelieveld, J.: "Gas/aerosol partitioning: 1. A computationally efficient model", J. Geophys. Res., 107, 1–24, [https://doi.org/10.1029/2001JD001102](https://doi.org/10.1029/2001JD001102), 2002.

## EQSAM (v2)
- Metzger, S., Mihalopoulos, N., and Lelieveld, J.: "Importance of mineral cations and organics in gas-aerosol partitioning of reactive nitrogen compounds: case study based on MINOS results", Atmos. Chem. Phys., 6, 2549–2567, [https://doi.org/10.5194/acp-6-2549-2006](https://doi.org/10.5194/acp-6-2549-2006), 2006.

## EQSAM (v3)
-  Metzger, S. and Lelieveld, J.: "Reformulating atmospheric aerosol thermodynamics and hygroscopic growth into fog, haze and clouds", Atmospheric Chemistry and Physics, 7, 3163–3193, [https://doi.org/10.5194/acp-7-3163-2007](https://doi.org/10.5194/acp-7-3163-2007), 2007.

## EQSAM (v4)
- Metzger, S., B. Steil, L. Xu, J. E. Penner, and J. Lelieveld,  "New representation of water activity based on a single solute specific constant to parameterize the hygroscopic growth of aerosols in atmospheric models",  Atmos. Chem. Phys., 12, 5429–5446, [https://doi.org/10.5194/acp-12-5429-2012](https://doi.org/10.5194/acp-12-5429-2012), 2012.
  <br/>

- Metzger, S., B. Steil, M. Abdelkader, K. Klingmüller, L. Xu, J.E. Penner, C. Fountoukis,  A. Nenes, and J. Lelieveld; "Aerosol Water Parameterization: A single parameter framework";  Atmos. Chem. Phys., 16, 7213–7237, [https://doi.org/10.5194/acp-16-7213-2016,](https://doi.org/10.5194/acp-16-7213-2016,) 2016a.
 <br/>

- Metzger, S., M. Abdelkader, K. Klingmüller,  B. Steil, and J. Lelieveld, "Comparison of Metop - PMAp Version 2 AOD Products using Model Data", EUMETSAT ITT 15/210839 [https://www.eumetsat.int/PMAP](https://www.eumetsat.int/PMAP), Validation [Report, 12/2016b](https://www-cdn.eumetsat.int/files/2020-04/pdf_pmap_v2_model_comp.pdf), Final Acceptance Review (FAR) [presentation](https://www-cdn.eumetsat.int/files/2020-04/pdf_science_cal_val_pmap_presentation.pdf).
 <br/>
 
- Metzger, S., Abdelkader, M., Steil, B., and Klingmüller, K.: "Aerosol water parameterization: long-term evaluation and importance for climate studies",  Atmos. Chem. Phys., 18, 16747–16774, [https://doi.org/10.5194/acp-18-16747-2018](https://doi.org/10.5194/acp-18-16747-2018), 2018.
 <br/>
 
- Svetlana Tsyro and Swen Metzger, contribution to the EMEP Status Report 1/2019, "Transboundary particulate matter, photo-oxidants, acidifying and eutrophying components", Joint MSC-W & CCC & CEIP Report, Chapter 9 (p133): EQSAM4clim  Report available from [https://emep.int/publ/emep2019_publications.html](https://emep.int/publ/emep2019_publications.html) (pdf 31 MB).
 <br/>
 
- B Koo, S Metzger, P Vennam, C Emery, G Wilson, G Yarwood, "Comparing the ISORROPIA and EQSAM Aerosol Thermodynamic Options in CAMx", International Technical Meeting on Air Pollution Modelling and its Application,  ITM 2018: Air Pollution Modeling and its Application XXVI pp 93-98, 2020 [https://link.springer.com/chapter/10.1007/978-3-030-22055-6_16](https://link.springer.com/chapter/10.1007/978-3-030-22055-6_16).
