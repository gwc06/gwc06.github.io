# hw 2.1
## 1     
* input  
```
wc -l test_command.gtf
```  
* output  
```
8 test_command.gtf
```
* input  
```
wc -c test_command.gtf
```
* output  
```
636 test_command.gtf
```
## 2
* input
```
grep 'chr_' test_command.gtf | grep 'YDL248W'
```
* output
```
chr_IV  ensembl gene    1802    2953    .       +       .       gene_id "YDL248W"; gene_version "1";
chr_IV  ensembl transcript      802     2953    .       +       .       gene_id "YDL248W"; gene_version "1";
chr_IV  ensembl start_codon     1802    1804    .       +       0       gene_id "YDL248W"; gene_version "1";
```
* input
```
cut -f 1,3,4,5 test_command.gtf | sed 's/chr_/chromosome/g'
```
* output
```
chromosomeIV    gene    1802    2953
chromosomeIV    transcript      802     2953
chromosome_IV   exon    1802    2953
chromosome_IV   CDS     1802    950
chromosomeIV    start_codon     1802    1804
chromosome_IV   stop_codon      2951    2953
chromosome_IV   gene    762     3836
chromosomeIV    transcript      3762    836
```
## 3
* input
```
sort -k 4 -k 5 -n test_command.gtf | awk -F '\t' -v OFS='\t' '{ a=$2; $2=$3; $3=a; print}' > result.gtf
```
* output: 无直接输出，输出文件result.gtf的内容为
```
chromosome_IV	gene	ensembl	762	3836	.	+	.	gene_id "YDL247W-A"; gene_version "1";
chr_IV	transcript	ensembl	802	2953	.	+	.	gene_id "YDL248W"; gene_version "1";
chromosome_IV	CDS	ensembl	1802	950	.	+	0	gene_id "YDL248W"; gene_version "1";
chr_IV	start_codon	ensembl	1802	1804	.	+	0	gene_id "YDL248W"; gene_version "1";
chr_IV	gene	ensembl	1802	2953	.	+	.	gene_id "YDL248W"; gene_version "1";
chromosome_IV	exon	ensembl	1802	2953	.	+	.	gene_id "YDL248W"; gene_version "1";
chromosome_IV	stop_codon	ensembl	2951	2953	.	+	0	gene_id "YDL248W"; gene_version "1";
chr_IV	transcript	ensembl	3762	836	.	+	.	gene_id "YDL247W-A"; gene_version "1";
```
## 4
* input
```
ls -l test_command.gtf
```
* output
```
-rwxrwxrwx 1 root root 636 Mar  8 08:57 test_command.gtf
```
* input
```
chmod 774 test_command.gtf
ls -l test_command.gtf
```
* output
```
-rwxrwxr-- 1 root root 636 Mar  8 08:57 test_command.gtf
```
