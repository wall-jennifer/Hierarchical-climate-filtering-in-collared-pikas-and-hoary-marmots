# From peaks to patches: Hierarchical climate filtering in collared pikas and hoary marmots
### Jennifer L. Wall and Jedediah F. Brodie

### Ecology
### Accepted: June 18, 2026
### Corresponding author: Jennifer Wall, jwall0602@gmail.com

## Abstract
Climate changes are amplified in boreal regions and can disproportionately impact alpine species. Yet predicting how species will respond is difficult due to a complex interplay of scale-dependent factors. For understudied taxa in relatively inaccessible boreal regions, it is particularly challenging to disentangle the drivers of species distributions. Here we utilized an integrated framework to better understand the relative importance of climate and microhabitat in shaping species distributions at different spatial scales. This framework combines landscape-scale generalized linear models of species occurrence with local-scale Bayesian causal structural equation occupancy models. We tested this approach on two understudied alpine species with differing life history strategies – collared pikas (*Ochotona collaris*) and hoary marmots (*Marmota caligata*) – in Denali National Park and Preserve, Alaska (USA). While both species are projected to be sensitive to climate change, considerable uncertainty exists regarding the specific climatic factors and underlying mechanisms driving these impacts. At the landscape scale, we modeled 63 pika and 33 marmot detections and found that species occurrence was negatively linked to warmer summers and shrub-encroachment (marmots only) and positively linked to slope, colder and wetter winters (marmots only) and stable snowpack insulation (pikas only). We incorporated these predictors into structural equation occupancy models with occurrence data from 83 sites to tease apart climatic relationships and tested additional occupancy models of microhabitat conditions. At local scales, we found support for microhabitat influencing the occurrence of pikas, with occupancy positively related to talus rock size, but an inconclusive effect of climate on pika occupancy and inconclusive support for all predictors on marmot occupancy. These results are consistent with distributions of both species being constrained by climatic factors at a landscape scale, with pikas additionally limited by local microhabitat conditions. For pikas, these hierarchical constraints highlight the importance of incorporating local, environmental conditions within broad-scale climate models and suggest that large, rocky talus may confer pikas greater resilience to climate pressures than suggested by broad-scale models alone. Overall, our study provides a versatile framework for analyzing the diverse and multi-scale impacts of climate change on species.

## Code
  1. [0.1_prior-estimation.R](/code/0.1_prior-estimation.R) Prior development and visualization of weakly informative priors.
  2. [Link to data]: Code for the simulation I ran of the various GLMs.
  3. [0.3_SEM-occupancy-simulation.Rmd](/code/0.3_SEM-occupancy-simulation.Rmd): Simulated Bayesian causal structural equation / occupancy model. This model uses multiple equations to represent relationships between observed and latent variables while simultaneously accounting for imperfect detection of species and calculates detection probabilities using 3-4 different sign types from our focal species as an alternative to repeated site visits.
  4. Collared pika *(Ochotona collaris)* models:
     
      - [1.1_COPI_climate-drivers-SEM-occupancy](code/1.1_COPI_climate-drivers-SEM-occupancy.R): Hierarchical occupancy model nested within a structural equation model with latent and observed variables.
      - [1.2_COPI_climate-filtering-occupancy](code/1.2_COPI_climate-filtering-occupancy.R): Hierarchical single-species, single-season occupancy model of local, microclimate factors.
      - [1.3_COPI_climate-drivers-SEM-occupancy-simplified](code/1.3_COPI_climate-drivers-SEM-occupancy-simplified.R): Hierarchical occupancy model nested within a structural equation model with latent and observed variables.
    
  5. Hoary marmot *(Marmota caligata)* models: 
     
      - [2.1_HOMA_climate-drivers-SEM-occupancy](code/2.1_HOMA_climate-drivers-SEM-occupancy.R): Hierarchical occupancy model nested within a structural equation model with latent and observed variables.
      - [2.2_HOMA_climate-filtering-occupancy](code/2.2_HOMA_climate-filtering-occupancy.R): Hierarchical single-species, single-season occupancy model of local, microclimate factors.
      - [2.3_HOMA_climate-drivers-SEM-occupancy-simplified](code/2.3_HOMA_climate-drivers-SEM-occupancy-simplified.R)
    
## Variables

- **slope**: Calculated from a digital elevation model from ArcticDEM (U.S. Geological Survey 2020) with 8 neighboring cells (Horn 1981).
- **max.sum.temp**: Maximum summer temperature (&deg;C), as calculated from MOD11A1 Version 6.1 daily Land Surface Temperature between May to August.
- **days.above.21**: Total summer days above 21&deg;C, as calculated from MOD11A1 Version 6.1 daily Land Surface Temperature between May to August.
- **min.wint**: Minimum winter temperature (&deg;C), as calculated from MOD11A1 Version 6.1 daily Land Surface Temperature between October of the previous year to March.
- **wint.days.below.neg5**: Total winter days below -5&deg;C, as calculated from MOD11A1 Version 6.1 daily Land Surface Temperature between October of the previous year to March.
- **wint.days.above.0**: Total winter days above 0&deg;C, as calculated from MOD11A1 Version 6.1 daily Land Surface Temperature between October of the previous year to March.
- **ros**: Total number of days with rain-on-snow events, as calculated from SnowModel where the 10 year average daily rainfall is ≥ 3mm on snow depths ≥ 1.5 cm.
- **snow.dens**: Average snow density (kg/m<sup>3</sup>), as calculated from the 10 year average SnowModel data between September of the previous year to April.
- **snow.depth**: Maximum snow depth (m), as calculated from the 10 year average SnowModel data between September of the previous year to April.
- **perm**: Continuous probability (%) of near-surface permafrost, based on models by Pastick 4326.
- **evi**: Average summer greenness from the previous summer, as measured via the enhanced vegetation index and calculated from MOD13Q1 v061 16-day EVI between June – August.
