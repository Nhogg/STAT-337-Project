# Beta-Poisson Transmission Model: Application to Hong Kong COVID-19 Data
## STAT 337/437 - Quantitative Bioinformatics Project
### Overview
This project applied the methods from Hilton & Hall (2024), "A beta-Poisson model for infectious disease transmission" (PLOS Computational Biology), to a new dataset of COVID-19 transmission pairs from Hong Kong.

We fit five offspring distributions - Poisson, geometric, negative binomial, zero-inflated Poisson (ZIP), and beta-Poisson - to secondary case data and compare their performance using maximum likelihood estimation, Akaike Information Criterion (AIC), and epidemiological metrics including overdispersion, superspreading prevalence, and proportion of zero-transmission cases.

### Paper
Hilton J, Hall I (2024). A beta-Poisson model for infectious disease transmission. PLoS Comput Biol 20(2): e1011856. https://doi.org/10.1371/journal.pcbi.1011856

### Dataset
Adam DC et al. (2020). Clustering and superspreading potential of SARS-CoV-2 infections in Hong Kong. Nature Medicine 26: 1714–1719. https://doi.org/10.1038/s41591-020-1092-0

- Location: Hong Kong
- Period: January 23 – April 28, 2020
- Cases: 1,038 laboratory-confirmed SARS-CoV-2 cases
- Transmission pairs: 169 unique infector–infectee pairs from contact tracing
- Data file: `transmission_pairs.csv`

### Methods
| Model                 | Parameters                                              | Estimation       |
|-----------------------|---------------------------------------------------------|------------------|
| Poisson               | $\lambda$ (mean)                                        | Closed-form MLE  |
| Geometric             | $\lambda$ (mean)                                        | Closed-form MLE  |
| Negative Binomial     | $\lambda$ (mean) $\theta$ (overdispersion)              | MLE via BFGS     |
| Zero-Inflated Poisson | $\lambda$ (Poisson mean), $\theta$ (zero-inflation)     | MLE via L-BFGS-B |
| Beta-Poisson          | $\lambda$ (mean) $\phi$ (overdispersion) $N$ (contacts) | MLE via L-BFGS-B |

