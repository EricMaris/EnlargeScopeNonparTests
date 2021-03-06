# Simulation studies for investigating FA-rate control of randomization tests in studies with a within-participant manipulation of the explanatory variable (one-sample t-test)

We will run two types of simulation studies in which we will use different datasets: (1) resting state data, and (2) data with effects at the single-participant level. For both data sets, the random effect null hypothesis (formulated in terms of statistical independence) holds. For data set 1, there are no effects at the single-participant level, whereas for data set 2, these effects do exist (but cancel out across participants).

Data set 1 is the Oulu data set used that was used by Eklund et al (2016). The motivation for this is that the simulations by Eklund et al showed that the FA rate was not controlled for this data set, neither using their implementation of the permutation test using sign-flipping, nor using the parametric statistical test implemented in SPM. 

Data set 2 will be generated from an existing data set with a two-condition event-related design. For every observed participant, we will estimate the HRF amplitudes for the two conditions, and will use these estimated HRF amplitudes to generate data for two simulated participants. Every pair of simulated participants differs with respect to the order of the HRF amplitudes across the two conditions: for one simulated participant condition 1 has the highest HRF amplitude, and for the other simulated participant this is condition 2. For data that are simulated in this way, the random effect null hypothesis holds.

 
## Analyses of data set 1

Data set 1 will be analyzed in four different ways: two nonparametric analyses, and two parametric ones. The two nonparametric analyses are the following: (1) the analysis performed by Eklund et al (2016), and (2) the analysis prescribed by the theoretical paper on randomization tests. The difference between these two analyses pertains to the regression coefficient contrast that is tested against 0. Specifically, in Eklund et al, this regression coefficient contrast is based on a GLM analysis in which only a single event is coded (but represented by two columns in the design matrix, the HRF and its first derivative). Thresholding and clustering is performed on the basis of the one-sample t-statistic for the HRF regression coefficient. (Strictly speaking, a single regression coefficient is not a contrast, because it does not involve a comparison with one or more other conditions.)

For our randomization test, we will use a different GLM analysis. Specifically, our GLM analysis is based on a design matrix in which two events are coded: (1) the presentation of a stimulus of which we want to evaluate the neuronal effect, and (2) the absence of such a stimulus. Thus, we consider a so-called activation study as a study with experimental conditions, of which the second corresponds to the absence of a stimulus. This conceptual difference with Eklund et al (2016) has a consequence for the GLM design matrix: in our GLM design matrix, we explicitly code the absence of a stimulus with two additional columns, one for the HRF, and one for its first derivative. Thresholding and clustering is performed on the basis of the one-sample t-statistic for the HRF regression coefficient contrast between the two conditions (stimulus versus no stimulus). This is a genuine contrast. Note that, with this contrast, randomly switching between two complementary condition orders (e.g., ABABABBA vs BABABAAB) is equivalent to sign-flipping.

The empirical FA rate of both non-parametric statistical tests will be evaluated for the following cluster-defining thresholds: 0.05, 0.01, 0.001. Note that, as compared to Eklund et al (2016), we have added the 0.05 threshold, which allows to detect weak but widespreac effects.

We will also perform the two corresponding parametric statistical tests using the SPM package. For the GLM design matrix used by Eklund et al (2016), this is a replication, but for the GLM design matrix that is used in our randomization test, this is not. 



