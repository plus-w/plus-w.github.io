+++
title = 'Research Log 2025 04'
date = 2025-04-17T14:12:08+08:00
draft = true
+++

## Summary

## 04.14
Scanned papers about VLP and self-assembly, a quick overview, found that many are not related with proteins, few of them are machine-learning works of even data-driven works. Review papers summarized roles of AI in this topic, but no significant work found. A recent theorectical work on Physics Review X is interesting but limited, may require further investigate to find possible inspirations. Baker's team has some works about designing protein cage and such architecture, but I guess these works are using AI for story telling, it might not actualy work.

## 04.15

Evaluated MLDE simulation with DPO on 7 indels datasets of ProteinGym using only deletion data, results proved the effectiveness. The base model is 8M, future works are replacing it with 650M model and comparing result with vanilla training.

For 6HWX structures, remove two outer circles of chains, structure of the left part highly matches those predicted by AF3 and Chai-1. Maybe we can use these predicted structures of polymers as model input.

Calculated the attentions for eVLP DMS data using 650M model, further analysis and calculation using ESM-IF are required. The key is to find whether the binding sites/regions can be discovered.

Checked the algorithms that ProteinGym applied for scoring(zero-shot) mutants with PLM. 
- Pseudo-perplexity
- WT-marginal
- Masked-marginal.

Drawed a draft of overview figure of MiniCas9, discussed with Chen. Obtained first batch of wetlab results of 1-order samples for the 1st round, and results are decent.

## 04.16

Calculated correlation between eVLP DMS and 4 types of ESM zero-shot scores, not correlated.

Running predictions for sacas9 deletion variants with 650M ESM2 trained on ngs data (oldmerged_o10x).

## 04.17

Predicted all deletion variants for sacas9 with 650M model

## 04.18

Visualized predictions for sacas9 deletion variants

Select top 100 common samples of sacas9 predictions, delete regions are short.

Running predictions for ascas12a deletion variants with 650M ESM2 trained on ngs data (oldmerged_o10x).

Wrote appendix outline for AuraBind

Tried to deploy progen3

Installed cudatoolkit-12.4.0 on 10.11.16.180

## 04.21

DPO fine-tuning on 1st round of wet-lab data

Benchmarking ProteinGym simulated directed evolution with 8M model

Determine methods to calculate PLM zero-shot score

## 04.22

Get 2nd round of wet-lab samples

Prepare group meet ppt

## 04.23

Group meet

discuss ascas12a and sacas9 design

a new project: mini gene editor design

## 04.24

