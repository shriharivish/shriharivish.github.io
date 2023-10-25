---
layout: page
title: mirtargetbenchmark
description: R package aimed towards benchmarking miRNA target prediction tools
img: assets/img/gt_binding_sites.png
importance: 3
category: fun
---

There are different types of cells in our body even though they have the same genetic material.
This happens because different proteins are synthesized inside these cells in different amounts.
The difference in the amount of proteins is due to regulation in the amount of messenger RNAs
during the process of protein synthesis in the cells. One such type of regulation is caused by
microRNAs (miRNAs). miRNAs bind to the messenger RNAs and lead to their degradation
causing repression. There are various tools which use the sequence information of miRNAs and
mRNAs to predict the miRNA targets.

These tools result in a lot of false positives, presumably because they are not condition-specific
or tissue-specific. Since there is no universal standard to benchmark these tools, we have
evaluated these tools by creating regression models on gene and miRNA expression data from
specific conditions like breast cancer and pan-cancer and compared the predictions from
various tools like TargetScan, mircode, miRWalk, miRDB, PITA miRTarBase and miRanda,
against the results from regression models built on the combined miRNA-gene expression data.
Two approaches were used for benchmarking. In the first approach, binarized regression
coefficients were compared with binarized binding sites. The tools used in this approach were
TargetScan, miRcode, miRTarBase and miRTarBase7. In the second approach, the binarized
regression coefficients were compared with the binarized confidence scores. The tools used in
this approach were TargetScan, miRanda, miRWalk, miRDB and PITA. An ensemble method
was also developed for target prediction by combining the scores from all the tools.
We observed that TargetScan had slightly higher precision and miRcode had significantly better
sensitivity and worse specificity than other tools in the first approach discussed above. In the
results obtained by using the second approach and comparing the coefficients from ridge
regression with the confidence scores, we observed that the precision of miRDB was overall the
highest and increased steadily from low to high confidence scores. The miRDB scoring method
was thus the only one with a continuous behavior.

A package called <a href="https://github.com/biomedbigdata/mirtargetbenchmark">‘mirtargetbenchmark’</a> was developed which provides functionalities for both
approaches mentioned above. It also provides functionalities for filtering the expression data,
organizing the tool predictions into a matrix, converting the gene/miRNA annotations into
desired format, choosing miRNAs which have a lot of interactions in online databases
containing experimentally validated interactions and ensemble method which provides target
predictions.



<div class="img">
        {% include figure.html path="assets/img/gt_binding_sites.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Approach 1 (GT vs Binding Sites)
</div>

<div class="img">
        {% include figure.html path="assets/img/gt_cs.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
<div class="caption">
    Approach 2 (GT vs Confidence Scores)
</div>