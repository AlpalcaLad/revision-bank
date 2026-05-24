### Evaluation 
![[Pasted image 20260523000733.png]]

Mathews correlation coefficient
$MCC =\frac{TP \times TN - FP \times FN}{\sqrt{(TP+FP)(TP+FN)(TN+FP)(TN+FN)}}$

Cohen's Kappa coefficient, do annotators A1 and A2 agree
$\kappa=\frac{P(a)-P(e)}{1-P(e)}$
$P(a)=P(A1=Yes,A2=Yes)+P(A1=No,A2=No)$
$P(e)=P(A1=Yes)*P(A2=Yes)+P(A1=No)*P(A2=No)$

Precision
P = TP/ (TP + FP)

Recall
R = TP/(TP + FN)

F-score
$F_\beta=\frac{(\beta^2+1)PR}{((\beta^2P)+R)}$
Typically beta is 1 so
$F_1=\frac{2PR}{P+R}$

Macro-averaging
Averages are calculated after formula

weighted macro-averaging
averages after formula where f1 scores are multiplies by proportion of samples it represents

micro-averaging
averages are calculated before formula
### Word meaning
$Term freq=tf_{t,d}=log(count(t,d) + 1)$

$InvDocFreq=log_{10}(N/df_t)$  where $N$ is doc number and $df_t$ is number of docs with term t

$PMI(w,c)=log_2\frac{P(w,c)}{P(w)P(c)}$

$PPMI(w,c)=max(PMI(w,c),0)$

Max likelihood estimation:
![[Pasted image 20260521133635.png|586]]

### Neural nets
Cross entropy loss, these are the same because the correct probs are all 0 except 1, so are ignored in the sum.
$L_{CE}(\hat{y},y)=-\sum_{k=1}^{K}{y_klog(\hat{y_k})}$  where $y$ is gold standard, $\hat{y}$ is predicted
$L_{CE}(\hat{y},y)=-log(\hat{y_c})$   where c is the correct word

### Sequence-to-sequence
Blue-N
$sum(min(count_{hypothesis},count_{reference}))/hypothesis_{num}$
