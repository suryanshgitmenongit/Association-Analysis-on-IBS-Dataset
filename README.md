# Association-Analysis-on-IBS-Dataset

This document presents the results of the association analysis performed on the IBS dataset. Below is a detailed explanation of the key steps and the resulting metrics.

## 1. Dataset Preparation

- **Loading Data**: The abundance data was loaded from an Excel file named `IBS Dataset.xlsx`.
- **Normalization**: The data was normalized so that the sum of each row (sample) equals 1. This step ensures that the abundance values are relative.
- **Binarization**: The data was binarized to indicate the presence (True) or absence (False) of each bacterial taxa in each sample. This transformation is necessary for applying the Apriori algorithm.

## 2. Frequent Itemset Generation

- **Algorithm**: The Apriori algorithm was used to identify frequent itemsets, which are combinations of bacterial taxa that appear together in the dataset.
- **Support Threshold**: A minimum support threshold of 0.5 was used. This means only itemsets that appear in at least 50% of the samples are considered frequent.

### Example Frequent Itemset

| support | itemsets                                             |
|---------|------------------------------------------------------|
| 0.976608| (d__Bacteria;p__Bacteroidota;c__Bacteroidia;o_...)  |

- **Support**: Indicates the proportion of samples in which the itemset appears. For example, the itemset `(d__Bacteria;p__Bacteroidota;c__Bacteroidia;o_...)` appears in 97.66% of the samples.

## 3. Association Rule Mining

- **Metric**: The rules were generated using the `lift` metric with a minimum threshold of 1. Lift values greater than 1 indicate a positive association between the antecedent and consequent itemsets.
- **Results**: The association rules show relationships between itemsets, along with various metrics.

### Example Association Rule

| antecedents                                      | consequents                                       | support  | confidence | lift    | leverage | conviction | zhangs_metric |
|--------------------------------------------------|--------------------------------------------------|----------|------------|---------|----------|------------|---------------|
| (d__Bacteria;p__Bacteroidota;c__Bacteroidia;o_...) | (d__Bacteria;p__Firmicutes;c__Clostridia;o__La...) | 0.822612 | 0.842315   | 1.001409| 0.001157 | 1.007514   | 0.060130      |

- **Antecedents**: The itemsets on the left side of the rule.
- **Consequents**: The itemsets on the right side of the rule.
- **Support**: The proportion of samples containing the rule (both antecedent and consequent).
- **Confidence**: The proportion of samples with the antecedent that also contain the consequent.
- **Lift**: The ratio of the observed support to the expected support if the antecedent and consequent were independent. A lift value greater than 1 indicates a positive association.
- **Leverage**: The difference between the observed support and the expected support if the antecedent and consequent were independent.
- **Conviction**: A measure of the implication strength. Values greater than 1 indicate a stronger implication.
- **Zhang's Metric**: A measure to evaluate the interestingness of the rule.

