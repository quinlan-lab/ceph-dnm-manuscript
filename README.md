## Large, three-generation CEPH families reveal post-zygotic mosaicism and variability in germline mutation accumulation

### Thomas A. Sasani, Brent S. Pedersen, Ziyue Gao, Lisa M. Baird, Molly Przeworski, Lynn B. Jorde, Aaron R. Quinlan

This repository contains the necessary **Jupyter Notebooks and data files to reproduce figures in the manuscript (also see the link to a Binder environment below)**. 

Below is an example figure from the MS, which summarizes our finding that the paternal age effect on DNM counts significantly differs between CEPH families. This figure can be created (in multiple parts) using this repository.

![alt text](img/fig3.png)

Two notebooks, `ms_figs.R.ipynb` and `ms_figs.python.ipynb`, can be used to reproduce figures from the manuscript. A notebook called `inter-family-variability.ipynb` can be used to reproduce the statistical analyses associated with inter-family variability in parental age effects. Finally, figures presented in the main response to reviewers can be reproduced using `response_figures.ipynb`. Figures in the manuscript were generated with the versions of each library listed below, though more recent versions (if applicable) will likely work, as well. 

To mitigate compatability/version issues, we have **packaged all notebooks into a [binder](mybinder.org) environment**; to access the environment, **simply click on the badge below**. It might take a minute to load everything.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/quinlan-lab/ceph-dnm-manuscript/master)

The files included in the `data` directory are organized as follows:

`second_gen.dnms.txt` and `third_gen.dnms.txt` contain a row for every DNM identified in the second or third generation, respectively. `gonosomal.dnms.txt` and `post-pgcs.dnms.txt` contain a row for every DNM identified as being gonosomal or a post-PGCS mosaic mutation, respectively. Each row in these files is formatted like a heavily annotated BED entry, where the first three columns indicate the chromosome, start position, and end position of the variant, followed by additional columns with per-variant information, such as the reference and alternate alleles, depth and genotype qualities in the proband and parents, etc. **All coordinates are with respect to GRCh37**.

For example, the first few lines of `second_gen.dnms.txt` are shown below:

```
chrom	start	end	new_sample_id	new_family_id	ref	alt	mut	new_paternal_id	new_maternal_id	kid_ref_depth	kid_alt_depth	kid_total_depth	kid_allele_balance	mom_ref_depth	mom_alt_depth	mom_total_depth	dad_ref_depth	dad_alt_depth	dad_total_depth	kid_qual	mom_qual	dad_qual	paternal_age_at_birth	maternal_age_at_birth	phase
1	1142254	1142255	538	29	G	A	CpG>TpG	544	543	17	15	32	0.46875	24	0	24	35	0	35	99.0	63.0	99.0	32.69999999999999	27.0	paternal
1	1461136	1461137	257	16	G	C	C>G	261	263	12	17	29	0.5862068965517241	27	0	27	45	0	45	99.0	81.0	81.0	30.800000000000008	22.0	paternal
```

`second_gen.dnms.summary.csv`, `third_gen.dnms.summary.csv`, `gonosomal.dnms.summary.csv`, and `post-pgcs.dnms.summary.csv` are summary CSV files, and contain a row for every sample in the second, third, second (again, but for the gonosomal DNMs), and third (again, but for the post-PGCS DNMs) generations, respectively. Each row contains summary information about the sample, including the total number of DNMs identified, the numbers that were phased to either parental allele, the callable autosomal fraction in the sample, etc. 

For example, the first few lines of `second_gen.dnms.summary.csv` is shown below:

```
all_dnms,alpha,autosomal_callable_fraction,autosomal_dnms,dad_age,dad_dnms,dad_dnms_auto,dad_dnms_auto_snv,dad_dnms_snv,family_id,maternal_id,mom_age,mom_dnms,mom_dnms_auto,mom_dnms_auto_snv,mom_dnms_snv,n_children,n_sibs,paternal_id,phased_frac,sample_id,snv_autosomal_dnms,snv_dnms,mean_depth
57.0,0.6545454545454545,2587148570.0,57.0,22.8,36.0,36.0,34.0,17.0,20,329,21.599999999999994,19.0,19.0,17.0,17.0,9.0,1.0,330,0.9649122807017544,328,52.0,52.0,36.822442140553065
86.0,0.8604651162790697,2560784557.0,86.0,30.800000000000008,74.0,74.0,69.0,11.0,16,263,22.0,12.0,12.0,11.0,11.0,9.0,1.0,261,1.0,257,80.0,80.0,33.838202333693275
```

#### Dependencies (if **not** using the Binder environment provided above)

#### For `python 3.7.3`:

`scipy v1.2.1`

`seaborn v0.9.0`

`matplotlib v2.2.3`

`numpy v1.16.2`

`pandas 0.24.2`

`statsmodels v0.9.0`

#### For `R 3.4.4`:

`ggplot2 v3.1.0`

`cowplot v0.9.3`

`ggridges v0.5.1`

`viridis v0.5.1`

#### Installation (if **not** using the Binder environment provided above)

Simply clone the repository and run a notebook as follows:

```
git clone https://github.com/tomsasani/ceph-dnm-manuscript

cd ceph-dnm-manuscript/notebooks

jupyter lab ms_figs.R.ipynb

jupyter lab ms_figs.python.ipynb

jupyter lab inter-family-variability.ipynb
```
