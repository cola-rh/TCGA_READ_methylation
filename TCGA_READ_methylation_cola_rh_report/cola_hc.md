cola Report for Hierarchical Partitioning - 'TCGA_READ_methylation'
==================

**Date**: 2021-07-22 16:12:24 CEST, **cola version**: 1.9.4

----------------------------------------------------------------

<style type='text/css'>

body, td, th {
   font-family: Arial,Helvetica,sans-serif;
   background-color: white;
   font-size: 13px;
  max-width: 800px;
  margin: auto;
  margin-left:210px;
  padding: 0px 10px 0px 10px;
  border-left: 1px solid #EEEEEE;
  line-height: 150%;
}

tt, code, pre {
   font-family: 'DejaVu Sans Mono', 'Droid Sans Mono', 'Lucida Console', Consolas, Monaco, 

monospace;
}

h1 {
   font-size:2.2em;
}

h2 {
   font-size:1.8em;
}

h3 {
   font-size:1.4em;
}

h4 {
   font-size:1.0em;
}

h5 {
   font-size:0.9em;
}

h6 {
   font-size:0.8em;
}

a {
  text-decoration: none;
  color: #0366d6;
}

a:hover {
  text-decoration: underline;
}

a:visited {
   color: #0366d6;
}

pre, img {
  max-width: 100%;
}
pre {
  overflow-x: auto;
}
pre code {
   display: block; padding: 0.5em;
}

code {
  font-size: 92%;
  border: 1px solid #ccc;
}

code[class] {
  background-color: #F8F8F8;
}

table, td, th {
  border: 1px solid #ccc;
}

blockquote {
   color:#666666;
   margin:0;
   padding-left: 1em;
   border-left: 0.5em #EEE solid;
}

hr {
   height: 0px;
   border-bottom: none;
   border-top-width: thin;
   border-top-style: dotted;
   border-top-color: #999999;
}

@media print {
   * {
      background: transparent !important;
      color: black !important;
      filter:none !important;
      -ms-filter: none !important;
   }

   body {
      font-size:12pt;
      max-width:100%;
   }

   a, a:visited {
      text-decoration: underline;
   }

   hr {
      visibility: hidden;
      page-break-before: always;
   }

   pre, blockquote {
      padding-right: 1em;
      page-break-inside: avoid;
   }

   tr, img {
      page-break-inside: avoid;
   }

   img {
      max-width: 100% !important;
   }

   @page :left {
      margin: 15mm 20mm 15mm 10mm;
   }

   @page :right {
      margin: 15mm 10mm 15mm 20mm;
   }

   p, h2, h3 {
      orphans: 3; widows: 3;
   }

   h2, h3 {
      page-break-after: avoid;
   }
}
</style>




## Summary



First the variable is renamed to `res_rh`.


```r
res_rh = rh
```



The partition hierarchy and all available functions which can be applied to `res_rh` object.


```r
res_rh
```

```
#> A 'HierarchicalPartition' object with 4 combinations of top-value methods and partitioning methods.
#>   On a matrix with 375746 rows and 106 columns.
#>   Performed in total 32200 partitions.
#>   There are 15 groups under the following parameters:
#>     - min_samples: 6
#>     - mean_silhouette_cutoff: 0.9
#>     - min_n_signatures: 1000 (signatures are selected based on:)
#>       - fdr_cutoff: 0.05
#>       - group_diff: 0.25
#> 
#> Hierarchy of the partition:
#>   0, 106 cols
#>   |-- 01, 32 cols, 14315 signatures
#>   |   |-- 011, 18 cols, 3371 signatures
#>   |   |   |-- 0111, 12 cols, 15 signatures (c)
#>   |   |   |-- 0112, 3 cols (b)
#>   |   |   `-- 0113, 3 cols (b)
#>   |   |-- 012, 9 cols (b)
#>   |   `-- 013, 5 cols (b)
#>   |-- 02, 27 cols, 14944 signatures
#>   |   |-- 021, 7 cols (b)
#>   |   |-- 022, 14 cols, 139 signatures (c)
#>   |   `-- 023, 6 cols (b)
#>   `-- 03, 47 cols, 3210 signatures
#>       |-- 031, 15 cols, 2183 signatures
#>       |   |-- 0311, 9 cols (b)
#>       |   `-- 0312, 6 cols (b)
#>       `-- 032, 32 cols, 3794 signatures
#>           |-- 0321, 8 cols (b)
#>           |-- 0322, 14 cols, 1217 signatures
#>           |   |-- 03221, 4 cols (b)
#>           |   `-- 03222, 10 cols (b)
#>           |-- 0323, 8 cols (b)
#>           `-- 0324, 2 cols (b)
#> Stop reason:
#>   b) Subgroup had too few columns.
#>   c) There were too few signatures.
#> 
#> Following methods can be applied to this 'HierarchicalPartition' object:
#>  [1] "all_leaves"            "all_nodes"             "cola_report"           "collect_classes"      
#>  [5] "colnames"              "compare_signatures"    "dimension_reduction"   "functional_enrichment"
#>  [9] "get_anno_col"          "get_anno"              "get_children_nodes"    "get_classes"          
#> [13] "get_matrix"            "get_signatures"        "is_leaf_node"          "max_depth"            
#> [17] "merge_node"            "ncol"                  "node_info"             "node_level"           
#> [21] "nrow"                  "rownames"              "show"                  "split_node"           
#> [25] "suggest_best_k"        "test_to_known_factors" "top_rows_heatmap"      "top_rows_overlap"     
#> 
#> You can get result for a single node by e.g. object["01"]
```

The call of `hierarchical_partition()` was:


```
#> hierarchical_partition(data = mat, top_n = 1000, top_value_method = c("SD", "ATC"), 
#>     partition_method = c("kmeans", "skmeans"), subset = 500, group_diff = 0.25, min_n_signatures = 1000, 
#>     filter_fun = function(mat) {
#>         s = rowSds(mat)
#>         order(-s)[1:30000]
#>     }, max_k = 8, scale_rows = FALSE, cores = 4)
```

Dimension of the input matrix:


```r
mat = get_matrix(res_rh)
dim(mat)
```

```
#> [1] 375746    106
```

All the methods that were tried:


```r
res_rh@param$combination_method
```

```
#> [[1]]
#> [1] "SD"     "kmeans"
#> 
#> [[2]]
#> [1] "ATC"    "kmeans"
#> 
#> [[3]]
#> [1] "SD"      "skmeans"
#> 
#> [[4]]
#> [1] "ATC"     "skmeans"
```

### Density distribution

The density distribution for each sample is visualized as one column in the following heatmap.
The clustering is based on the distance which is the Kolmogorov-Smirnov statistic between two distributions.




```r
library(ComplexHeatmap)
densityHeatmap(mat, ylab = "value", cluster_columns = TRUE, show_column_names = FALSE,
    mc.cores = 1)
```

![plot of chunk density-heatmap](figure_cola/density-heatmap-1.png)



Some values about the hierarchy:


```r
all_nodes(res_rh)
```

```
#>  [1] "0"     "01"    "011"   "0111"  "0112"  "0113"  "012"   "013"   "02"    "021"   "022"   "023"  
#> [13] "03"    "031"   "0311"  "0312"  "032"   "0321"  "0322"  "03221" "03222" "0323"  "0324"
```

```r
all_leaves(res_rh)
```

```
#>  [1] "0111"  "0112"  "0113"  "012"   "013"   "021"   "022"   "023"   "0311"  "0312"  "0321"  "03221"
#> [13] "03222" "0323"  "0324"
```

```r
node_info(res_rh)
```

```
#>       id best_method depth best_k n_columns n_signatures p_signatures is_leaf
#> 1      0  ATC:kmeans     1      3       106        24376     6.49e-02   FALSE
#> 2     01  ATC:kmeans     2      3        32        14315     3.81e-02   FALSE
#> 3    011 ATC:skmeans     3      3        18         3371     8.97e-03   FALSE
#> 4   0111 ATC:skmeans     4      2        12           15     3.99e-05    TRUE
#> 5   0112 not applied     4     NA         3           NA           NA    TRUE
#> 6   0113 not applied     4     NA         3           NA           NA    TRUE
#> 7    012 not applied     3     NA         9           NA           NA    TRUE
#> 8    013 not applied     3     NA         5           NA           NA    TRUE
#> 9     02  SD:skmeans     2      3        27        14944     3.98e-02   FALSE
#> 10   021 not applied     3     NA         7           NA           NA    TRUE
#> 11   022 ATC:skmeans     3      2        14          139     3.70e-04    TRUE
#> 12   023 not applied     3     NA         6           NA           NA    TRUE
#> 13    03  SD:skmeans     2      2        47         3210     8.54e-03   FALSE
#> 14   031  ATC:kmeans     3      2        15         2183     5.81e-03   FALSE
#> 15  0311 not applied     4     NA         9           NA           NA    TRUE
#> 16  0312 not applied     4     NA         6           NA           NA    TRUE
#> 17   032 ATC:skmeans     3      4        32         3794     1.01e-02   FALSE
#> 18  0321 not applied     4     NA         8           NA           NA    TRUE
#> 19  0322 ATC:skmeans     4      2        14         1217     3.24e-03   FALSE
#> 20 03221 not applied     5     NA         4           NA           NA    TRUE
#> 21 03222 not applied     5     NA        10           NA           NA    TRUE
#> 22  0323 not applied     4     NA         8           NA           NA    TRUE
#> 23  0324 not applied     4     NA         2           NA           NA    TRUE
```

In the output from `node_info()`, there are the following columns:

- `id`: The node id.
- `best_method`: The best method selected.
- `depth`: Depth of the node in the hierarchy.
- `best_k`: Best number of groups of the partition on that node.
- `n_columns`: Number of columns in the submatrix.
- `n_signatures`: Number of signatures with the `best_k`.
- `p_signatures`: Proportion of hte signatures in total number of rows in the matrix.
- `is_leaf`: Whether the node is a leaf.

Labels of nodes are encoded in a special way. The number of digits
correspond to the depth of the node in the hierarchy and the value of the
digits correspond to the index of the subgroup in the current node, E.g. a label
of “012” means the node is the second subgroup of the partition which is the
first subgroup of the root node.

### Suggest the best k



Following table shows the best `k` (number of partitions) for each node in the
partition hierarchy. Clicking on the node name in the table goes to the
corresponding section for the partitioning on that node.

[The cola vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13)
explains the definition of the metrics used for determining the best
number of partitions.



```r
suggest_best_k(res_rh)
```


|Node                  |Best method                                         |Is leaf   |Best k |1-PAC |Mean silhouette |Concordance | #samples|   |
|:---------------------|:---------------------------------------------------|:---------|:------|:-----|:---------------|:-----------|--------:|:--|
|[Node0](#Node0)       |ATC:kmeans                                          |          |3      |1.00  |0.98            |0.99        |      106|** |
|[Node01](#Node01)     |ATC:kmeans                                          |          |3      |1.00  |1.00            |1.00        |       32|** |
|[Node011](#Node011)   |ATC:skmeans                                         |          |3      |1.00  |0.99            |1.00        |       18|** |
|Node0111-leaf         |ATC:skmeans                                         |✓ (&#99;) |8      |0.95  |0.48            |0.99        |       12|** |
|Node0112-leaf         |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        3|   |
|Node0113-leaf         |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        3|   |
|Node012-leaf          |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        9|   |
|Node013-leaf          |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        5|   |
|[Node02](#Node02)     |SD:skmeans                                          |          |5      |0.90  |0.86            |0.94        |       27|*  |
|Node021-leaf          |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        7|   |
|Node022-leaf          |ATC:skmeans                                         |✓ (&#99;) |7      |0.90  |0.68            |0.95        |       14|*  |
|Node023-leaf          |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        6|   |
|[Node03](#Node03)     |SD:skmeans                                          |          |2      |1.00  |0.97            |0.98        |       47|** |
|[Node031](#Node031)   |ATC:kmeans                                          |          |2      |1.00  |1.00            |1.00        |       15|** |
|Node0311-leaf         |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        9|   |
|Node0312-leaf         |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        6|   |
|[Node032](#Node032)   |ATC:skmeans                                         |          |4      |0.94  |0.98            |0.97        |       32|*  |
|Node0321-leaf         |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        8|   |
|[Node0322](#Node0322) |ATC:skmeans                                         |          |2      |1.00  |1.00            |1.00        |       14|** |
|Node03221-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        4|   |
|Node03222-leaf        |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |       10|   |
|Node0323-leaf         |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        8|   |
|Node0324-leaf         |<span style='color:grey;'><i>not applied</i></span> |✓ (b)     |       |      |                |            |        2|   |


Stop reason: b) Subgroup had too few columns. c) There were too few signatures. 

\*\*: 1-PAC > 0.95, \*: 1-PAC > 0.9


### Partition hierarchy

The nodes of the hierarchy can be merged by setting the `merge_node` parameters. Here we 
control the hierarchy with the `min_n_signatures` parameter. The value of `min_n_signatures` is
from `node_info()`.





<style type='text/css'>



.ui-helper-hidden {
	display: none;
}
.ui-helper-hidden-accessible {
	border: 0;
	clip: rect(0 0 0 0);
	height: 1px;
	margin: -1px;
	overflow: hidden;
	padding: 0;
	position: absolute;
	width: 1px;
}
.ui-helper-reset {
	margin: 0;
	padding: 0;
	border: 0;
	outline: 0;
	line-height: 1.3;
	text-decoration: none;
	font-size: 100%;
	list-style: none;
}
.ui-helper-clearfix:before,
.ui-helper-clearfix:after {
	content: "";
	display: table;
	border-collapse: collapse;
}
.ui-helper-clearfix:after {
	clear: both;
}
.ui-helper-zfix {
	width: 100%;
	height: 100%;
	top: 0;
	left: 0;
	position: absolute;
	opacity: 0;
	filter:Alpha(Opacity=0); 
}

.ui-front {
	z-index: 100;
}



.ui-state-disabled {
	cursor: default !important;
	pointer-events: none;
}



.ui-icon {
	display: inline-block;
	vertical-align: middle;
	margin-top: -.25em;
	position: relative;
	text-indent: -99999px;
	overflow: hidden;
	background-repeat: no-repeat;
}

.ui-widget-icon-block {
	left: 50%;
	margin-left: -8px;
	display: block;
}




.ui-widget-overlay {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}
.ui-accordion .ui-accordion-header {
	display: block;
	cursor: pointer;
	position: relative;
	margin: 2px 0 0 0;
	padding: .5em .5em .5em .7em;
	font-size: 100%;
}
.ui-accordion .ui-accordion-content {
	padding: 1em 2.2em;
	border-top: 0;
	overflow: auto;
}
.ui-autocomplete {
	position: absolute;
	top: 0;
	left: 0;
	cursor: default;
}
.ui-menu {
	list-style: none;
	padding: 0;
	margin: 0;
	display: block;
	outline: 0;
}
.ui-menu .ui-menu {
	position: absolute;
}
.ui-menu .ui-menu-item {
	margin: 0;
	cursor: pointer;
	
	list-style-image: url("data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7");
}
.ui-menu .ui-menu-item-wrapper {
	position: relative;
	padding: 3px 1em 3px .4em;
}
.ui-menu .ui-menu-divider {
	margin: 5px 0;
	height: 0;
	font-size: 0;
	line-height: 0;
	border-width: 1px 0 0 0;
}
.ui-menu .ui-state-focus,
.ui-menu .ui-state-active {
	margin: -1px;
}


.ui-menu-icons {
	position: relative;
}
.ui-menu-icons .ui-menu-item-wrapper {
	padding-left: 2em;
}


.ui-menu .ui-icon {
	position: absolute;
	top: 0;
	bottom: 0;
	left: .2em;
	margin: auto 0;
}


.ui-menu .ui-menu-icon {
	left: auto;
	right: 0;
}
.ui-button {
	padding: .4em 1em;
	display: inline-block;
	position: relative;
	line-height: normal;
	margin-right: .1em;
	cursor: pointer;
	vertical-align: middle;
	text-align: center;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;

	
	overflow: visible;
}

.ui-button,
.ui-button:link,
.ui-button:visited,
.ui-button:hover,
.ui-button:active {
	text-decoration: none;
}


.ui-button-icon-only {
	width: 2em;
	box-sizing: border-box;
	text-indent: -9999px;
	white-space: nowrap;
}


input.ui-button.ui-button-icon-only {
	text-indent: 0;
}


.ui-button-icon-only .ui-icon {
	position: absolute;
	top: 50%;
	left: 50%;
	margin-top: -8px;
	margin-left: -8px;
}

.ui-button.ui-icon-notext .ui-icon {
	padding: 0;
	width: 2.1em;
	height: 2.1em;
	text-indent: -9999px;
	white-space: nowrap;

}

input.ui-button.ui-icon-notext .ui-icon {
	width: auto;
	height: auto;
	text-indent: 0;
	white-space: normal;
	padding: .4em 1em;
}



input.ui-button::-moz-focus-inner,
button.ui-button::-moz-focus-inner {
	border: 0;
	padding: 0;
}
.ui-controlgroup {
	vertical-align: middle;
	display: inline-block;
}
.ui-controlgroup > .ui-controlgroup-item {
	float: left;
	margin-left: 0;
	margin-right: 0;
}
.ui-controlgroup > .ui-controlgroup-item:focus,
.ui-controlgroup > .ui-controlgroup-item.ui-visual-focus {
	z-index: 9999;
}
.ui-controlgroup-vertical > .ui-controlgroup-item {
	display: block;
	float: none;
	width: 100%;
	margin-top: 0;
	margin-bottom: 0;
	text-align: left;
}
.ui-controlgroup-vertical .ui-controlgroup-item {
	box-sizing: border-box;
}
.ui-controlgroup .ui-controlgroup-label {
	padding: .4em 1em;
}
.ui-controlgroup .ui-controlgroup-label span {
	font-size: 80%;
}
.ui-controlgroup-horizontal .ui-controlgroup-label + .ui-controlgroup-item {
	border-left: none;
}
.ui-controlgroup-vertical .ui-controlgroup-label + .ui-controlgroup-item {
	border-top: none;
}
.ui-controlgroup-horizontal .ui-controlgroup-label.ui-widget-content {
	border-right: none;
}
.ui-controlgroup-vertical .ui-controlgroup-label.ui-widget-content {
	border-bottom: none;
}


.ui-controlgroup-vertical .ui-spinner-input {

	
	width: 75%;
	width: calc( 100% - 2.4em );
}
.ui-controlgroup-vertical .ui-spinner .ui-spinner-up {
	border-top-style: solid;
}

.ui-checkboxradio-label .ui-icon-background {
	box-shadow: inset 1px 1px 1px #ccc;
	border-radius: .12em;
	border: none;
}
.ui-checkboxradio-radio-label .ui-icon-background {
	width: 16px;
	height: 16px;
	border-radius: 1em;
	overflow: visible;
	border: none;
}
.ui-checkboxradio-radio-label.ui-checkboxradio-checked .ui-icon,
.ui-checkboxradio-radio-label.ui-checkboxradio-checked:hover .ui-icon {
	background-image: none;
	width: 8px;
	height: 8px;
	border-width: 4px;
	border-style: solid;
}
.ui-checkboxradio-disabled {
	pointer-events: none;
}
.ui-datepicker {
	width: 17em;
	padding: .2em .2em 0;
	display: none;
}
.ui-datepicker .ui-datepicker-header {
	position: relative;
	padding: .2em 0;
}
.ui-datepicker .ui-datepicker-prev,
.ui-datepicker .ui-datepicker-next {
	position: absolute;
	top: 2px;
	width: 1.8em;
	height: 1.8em;
}
.ui-datepicker .ui-datepicker-prev-hover,
.ui-datepicker .ui-datepicker-next-hover {
	top: 1px;
}
.ui-datepicker .ui-datepicker-prev {
	left: 2px;
}
.ui-datepicker .ui-datepicker-next {
	right: 2px;
}
.ui-datepicker .ui-datepicker-prev-hover {
	left: 1px;
}
.ui-datepicker .ui-datepicker-next-hover {
	right: 1px;
}
.ui-datepicker .ui-datepicker-prev span,
.ui-datepicker .ui-datepicker-next span {
	display: block;
	position: absolute;
	left: 50%;
	margin-left: -8px;
	top: 50%;
	margin-top: -8px;
}
.ui-datepicker .ui-datepicker-title {
	margin: 0 2.3em;
	line-height: 1.8em;
	text-align: center;
}
.ui-datepicker .ui-datepicker-title select {
	font-size: 1em;
	margin: 1px 0;
}
.ui-datepicker select.ui-datepicker-month,
.ui-datepicker select.ui-datepicker-year {
	width: 45%;
}
.ui-datepicker table {
	width: 100%;
	font-size: .9em;
	border-collapse: collapse;
	margin: 0 0 .4em;
}
.ui-datepicker th {
	padding: .7em .3em;
	text-align: center;
	font-weight: bold;
	border: 0;
}
.ui-datepicker td {
	border: 0;
	padding: 1px;
}
.ui-datepicker td span,
.ui-datepicker td a {
	display: block;
	padding: .2em;
	text-align: right;
	text-decoration: none;
}
.ui-datepicker .ui-datepicker-buttonpane {
	background-image: none;
	margin: .7em 0 0 0;
	padding: 0 .2em;
	border-left: 0;
	border-right: 0;
	border-bottom: 0;
}
.ui-datepicker .ui-datepicker-buttonpane button {
	float: right;
	margin: .5em .2em .4em;
	cursor: pointer;
	padding: .2em .6em .3em .6em;
	width: auto;
	overflow: visible;
}
.ui-datepicker .ui-datepicker-buttonpane button.ui-datepicker-current {
	float: left;
}


.ui-datepicker.ui-datepicker-multi {
	width: auto;
}
.ui-datepicker-multi .ui-datepicker-group {
	float: left;
}
.ui-datepicker-multi .ui-datepicker-group table {
	width: 95%;
	margin: 0 auto .4em;
}
.ui-datepicker-multi-2 .ui-datepicker-group {
	width: 50%;
}
.ui-datepicker-multi-3 .ui-datepicker-group {
	width: 33.3%;
}
.ui-datepicker-multi-4 .ui-datepicker-group {
	width: 25%;
}
.ui-datepicker-multi .ui-datepicker-group-last .ui-datepicker-header,
.ui-datepicker-multi .ui-datepicker-group-middle .ui-datepicker-header {
	border-left-width: 0;
}
.ui-datepicker-multi .ui-datepicker-buttonpane {
	clear: left;
}
.ui-datepicker-row-break {
	clear: both;
	width: 100%;
	font-size: 0;
}


.ui-datepicker-rtl {
	direction: rtl;
}
.ui-datepicker-rtl .ui-datepicker-prev {
	right: 2px;
	left: auto;
}
.ui-datepicker-rtl .ui-datepicker-next {
	left: 2px;
	right: auto;
}
.ui-datepicker-rtl .ui-datepicker-prev:hover {
	right: 1px;
	left: auto;
}
.ui-datepicker-rtl .ui-datepicker-next:hover {
	left: 1px;
	right: auto;
}
.ui-datepicker-rtl .ui-datepicker-buttonpane {
	clear: right;
}
.ui-datepicker-rtl .ui-datepicker-buttonpane button {
	float: left;
}
.ui-datepicker-rtl .ui-datepicker-buttonpane button.ui-datepicker-current,
.ui-datepicker-rtl .ui-datepicker-group {
	float: right;
}
.ui-datepicker-rtl .ui-datepicker-group-last .ui-datepicker-header,
.ui-datepicker-rtl .ui-datepicker-group-middle .ui-datepicker-header {
	border-right-width: 0;
	border-left-width: 1px;
}


.ui-datepicker .ui-icon {
	display: block;
	text-indent: -99999px;
	overflow: hidden;
	background-repeat: no-repeat;
	left: .5em;
	top: .3em;
}
.ui-dialog {
	position: absolute;
	top: 0;
	left: 0;
	padding: .2em;
	outline: 0;
}
.ui-dialog .ui-dialog-titlebar {
	padding: .4em 1em;
	position: relative;
}
.ui-dialog .ui-dialog-title {
	float: left;
	margin: .1em 0;
	white-space: nowrap;
	width: 90%;
	overflow: hidden;
	text-overflow: ellipsis;
}
.ui-dialog .ui-dialog-titlebar-close {
	position: absolute;
	right: .3em;
	top: 50%;
	width: 20px;
	margin: -10px 0 0 0;
	padding: 1px;
	height: 20px;
}
.ui-dialog .ui-dialog-content {
	position: relative;
	border: 0;
	padding: .5em 1em;
	background: none;
	overflow: auto;
}
.ui-dialog .ui-dialog-buttonpane {
	text-align: left;
	border-width: 1px 0 0 0;
	background-image: none;
	margin-top: .5em;
	padding: .3em 1em .5em .4em;
}
.ui-dialog .ui-dialog-buttonpane .ui-dialog-buttonset {
	float: right;
}
.ui-dialog .ui-dialog-buttonpane button {
	margin: .5em .4em .5em 0;
	cursor: pointer;
}
.ui-dialog .ui-resizable-n {
	height: 2px;
	top: 0;
}
.ui-dialog .ui-resizable-e {
	width: 2px;
	right: 0;
}
.ui-dialog .ui-resizable-s {
	height: 2px;
	bottom: 0;
}
.ui-dialog .ui-resizable-w {
	width: 2px;
	left: 0;
}
.ui-dialog .ui-resizable-se,
.ui-dialog .ui-resizable-sw,
.ui-dialog .ui-resizable-ne,
.ui-dialog .ui-resizable-nw {
	width: 7px;
	height: 7px;
}
.ui-dialog .ui-resizable-se {
	right: 0;
	bottom: 0;
}
.ui-dialog .ui-resizable-sw {
	left: 0;
	bottom: 0;
}
.ui-dialog .ui-resizable-ne {
	right: 0;
	top: 0;
}
.ui-dialog .ui-resizable-nw {
	left: 0;
	top: 0;
}
.ui-draggable .ui-dialog-titlebar {
	cursor: move;
}
.ui-draggable-handle {
	-ms-touch-action: none;
	touch-action: none;
}
.ui-resizable {
	position: relative;
}
.ui-resizable-handle {
	position: absolute;
	font-size: 0.1px;
	display: block;
	-ms-touch-action: none;
	touch-action: none;
}
.ui-resizable-disabled .ui-resizable-handle,
.ui-resizable-autohide .ui-resizable-handle {
	display: none;
}
.ui-resizable-n {
	cursor: n-resize;
	height: 7px;
	width: 100%;
	top: -5px;
	left: 0;
}
.ui-resizable-s {
	cursor: s-resize;
	height: 7px;
	width: 100%;
	bottom: -5px;
	left: 0;
}
.ui-resizable-e {
	cursor: e-resize;
	width: 7px;
	right: -5px;
	top: 0;
	height: 100%;
}
.ui-resizable-w {
	cursor: w-resize;
	width: 7px;
	left: -5px;
	top: 0;
	height: 100%;
}
.ui-resizable-se {
	cursor: se-resize;
	width: 12px;
	height: 12px;
	right: 1px;
	bottom: 1px;
}
.ui-resizable-sw {
	cursor: sw-resize;
	width: 9px;
	height: 9px;
	left: -5px;
	bottom: -5px;
}
.ui-resizable-nw {
	cursor: nw-resize;
	width: 9px;
	height: 9px;
	left: -5px;
	top: -5px;
}
.ui-resizable-ne {
	cursor: ne-resize;
	width: 9px;
	height: 9px;
	right: -5px;
	top: -5px;
}
.ui-progressbar {
	height: 2em;
	text-align: left;
	overflow: hidden;
}
.ui-progressbar .ui-progressbar-value {
	margin: -1px;
	height: 100%;
}
.ui-progressbar .ui-progressbar-overlay {
	background: url("data:image/gif;base64,R0lGODlhKAAoAIABAAAAAP///yH/C05FVFNDQVBFMi4wAwEAAAAh+QQJAQABACwAAAAAKAAoAAACkYwNqXrdC52DS06a7MFZI+4FHBCKoDeWKXqymPqGqxvJrXZbMx7Ttc+w9XgU2FB3lOyQRWET2IFGiU9m1frDVpxZZc6bfHwv4c1YXP6k1Vdy292Fb6UkuvFtXpvWSzA+HycXJHUXiGYIiMg2R6W459gnWGfHNdjIqDWVqemH2ekpObkpOlppWUqZiqr6edqqWQAAIfkECQEAAQAsAAAAACgAKAAAApSMgZnGfaqcg1E2uuzDmmHUBR8Qil95hiPKqWn3aqtLsS18y7G1SzNeowWBENtQd+T1JktP05nzPTdJZlR6vUxNWWjV+vUWhWNkWFwxl9VpZRedYcflIOLafaa28XdsH/ynlcc1uPVDZxQIR0K25+cICCmoqCe5mGhZOfeYSUh5yJcJyrkZWWpaR8doJ2o4NYq62lAAACH5BAkBAAEALAAAAAAoACgAAAKVDI4Yy22ZnINRNqosw0Bv7i1gyHUkFj7oSaWlu3ovC8GxNso5fluz3qLVhBVeT/Lz7ZTHyxL5dDalQWPVOsQWtRnuwXaFTj9jVVh8pma9JjZ4zYSj5ZOyma7uuolffh+IR5aW97cHuBUXKGKXlKjn+DiHWMcYJah4N0lYCMlJOXipGRr5qdgoSTrqWSq6WFl2ypoaUAAAIfkECQEAAQAsAAAAACgAKAAAApaEb6HLgd/iO7FNWtcFWe+ufODGjRfoiJ2akShbueb0wtI50zm02pbvwfWEMWBQ1zKGlLIhskiEPm9R6vRXxV4ZzWT2yHOGpWMyorblKlNp8HmHEb/lCXjcW7bmtXP8Xt229OVWR1fod2eWqNfHuMjXCPkIGNileOiImVmCOEmoSfn3yXlJWmoHGhqp6ilYuWYpmTqKUgAAIfkECQEAAQAsAAAAACgAKAAAApiEH6kb58biQ3FNWtMFWW3eNVcojuFGfqnZqSebuS06w5V80/X02pKe8zFwP6EFWOT1lDFk8rGERh1TTNOocQ61Hm4Xm2VexUHpzjymViHrFbiELsefVrn6XKfnt2Q9G/+Xdie499XHd2g4h7ioOGhXGJboGAnXSBnoBwKYyfioubZJ2Hn0RuRZaflZOil56Zp6iioKSXpUAAAh+QQJAQABACwAAAAAKAAoAAACkoQRqRvnxuI7kU1a1UU5bd5tnSeOZXhmn5lWK3qNTWvRdQxP8qvaC+/yaYQzXO7BMvaUEmJRd3TsiMAgswmNYrSgZdYrTX6tSHGZO73ezuAw2uxuQ+BbeZfMxsexY35+/Qe4J1inV0g4x3WHuMhIl2jXOKT2Q+VU5fgoSUI52VfZyfkJGkha6jmY+aaYdirq+lQAACH5BAkBAAEALAAAAAAoACgAAAKWBIKpYe0L3YNKToqswUlvznigd4wiR4KhZrKt9Upqip61i9E3vMvxRdHlbEFiEXfk9YARYxOZZD6VQ2pUunBmtRXo1Lf8hMVVcNl8JafV38aM2/Fu5V16Bn63r6xt97j09+MXSFi4BniGFae3hzbH9+hYBzkpuUh5aZmHuanZOZgIuvbGiNeomCnaxxap2upaCZsq+1kAACH5BAkBAAEALAAAAAAoACgAAAKXjI8By5zf4kOxTVrXNVlv1X0d8IGZGKLnNpYtm8Lr9cqVeuOSvfOW79D9aDHizNhDJidFZhNydEahOaDH6nomtJjp1tutKoNWkvA6JqfRVLHU/QUfau9l2x7G54d1fl995xcIGAdXqMfBNadoYrhH+Mg2KBlpVpbluCiXmMnZ2Sh4GBqJ+ckIOqqJ6LmKSllZmsoq6wpQAAAh+QQJAQABACwAAAAAKAAoAAAClYx/oLvoxuJDkU1a1YUZbJ59nSd2ZXhWqbRa2/gF8Gu2DY3iqs7yrq+xBYEkYvFSM8aSSObE+ZgRl1BHFZNr7pRCavZ5BW2142hY3AN/zWtsmf12p9XxxFl2lpLn1rseztfXZjdIWIf2s5dItwjYKBgo9yg5pHgzJXTEeGlZuenpyPmpGQoKOWkYmSpaSnqKileI2FAAACH5BAkBAAEALAAAAAAoACgAAAKVjB+gu+jG4kORTVrVhRlsnn2dJ3ZleFaptFrb+CXmO9OozeL5VfP99HvAWhpiUdcwkpBH3825AwYdU8xTqlLGhtCosArKMpvfa1mMRae9VvWZfeB2XfPkeLmm18lUcBj+p5dnN8jXZ3YIGEhYuOUn45aoCDkp16hl5IjYJvjWKcnoGQpqyPlpOhr3aElaqrq56Bq7VAAAOw==");
	height: 100%;
	filter: alpha(opacity=25); 
	opacity: 0.25;
}
.ui-progressbar-indeterminate .ui-progressbar-value {
	background-image: none;
}
.ui-selectable {
	-ms-touch-action: none;
	touch-action: none;
}
.ui-selectable-helper {
	position: absolute;
	z-index: 100;
	border: 1px dotted black;
}
.ui-selectmenu-menu {
	padding: 0;
	margin: 0;
	position: absolute;
	top: 0;
	left: 0;
	display: none;
}
.ui-selectmenu-menu .ui-menu {
	overflow: auto;
	overflow-x: hidden;
	padding-bottom: 1px;
}
.ui-selectmenu-menu .ui-menu .ui-selectmenu-optgroup {
	font-size: 1em;
	font-weight: bold;
	line-height: 1.5;
	padding: 2px 0.4em;
	margin: 0.5em 0 0 0;
	height: auto;
	border: 0;
}
.ui-selectmenu-open {
	display: block;
}
.ui-selectmenu-text {
	display: block;
	margin-right: 20px;
	overflow: hidden;
	text-overflow: ellipsis;
}
.ui-selectmenu-button.ui-button {
	text-align: left;
	white-space: nowrap;
	width: 14em;
}
.ui-selectmenu-icon.ui-icon {
	float: right;
	margin-top: 0;
}
.ui-slider {
	position: relative;
	text-align: left;
}
.ui-slider .ui-slider-handle {
	position: absolute;
	z-index: 2;
	width: 1.2em;
	height: 1.2em;
	cursor: default;
	-ms-touch-action: none;
	touch-action: none;
}
.ui-slider .ui-slider-range {
	position: absolute;
	z-index: 1;
	font-size: .7em;
	display: block;
	border: 0;
	background-position: 0 0;
}


.ui-slider.ui-state-disabled .ui-slider-handle,
.ui-slider.ui-state-disabled .ui-slider-range {
	filter: inherit;
}

.ui-slider-horizontal {
	height: .8em;
}
.ui-slider-horizontal .ui-slider-handle {
	top: -.3em;
	margin-left: -.6em;
}
.ui-slider-horizontal .ui-slider-range {
	top: 0;
	height: 100%;
}
.ui-slider-horizontal .ui-slider-range-min {
	left: 0;
}
.ui-slider-horizontal .ui-slider-range-max {
	right: 0;
}

.ui-slider-vertical {
	width: .8em;
	height: 100px;
}
.ui-slider-vertical .ui-slider-handle {
	left: -.3em;
	margin-left: 0;
	margin-bottom: -.6em;
}
.ui-slider-vertical .ui-slider-range {
	left: 0;
	width: 100%;
}
.ui-slider-vertical .ui-slider-range-min {
	bottom: 0;
}
.ui-slider-vertical .ui-slider-range-max {
	top: 0;
}
.ui-sortable-handle {
	-ms-touch-action: none;
	touch-action: none;
}
.ui-spinner {
	position: relative;
	display: inline-block;
	overflow: hidden;
	padding: 0;
	vertical-align: middle;
}
.ui-spinner-input {
	border: none;
	background: none;
	color: inherit;
	padding: .222em 0;
	margin: .2em 0;
	vertical-align: middle;
	margin-left: .4em;
	margin-right: 2em;
}
.ui-spinner-button {
	width: 1.6em;
	height: 50%;
	font-size: .5em;
	padding: 0;
	margin: 0;
	text-align: center;
	position: absolute;
	cursor: default;
	display: block;
	overflow: hidden;
	right: 0;
}

.ui-spinner a.ui-spinner-button {
	border-top-style: none;
	border-bottom-style: none;
	border-right-style: none;
}
.ui-spinner-up {
	top: 0;
}
.ui-spinner-down {
	bottom: 0;
}
.ui-tabs {
	position: relative;
	padding: .2em;
}
.ui-tabs .ui-tabs-nav {
	margin: 0;
	padding: .2em .2em 0;
}
.ui-tabs .ui-tabs-nav li {
	list-style: none;
	float: left;
	position: relative;
	top: 0;
	margin: 1px .2em 0 0;
	border-bottom-width: 0;
	padding: 0;
	white-space: nowrap;
}
.ui-tabs .ui-tabs-nav .ui-tabs-anchor {
	float: left;
	padding: .5em 1em;
	text-decoration: none;
}
.ui-tabs .ui-tabs-nav li.ui-tabs-active {
	margin-bottom: -1px;
	padding-bottom: 1px;
}
.ui-tabs .ui-tabs-nav li.ui-tabs-active .ui-tabs-anchor,
.ui-tabs .ui-tabs-nav li.ui-state-disabled .ui-tabs-anchor,
.ui-tabs .ui-tabs-nav li.ui-tabs-loading .ui-tabs-anchor {
	cursor: text;
}
.ui-tabs-collapsible .ui-tabs-nav li.ui-tabs-active .ui-tabs-anchor {
	cursor: pointer;
}
.ui-tabs .ui-tabs-panel {
	display: block;
	border-width: 0;
	padding: 1em 1.4em;
	background: none;
}
.ui-tooltip {
	padding: 8px;
	position: absolute;
	z-index: 9999;
	max-width: 300px;
}
body .ui-tooltip {
	border-width: 2px;
}

.ui-widget {
	font-family: Arial,Helvetica,sans-serif;
	font-size: 1em;
}
.ui-widget .ui-widget {
	font-size: 1em;
}
.ui-widget input,
.ui-widget select,
.ui-widget textarea,
.ui-widget button {
	font-family: Arial,Helvetica,sans-serif;
	font-size: 1em;
}
.ui-widget.ui-widget-content {
	border: 1px solid #c5c5c5;
}
.ui-widget-content {
	border: 1px solid #dddddd;
	background: #ffffff;
	color: #333333;
}
.ui-widget-content a {
	color: #333333;
}
.ui-widget-header {
	border: 1px solid #dddddd;
	background: #e9e9e9;
	color: #333333;
	font-weight: bold;
}
.ui-widget-header a {
	color: #333333;
}


.ui-state-default,
.ui-widget-content .ui-state-default,
.ui-widget-header .ui-state-default,
.ui-button,


html .ui-button.ui-state-disabled:hover,
html .ui-button.ui-state-disabled:active {
	border: 1px solid #c5c5c5;
	background: #f6f6f6;
	font-weight: normal;
	color: #454545;
}
.ui-state-default a,
.ui-state-default a:link,
.ui-state-default a:visited,
a.ui-button,
a:link.ui-button,
a:visited.ui-button,
.ui-button {
	color: #454545;
	text-decoration: none;
}
.ui-state-hover,
.ui-widget-content .ui-state-hover,
.ui-widget-header .ui-state-hover,
.ui-state-focus,
.ui-widget-content .ui-state-focus,
.ui-widget-header .ui-state-focus,
.ui-button:hover,
.ui-button:focus {
	border: 1px solid #cccccc;
	background: #ededed;
	font-weight: normal;
	color: #2b2b2b;
}
.ui-state-hover a,
.ui-state-hover a:hover,
.ui-state-hover a:link,
.ui-state-hover a:visited,
.ui-state-focus a,
.ui-state-focus a:hover,
.ui-state-focus a:link,
.ui-state-focus a:visited,
a.ui-button:hover,
a.ui-button:focus {
	color: #2b2b2b;
	text-decoration: none;
}

.ui-visual-focus {
	box-shadow: 0 0 3px 1px rgb(94, 158, 214);
}
.ui-state-active,
.ui-widget-content .ui-state-active,
.ui-widget-header .ui-state-active,
a.ui-button:active,
.ui-button:active,
.ui-button.ui-state-active:hover {
	border: 1px solid #003eff;
	background: #007fff;
	font-weight: normal;
	color: #ffffff;
}
.ui-icon-background,
.ui-state-active .ui-icon-background {
	border: #003eff;
	background-color: #ffffff;
}
.ui-state-active a,
.ui-state-active a:link,
.ui-state-active a:visited {
	color: #ffffff;
	text-decoration: none;
}


.ui-state-highlight,
.ui-widget-content .ui-state-highlight,
.ui-widget-header .ui-state-highlight {
	border: 1px solid #dad55e;
	background: #fffa90;
	color: #777620;
}
.ui-state-checked {
	border: 1px solid #dad55e;
	background: #fffa90;
}
.ui-state-highlight a,
.ui-widget-content .ui-state-highlight a,
.ui-widget-header .ui-state-highlight a {
	color: #777620;
}
.ui-state-error,
.ui-widget-content .ui-state-error,
.ui-widget-header .ui-state-error {
	border: 1px solid #f1a899;
	background: #fddfdf;
	color: #5f3f3f;
}
.ui-state-error a,
.ui-widget-content .ui-state-error a,
.ui-widget-header .ui-state-error a {
	color: #5f3f3f;
}
.ui-state-error-text,
.ui-widget-content .ui-state-error-text,
.ui-widget-header .ui-state-error-text {
	color: #5f3f3f;
}
.ui-priority-primary,
.ui-widget-content .ui-priority-primary,
.ui-widget-header .ui-priority-primary {
	font-weight: bold;
}
.ui-priority-secondary,
.ui-widget-content .ui-priority-secondary,
.ui-widget-header .ui-priority-secondary {
	opacity: .7;
	filter:Alpha(Opacity=70); 
	font-weight: normal;
}
.ui-state-disabled,
.ui-widget-content .ui-state-disabled,
.ui-widget-header .ui-state-disabled {
	opacity: .35;
	filter:Alpha(Opacity=35); 
	background-image: none;
}
.ui-state-disabled .ui-icon {
	filter:Alpha(Opacity=35); 
}




.ui-icon {
	width: 16px;
	height: 16px;
}
.ui-icon,
.ui-widget-content .ui-icon {
	background-image: url("images/ui-icons_444444_256x240.png");
}
.ui-widget-header .ui-icon {
	background-image: url("images/ui-icons_444444_256x240.png");
}
.ui-state-hover .ui-icon,
.ui-state-focus .ui-icon,
.ui-button:hover .ui-icon,
.ui-button:focus .ui-icon {
	background-image: url("images/ui-icons_555555_256x240.png");
}
.ui-state-active .ui-icon,
.ui-button:active .ui-icon {
	background-image: url("images/ui-icons_ffffff_256x240.png");
}
.ui-state-highlight .ui-icon,
.ui-button .ui-state-highlight.ui-icon {
	background-image: url("images/ui-icons_777620_256x240.png");
}
.ui-state-error .ui-icon,
.ui-state-error-text .ui-icon {
	background-image: url("images/ui-icons_cc0000_256x240.png");
}
.ui-button .ui-icon {
	background-image: url("images/ui-icons_777777_256x240.png");
}


.ui-icon-blank { background-position: 16px 16px; }
.ui-icon-caret-1-n { background-position: 0 0; }
.ui-icon-caret-1-ne { background-position: -16px 0; }
.ui-icon-caret-1-e { background-position: -32px 0; }
.ui-icon-caret-1-se { background-position: -48px 0; }
.ui-icon-caret-1-s { background-position: -65px 0; }
.ui-icon-caret-1-sw { background-position: -80px 0; }
.ui-icon-caret-1-w { background-position: -96px 0; }
.ui-icon-caret-1-nw { background-position: -112px 0; }
.ui-icon-caret-2-n-s { background-position: -128px 0; }
.ui-icon-caret-2-e-w { background-position: -144px 0; }
.ui-icon-triangle-1-n { background-position: 0 -16px; }
.ui-icon-triangle-1-ne { background-position: -16px -16px; }
.ui-icon-triangle-1-e { background-position: -32px -16px; }
.ui-icon-triangle-1-se { background-position: -48px -16px; }
.ui-icon-triangle-1-s { background-position: -65px -16px; }
.ui-icon-triangle-1-sw { background-position: -80px -16px; }
.ui-icon-triangle-1-w { background-position: -96px -16px; }
.ui-icon-triangle-1-nw { background-position: -112px -16px; }
.ui-icon-triangle-2-n-s { background-position: -128px -16px; }
.ui-icon-triangle-2-e-w { background-position: -144px -16px; }
.ui-icon-arrow-1-n { background-position: 0 -32px; }
.ui-icon-arrow-1-ne { background-position: -16px -32px; }
.ui-icon-arrow-1-e { background-position: -32px -32px; }
.ui-icon-arrow-1-se { background-position: -48px -32px; }
.ui-icon-arrow-1-s { background-position: -65px -32px; }
.ui-icon-arrow-1-sw { background-position: -80px -32px; }
.ui-icon-arrow-1-w { background-position: -96px -32px; }
.ui-icon-arrow-1-nw { background-position: -112px -32px; }
.ui-icon-arrow-2-n-s { background-position: -128px -32px; }
.ui-icon-arrow-2-ne-sw { background-position: -144px -32px; }
.ui-icon-arrow-2-e-w { background-position: -160px -32px; }
.ui-icon-arrow-2-se-nw { background-position: -176px -32px; }
.ui-icon-arrowstop-1-n { background-position: -192px -32px; }
.ui-icon-arrowstop-1-e { background-position: -208px -32px; }
.ui-icon-arrowstop-1-s { background-position: -224px -32px; }
.ui-icon-arrowstop-1-w { background-position: -240px -32px; }
.ui-icon-arrowthick-1-n { background-position: 1px -48px; }
.ui-icon-arrowthick-1-ne { background-position: -16px -48px; }
.ui-icon-arrowthick-1-e { background-position: -32px -48px; }
.ui-icon-arrowthick-1-se { background-position: -48px -48px; }
.ui-icon-arrowthick-1-s { background-position: -64px -48px; }
.ui-icon-arrowthick-1-sw { background-position: -80px -48px; }
.ui-icon-arrowthick-1-w { background-position: -96px -48px; }
.ui-icon-arrowthick-1-nw { background-position: -112px -48px; }
.ui-icon-arrowthick-2-n-s { background-position: -128px -48px; }
.ui-icon-arrowthick-2-ne-sw { background-position: -144px -48px; }
.ui-icon-arrowthick-2-e-w { background-position: -160px -48px; }
.ui-icon-arrowthick-2-se-nw { background-position: -176px -48px; }
.ui-icon-arrowthickstop-1-n { background-position: -192px -48px; }
.ui-icon-arrowthickstop-1-e { background-position: -208px -48px; }
.ui-icon-arrowthickstop-1-s { background-position: -224px -48px; }
.ui-icon-arrowthickstop-1-w { background-position: -240px -48px; }
.ui-icon-arrowreturnthick-1-w { background-position: 0 -64px; }
.ui-icon-arrowreturnthick-1-n { background-position: -16px -64px; }
.ui-icon-arrowreturnthick-1-e { background-position: -32px -64px; }
.ui-icon-arrowreturnthick-1-s { background-position: -48px -64px; }
.ui-icon-arrowreturn-1-w { background-position: -64px -64px; }
.ui-icon-arrowreturn-1-n { background-position: -80px -64px; }
.ui-icon-arrowreturn-1-e { background-position: -96px -64px; }
.ui-icon-arrowreturn-1-s { background-position: -112px -64px; }
.ui-icon-arrowrefresh-1-w { background-position: -128px -64px; }
.ui-icon-arrowrefresh-1-n { background-position: -144px -64px; }
.ui-icon-arrowrefresh-1-e { background-position: -160px -64px; }
.ui-icon-arrowrefresh-1-s { background-position: -176px -64px; }
.ui-icon-arrow-4 { background-position: 0 -80px; }
.ui-icon-arrow-4-diag { background-position: -16px -80px; }
.ui-icon-extlink { background-position: -32px -80px; }
.ui-icon-newwin { background-position: -48px -80px; }
.ui-icon-refresh { background-position: -64px -80px; }
.ui-icon-shuffle { background-position: -80px -80px; }
.ui-icon-transfer-e-w { background-position: -96px -80px; }
.ui-icon-transferthick-e-w { background-position: -112px -80px; }
.ui-icon-folder-collapsed { background-position: 0 -96px; }
.ui-icon-folder-open { background-position: -16px -96px; }
.ui-icon-document { background-position: -32px -96px; }
.ui-icon-document-b { background-position: -48px -96px; }
.ui-icon-note { background-position: -64px -96px; }
.ui-icon-mail-closed { background-position: -80px -96px; }
.ui-icon-mail-open { background-position: -96px -96px; }
.ui-icon-suitcase { background-position: -112px -96px; }
.ui-icon-comment { background-position: -128px -96px; }
.ui-icon-person { background-position: -144px -96px; }
.ui-icon-print { background-position: -160px -96px; }
.ui-icon-trash { background-position: -176px -96px; }
.ui-icon-locked { background-position: -192px -96px; }
.ui-icon-unlocked { background-position: -208px -96px; }
.ui-icon-bookmark { background-position: -224px -96px; }
.ui-icon-tag { background-position: -240px -96px; }
.ui-icon-home { background-position: 0 -112px; }
.ui-icon-flag { background-position: -16px -112px; }
.ui-icon-calendar { background-position: -32px -112px; }
.ui-icon-cart { background-position: -48px -112px; }
.ui-icon-pencil { background-position: -64px -112px; }
.ui-icon-clock { background-position: -80px -112px; }
.ui-icon-disk { background-position: -96px -112px; }
.ui-icon-calculator { background-position: -112px -112px; }
.ui-icon-zoomin { background-position: -128px -112px; }
.ui-icon-zoomout { background-position: -144px -112px; }
.ui-icon-search { background-position: -160px -112px; }
.ui-icon-wrench { background-position: -176px -112px; }
.ui-icon-gear { background-position: -192px -112px; }
.ui-icon-heart { background-position: -208px -112px; }
.ui-icon-star { background-position: -224px -112px; }
.ui-icon-link { background-position: -240px -112px; }
.ui-icon-cancel { background-position: 0 -128px; }
.ui-icon-plus { background-position: -16px -128px; }
.ui-icon-plusthick { background-position: -32px -128px; }
.ui-icon-minus { background-position: -48px -128px; }
.ui-icon-minusthick { background-position: -64px -128px; }
.ui-icon-close { background-position: -80px -128px; }
.ui-icon-closethick { background-position: -96px -128px; }
.ui-icon-key { background-position: -112px -128px; }
.ui-icon-lightbulb { background-position: -128px -128px; }
.ui-icon-scissors { background-position: -144px -128px; }
.ui-icon-clipboard { background-position: -160px -128px; }
.ui-icon-copy { background-position: -176px -128px; }
.ui-icon-contact { background-position: -192px -128px; }
.ui-icon-image { background-position: -208px -128px; }
.ui-icon-video { background-position: -224px -128px; }
.ui-icon-script { background-position: -240px -128px; }
.ui-icon-alert { background-position: 0 -144px; }
.ui-icon-info { background-position: -16px -144px; }
.ui-icon-notice { background-position: -32px -144px; }
.ui-icon-help { background-position: -48px -144px; }
.ui-icon-check { background-position: -64px -144px; }
.ui-icon-bullet { background-position: -80px -144px; }
.ui-icon-radio-on { background-position: -96px -144px; }
.ui-icon-radio-off { background-position: -112px -144px; }
.ui-icon-pin-w { background-position: -128px -144px; }
.ui-icon-pin-s { background-position: -144px -144px; }
.ui-icon-play { background-position: 0 -160px; }
.ui-icon-pause { background-position: -16px -160px; }
.ui-icon-seek-next { background-position: -32px -160px; }
.ui-icon-seek-prev { background-position: -48px -160px; }
.ui-icon-seek-end { background-position: -64px -160px; }
.ui-icon-seek-start { background-position: -80px -160px; }

.ui-icon-seek-first { background-position: -80px -160px; }
.ui-icon-stop { background-position: -96px -160px; }
.ui-icon-eject { background-position: -112px -160px; }
.ui-icon-volume-off { background-position: -128px -160px; }
.ui-icon-volume-on { background-position: -144px -160px; }
.ui-icon-power { background-position: 0 -176px; }
.ui-icon-signal-diag { background-position: -16px -176px; }
.ui-icon-signal { background-position: -32px -176px; }
.ui-icon-battery-0 { background-position: -48px -176px; }
.ui-icon-battery-1 { background-position: -64px -176px; }
.ui-icon-battery-2 { background-position: -80px -176px; }
.ui-icon-battery-3 { background-position: -96px -176px; }
.ui-icon-circle-plus { background-position: 0 -192px; }
.ui-icon-circle-minus { background-position: -16px -192px; }
.ui-icon-circle-close { background-position: -32px -192px; }
.ui-icon-circle-triangle-e { background-position: -48px -192px; }
.ui-icon-circle-triangle-s { background-position: -64px -192px; }
.ui-icon-circle-triangle-w { background-position: -80px -192px; }
.ui-icon-circle-triangle-n { background-position: -96px -192px; }
.ui-icon-circle-arrow-e { background-position: -112px -192px; }
.ui-icon-circle-arrow-s { background-position: -128px -192px; }
.ui-icon-circle-arrow-w { background-position: -144px -192px; }
.ui-icon-circle-arrow-n { background-position: -160px -192px; }
.ui-icon-circle-zoomin { background-position: -176px -192px; }
.ui-icon-circle-zoomout { background-position: -192px -192px; }
.ui-icon-circle-check { background-position: -208px -192px; }
.ui-icon-circlesmall-plus { background-position: 0 -208px; }
.ui-icon-circlesmall-minus { background-position: -16px -208px; }
.ui-icon-circlesmall-close { background-position: -32px -208px; }
.ui-icon-squaresmall-plus { background-position: -48px -208px; }
.ui-icon-squaresmall-minus { background-position: -64px -208px; }
.ui-icon-squaresmall-close { background-position: -80px -208px; }
.ui-icon-grip-dotted-vertical { background-position: 0 -224px; }
.ui-icon-grip-dotted-horizontal { background-position: -16px -224px; }
.ui-icon-grip-solid-vertical { background-position: -32px -224px; }
.ui-icon-grip-solid-horizontal { background-position: -48px -224px; }
.ui-icon-gripsmall-diagonal-se { background-position: -64px -224px; }
.ui-icon-grip-diagonal-se { background-position: -80px -224px; }





.ui-corner-all,
.ui-corner-top,
.ui-corner-left,
.ui-corner-tl {
	border-top-left-radius: 3px;
}
.ui-corner-all,
.ui-corner-top,
.ui-corner-right,
.ui-corner-tr {
	border-top-right-radius: 3px;
}
.ui-corner-all,
.ui-corner-bottom,
.ui-corner-left,
.ui-corner-bl {
	border-bottom-left-radius: 3px;
}
.ui-corner-all,
.ui-corner-bottom,
.ui-corner-right,
.ui-corner-br {
	border-bottom-right-radius: 3px;
}


.ui-widget-overlay {
	background: #aaaaaa;
	opacity: .3;
	filter: Alpha(Opacity=30); 
}
.ui-widget-shadow {
	-webkit-box-shadow: 0px 0px 5px #666666;
	box-shadow: 0px 0px 5px #666666;
} 
</style>
<script src='js/jquery-1.12.4.js'></script>
<script src='js/jquery-ui.js'></script>

<script>
$( function() {
	$( '#tabs-collect-classes-from-hierarchical-partition' ).tabs();
} );
</script>
<div id='tabs-collect-classes-from-hierarchical-partition'>
<ul>
<li><a href='#tab-collect-classes-from-hierarchical-partition-1'>n_signatures ≥ 1217</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-2'>n_signatures ≥ 2183</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-3'>n_signatures ≥ 3210</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-4'>n_signatures ≥ 3371</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-5'>n_signatures ≥ 3794</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-6'>n_signatures ≥ 14315</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-7'>n_signatures ≥ 14944</a></li>
<li><a href='#tab-collect-classes-from-hierarchical-partition-8'>n_signatures ≥ 24376</a></li>
</ul>
<div id='tab-collect-classes-from-hierarchical-partition-1'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 1217))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-1-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-1"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-2'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 2183))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-2-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-2"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-3'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3210))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-3-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-3"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-4'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3371))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-4-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-4"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-5'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3794))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-5-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-5"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-6'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 14315))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-6-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-6"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-7'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 14944))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-7-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-7"/></p>

</div>
<div id='tab-collect-classes-from-hierarchical-partition-8'>
<pre><code class="r">collect_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 24376))
</code></pre>

<p><img src="figure_cola/tab-collect-classes-from-hierarchical-partition-8-1.png" alt="plot of chunk tab-collect-classes-from-hierarchical-partition-8"/></p>

</div>
</div>

Following shows the table of the partitions (You need to click the **show/hide
code output** link to see it).


<script>
$( function() {
	$( '#tabs-get-classes-from-hierarchical-partition' ).tabs();
} );
</script>
<div id='tabs-get-classes-from-hierarchical-partition'>
<ul>
<li><a href='#tab-get-classes-from-hierarchical-partition-1'>n_signatures ≥ 1217</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-2'>n_signatures ≥ 2183</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-3'>n_signatures ≥ 3210</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-4'>n_signatures ≥ 3371</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-5'>n_signatures ≥ 3794</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-6'>n_signatures ≥ 14315</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-7'>n_signatures ≥ 14944</a></li>
<li><a href='#tab-get-classes-from-hierarchical-partition-8'>n_signatures ≥ 24376</a></li>
</ul>

<div id='tab-get-classes-from-hierarchical-partition-1'>
<p><a id='tab-get-classes-from-hierarchical-partition-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 1217))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;           &quot;022&quot;           &quot;022&quot;          &quot;0321&quot;          &quot;0321&quot;           &quot;022&quot;          &quot;0311&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;          &quot;0323&quot;          &quot;0112&quot;          &quot;0323&quot;           &quot;023&quot;         &quot;03221&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;           &quot;021&quot;          &quot;0111&quot;           &quot;013&quot;          &quot;0321&quot;          &quot;0113&quot;           &quot;013&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;          &quot;0323&quot;         &quot;03221&quot;         &quot;03222&quot;          &quot;0111&quot;         &quot;03222&quot;           &quot;022&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;          &quot;0323&quot;          &quot;0312&quot;           &quot;022&quot;         &quot;03222&quot;          &quot;0324&quot;          &quot;0312&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;         &quot;03222&quot;           &quot;023&quot;           &quot;013&quot;           &quot;023&quot;           &quot;013&quot;           &quot;022&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;           &quot;022&quot;          &quot;0311&quot;         &quot;03222&quot;          &quot;0311&quot;           &quot;021&quot;          &quot;0312&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;           &quot;023&quot;          &quot;0323&quot;          &quot;0321&quot;           &quot;022&quot;          &quot;0311&quot;           &quot;012&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;          &quot;0111&quot;          &quot;0321&quot;          &quot;0113&quot;          &quot;0311&quot;          &quot;0311&quot;          &quot;0111&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;           &quot;012&quot;           &quot;022&quot;           &quot;023&quot;          &quot;0323&quot;         &quot;03221&quot;           &quot;012&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;          &quot;0111&quot;         &quot;03222&quot;          &quot;0111&quot;          &quot;0111&quot;          &quot;0323&quot;           &quot;021&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;         &quot;03221&quot;          &quot;0324&quot;          &quot;0312&quot;         &quot;03222&quot;          &quot;0311&quot;          &quot;0312&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;          &quot;0111&quot;           &quot;012&quot;          &quot;0312&quot;          &quot;0112&quot;          &quot;0321&quot;           &quot;012&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;           &quot;013&quot;         &quot;03222&quot;         &quot;03222&quot;           &quot;012&quot;          &quot;0111&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;          &quot;0113&quot;           &quot;022&quot;         &quot;03222&quot;          &quot;0323&quot;          &quot;0311&quot;          &quot;0321&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;           &quot;022&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;023&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;          &quot;0111&quot;          &quot;0321&quot;           &quot;022&quot;          &quot;0311&quot;           &quot;021&quot;           &quot;021&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;           &quot;021&quot;           &quot;021&quot;          &quot;0112&quot;           &quot;012&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-1-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-1-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-2'>
<p><a id='tab-get-classes-from-hierarchical-partition-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 2183))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;           &quot;022&quot;           &quot;022&quot;          &quot;0321&quot;          &quot;0321&quot;           &quot;022&quot;          &quot;0311&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;          &quot;0323&quot;          &quot;0112&quot;          &quot;0323&quot;           &quot;023&quot;          &quot;0322&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;           &quot;021&quot;          &quot;0111&quot;           &quot;013&quot;          &quot;0321&quot;          &quot;0113&quot;           &quot;013&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;          &quot;0323&quot;          &quot;0322&quot;          &quot;0322&quot;          &quot;0111&quot;          &quot;0322&quot;           &quot;022&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;          &quot;0323&quot;          &quot;0312&quot;           &quot;022&quot;          &quot;0322&quot;          &quot;0324&quot;          &quot;0312&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;          &quot;0322&quot;           &quot;023&quot;           &quot;013&quot;           &quot;023&quot;           &quot;013&quot;           &quot;022&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;           &quot;022&quot;          &quot;0311&quot;          &quot;0322&quot;          &quot;0311&quot;           &quot;021&quot;          &quot;0312&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;           &quot;023&quot;          &quot;0323&quot;          &quot;0321&quot;           &quot;022&quot;          &quot;0311&quot;           &quot;012&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;          &quot;0111&quot;          &quot;0321&quot;          &quot;0113&quot;          &quot;0311&quot;          &quot;0311&quot;          &quot;0111&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;           &quot;012&quot;           &quot;022&quot;           &quot;023&quot;          &quot;0323&quot;          &quot;0322&quot;           &quot;012&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;          &quot;0111&quot;          &quot;0322&quot;          &quot;0111&quot;          &quot;0111&quot;          &quot;0323&quot;           &quot;021&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;          &quot;0322&quot;          &quot;0324&quot;          &quot;0312&quot;          &quot;0322&quot;          &quot;0311&quot;          &quot;0312&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;          &quot;0111&quot;           &quot;012&quot;          &quot;0312&quot;          &quot;0112&quot;          &quot;0321&quot;           &quot;012&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;           &quot;013&quot;          &quot;0322&quot;          &quot;0322&quot;           &quot;012&quot;          &quot;0111&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;          &quot;0113&quot;           &quot;022&quot;          &quot;0322&quot;          &quot;0323&quot;          &quot;0311&quot;          &quot;0321&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;           &quot;022&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;023&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;          &quot;0111&quot;          &quot;0321&quot;           &quot;022&quot;          &quot;0311&quot;           &quot;021&quot;           &quot;021&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;           &quot;021&quot;           &quot;021&quot;          &quot;0112&quot;           &quot;012&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-2-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-2-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-3'>
<p><a id='tab-get-classes-from-hierarchical-partition-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3210))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;           &quot;022&quot;           &quot;022&quot;          &quot;0321&quot;          &quot;0321&quot;           &quot;022&quot;           &quot;031&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;          &quot;0323&quot;          &quot;0112&quot;          &quot;0323&quot;           &quot;023&quot;          &quot;0322&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;           &quot;021&quot;          &quot;0111&quot;           &quot;013&quot;          &quot;0321&quot;          &quot;0113&quot;           &quot;013&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;          &quot;0323&quot;          &quot;0322&quot;          &quot;0322&quot;          &quot;0111&quot;          &quot;0322&quot;           &quot;022&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;          &quot;0323&quot;           &quot;031&quot;           &quot;022&quot;          &quot;0322&quot;          &quot;0324&quot;           &quot;031&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;          &quot;0322&quot;           &quot;023&quot;           &quot;013&quot;           &quot;023&quot;           &quot;013&quot;           &quot;022&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;           &quot;022&quot;           &quot;031&quot;          &quot;0322&quot;           &quot;031&quot;           &quot;021&quot;           &quot;031&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;           &quot;023&quot;          &quot;0323&quot;          &quot;0321&quot;           &quot;022&quot;           &quot;031&quot;           &quot;012&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;          &quot;0111&quot;          &quot;0321&quot;          &quot;0113&quot;           &quot;031&quot;           &quot;031&quot;          &quot;0111&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;           &quot;012&quot;           &quot;022&quot;           &quot;023&quot;          &quot;0323&quot;          &quot;0322&quot;           &quot;012&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;          &quot;0111&quot;          &quot;0322&quot;          &quot;0111&quot;          &quot;0111&quot;          &quot;0323&quot;           &quot;021&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;          &quot;0322&quot;          &quot;0324&quot;           &quot;031&quot;          &quot;0322&quot;           &quot;031&quot;           &quot;031&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;          &quot;0111&quot;           &quot;012&quot;           &quot;031&quot;          &quot;0112&quot;          &quot;0321&quot;           &quot;012&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;           &quot;013&quot;          &quot;0322&quot;          &quot;0322&quot;           &quot;012&quot;          &quot;0111&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;          &quot;0113&quot;           &quot;022&quot;          &quot;0322&quot;          &quot;0323&quot;           &quot;031&quot;          &quot;0321&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;           &quot;022&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;023&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;          &quot;0111&quot;          &quot;0321&quot;           &quot;022&quot;           &quot;031&quot;           &quot;021&quot;           &quot;021&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;           &quot;021&quot;           &quot;021&quot;          &quot;0112&quot;           &quot;012&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-3-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-3-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-4'>
<p><a id='tab-get-classes-from-hierarchical-partition-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3371))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;           &quot;022&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;            &quot;03&quot;          &quot;0112&quot;            &quot;03&quot;           &quot;023&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;           &quot;021&quot;          &quot;0111&quot;           &quot;013&quot;            &quot;03&quot;          &quot;0113&quot;           &quot;013&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;          &quot;0111&quot;            &quot;03&quot;           &quot;022&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;            &quot;03&quot;           &quot;023&quot;           &quot;013&quot;           &quot;023&quot;           &quot;013&quot;           &quot;022&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;           &quot;021&quot;            &quot;03&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;          &quot;0111&quot;            &quot;03&quot;          &quot;0113&quot;            &quot;03&quot;            &quot;03&quot;          &quot;0111&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;           &quot;012&quot;           &quot;022&quot;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;          &quot;0111&quot;            &quot;03&quot;          &quot;0111&quot;          &quot;0111&quot;            &quot;03&quot;           &quot;021&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;          &quot;0111&quot;           &quot;012&quot;            &quot;03&quot;          &quot;0112&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;           &quot;013&quot;            &quot;03&quot;            &quot;03&quot;           &quot;012&quot;          &quot;0111&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;          &quot;0113&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;           &quot;022&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;022&quot;          &quot;0111&quot;           &quot;023&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;          &quot;0111&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;           &quot;021&quot;           &quot;021&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;           &quot;021&quot;           &quot;021&quot;          &quot;0112&quot;           &quot;012&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-4-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-4-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-5'>
<p><a id='tab-get-classes-from-hierarchical-partition-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 3794))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;           &quot;022&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;           &quot;023&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;           &quot;021&quot;           &quot;011&quot;           &quot;013&quot;            &quot;03&quot;           &quot;011&quot;           &quot;013&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;           &quot;022&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;            &quot;03&quot;           &quot;023&quot;           &quot;013&quot;           &quot;023&quot;           &quot;013&quot;           &quot;022&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;           &quot;021&quot;            &quot;03&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;           &quot;011&quot;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;            &quot;03&quot;           &quot;011&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;           &quot;012&quot;           &quot;022&quot;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;           &quot;011&quot;            &quot;03&quot;           &quot;011&quot;           &quot;011&quot;            &quot;03&quot;           &quot;021&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;           &quot;011&quot;           &quot;012&quot;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;           &quot;013&quot;            &quot;03&quot;            &quot;03&quot;           &quot;012&quot;           &quot;011&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;           &quot;011&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;           &quot;022&quot;           &quot;022&quot;           &quot;011&quot;           &quot;022&quot;           &quot;011&quot;           &quot;023&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;           &quot;011&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;           &quot;021&quot;           &quot;021&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;           &quot;021&quot;           &quot;021&quot;           &quot;011&quot;           &quot;012&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-5-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-5-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-6'>
<p><a id='tab-get-classes-from-hierarchical-partition-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 14315))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;           &quot;022&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;           &quot;023&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;           &quot;021&quot;           &quot;011&quot;           &quot;013&quot;            &quot;03&quot;           &quot;011&quot;           &quot;013&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;           &quot;022&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;            &quot;03&quot;           &quot;023&quot;           &quot;013&quot;           &quot;023&quot;           &quot;013&quot;           &quot;022&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;           &quot;021&quot;            &quot;03&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;           &quot;011&quot;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;            &quot;03&quot;           &quot;011&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;           &quot;012&quot;           &quot;022&quot;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;           &quot;011&quot;            &quot;03&quot;           &quot;011&quot;           &quot;011&quot;            &quot;03&quot;           &quot;021&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;           &quot;011&quot;           &quot;012&quot;            &quot;03&quot;           &quot;011&quot;            &quot;03&quot;           &quot;012&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;           &quot;013&quot;            &quot;03&quot;            &quot;03&quot;           &quot;012&quot;           &quot;011&quot;           &quot;012&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;           &quot;011&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;           &quot;022&quot;           &quot;022&quot;           &quot;011&quot;           &quot;022&quot;           &quot;011&quot;           &quot;023&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;           &quot;011&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;           &quot;021&quot;           &quot;021&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;           &quot;021&quot;           &quot;021&quot;           &quot;011&quot;           &quot;012&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-6-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-6-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-7'>
<p><a id='tab-get-classes-from-hierarchical-partition-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 14944))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;           &quot;022&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;           &quot;023&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;           &quot;021&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;           &quot;022&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;            &quot;03&quot;           &quot;023&quot;            &quot;01&quot;           &quot;023&quot;            &quot;01&quot;           &quot;022&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;           &quot;021&quot;            &quot;03&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;            &quot;01&quot;           &quot;022&quot;           &quot;023&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;           &quot;021&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;            &quot;01&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;            &quot;01&quot;           &quot;022&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;           &quot;022&quot;           &quot;022&quot;            &quot;01&quot;           &quot;022&quot;            &quot;01&quot;           &quot;023&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;            &quot;01&quot;            &quot;03&quot;           &quot;022&quot;            &quot;03&quot;           &quot;021&quot;           &quot;021&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;           &quot;021&quot;           &quot;021&quot;            &quot;01&quot;            &quot;01&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-7-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-7-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-get-classes-from-hierarchical-partition-8'>
<p><a id='tab-get-classes-from-hierarchical-partition-8-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">get_classes(res_rh, merge_node = merge_node_param(min_n_signatures = 24376))
</code></pre>

<pre><code>#&gt; TCGA.F5.6812.01 TCGA.BM.6198.01 TCGA.AH.6644.01 TCGA.AH.6903.01 TCGA.G5.6572.02 TCGA.DC.6157.01 
#&gt;            &quot;02&quot;            &quot;02&quot;            &quot;03&quot;            &quot;03&quot;            &quot;02&quot;            &quot;03&quot; 
#&gt; TCGA.AG.3592.01 TCGA.AG.3591.01 TCGA.DT.5265.01 TCGA.EI.6506.01 TCGA.CI.6620.01 TCGA.AH.6549.01 
#&gt;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;            &quot;02&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.AG.A036.11 TCGA.EI.6514.01 TCGA.DY.A1DE.01 TCGA.AG.3731.01 TCGA.EI.6510.01 TCGA.EI.6513.01 
#&gt;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.G5.6233.01 TCGA.F5.6465.01 TCGA.DY.A1H8.01 TCGA.AG.A026.01 TCGA.CL.5917.01 TCGA.AF.4110.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;            &quot;02&quot; 
#&gt; TCGA.EI.6511.01 TCGA.CI.6619.01 TCGA.AH.6544.01 TCGA.AF.6136.01 TCGA.EI.7004.01 TCGA.F5.6702.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;02&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.EI.6512.01 TCGA.F5.6861.01 TCGA.F5.6810.01 TCGA.AF.2690.01 TCGA.EF.5830.01 TCGA.EI.6881.01 
#&gt;            &quot;03&quot;            &quot;02&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;02&quot; 
#&gt; TCGA.AF.2693.01 TCGA.DY.A0XA.01 TCGA.F5.6863.01 TCGA.AF.6655.01 TCGA.AG.3731.11 TCGA.CI.6624.01 
#&gt;            &quot;02&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;02&quot;            &quot;03&quot; 
#&gt; TCGA.DC.4745.01 TCGA.EI.6883.01 TCGA.AG.A036.01 TCGA.EI.6507.01 TCGA.CI.6623.01 TCGA.DC.5337.01 
#&gt;            &quot;02&quot;            &quot;03&quot;            &quot;03&quot;            &quot;02&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.CL.5918.01 TCGA.DC.6156.01 TCGA.AG.3725.01 TCGA.F5.6864.01 TCGA.DC.6160.01 TCGA.AF.3911.01 
#&gt;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.EI.6508.01 TCGA.EI.6917.01 TCGA.DC.6681.01 TCGA.F5.6814.01 TCGA.F5.6464.01 TCGA.DC.6158.01 
#&gt;            &quot;01&quot;            &quot;02&quot;            &quot;02&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.DC.5869.01 TCGA.AF.A56N.01 TCGA.AG.4022.01 TCGA.DY.A1DG.01 TCGA.EF.5831.01 TCGA.AG.3725.11 
#&gt;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;02&quot; 
#&gt; TCGA.AG.3732.01 TCGA.DY.A1DC.01 TCGA.EI.6885.01 TCGA.AF.A56L.01 TCGA.AF.A56K.01 TCGA.AG.A01Y.01 
#&gt;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.DC.6683.01 TCGA.AH.6897.01 TCGA.AF.2687.01 TCGA.EI.6882.01 TCGA.AH.6643.01 TCGA.AF.6672.01 
#&gt;            &quot;01&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot;            &quot;03&quot;            &quot;01&quot; 
#&gt; TCGA.DY.A1DF.01 TCGA.DC.6155.01 TCGA.CL.4957.01 TCGA.G5.6641.01 TCGA.AG.3742.01 TCGA.AG.4021.01 
#&gt;            &quot;01&quot;            &quot;03&quot;            &quot;03&quot;            &quot;01&quot;            &quot;01&quot;            &quot;01&quot; 
#&gt; TCGA.AG.A01W.01 TCGA.F5.6813.01 TCGA.F5.6571.01 TCGA.DC.6682.01 TCGA.EI.6509.01 TCGA.CI.6622.01 
#&gt;            &quot;01&quot;            &quot;02&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot;            &quot;03&quot; 
#&gt; TCGA.G5.6572.01 TCGA.CI.6621.01 TCGA.F5.6811.01 TCGA.G5.6235.01 TCGA.DC.6154.01 TCGA.AH.6547.01 
#&gt;            &quot;02&quot;            &quot;02&quot;            &quot;01&quot;            &quot;02&quot;            &quot;01&quot;            &quot;02&quot; 
#&gt; TCGA.DY.A1DD.01 TCGA.EI.7002.01 TCGA.EI.6884.01 TCGA.DC.4749.01 TCGA.AG.A020.11 TCGA.AG.A01Y.11 
#&gt;            &quot;01&quot;            &quot;03&quot;            &quot;02&quot;            &quot;03&quot;            &quot;02&quot;            &quot;02&quot; 
#&gt; TCGA.AG.A01W.11 TCGA.AG.A02N.11 TCGA.AG.A02N.01 TCGA.AG.A020.01 
#&gt;            &quot;02&quot;            &quot;02&quot;            &quot;01&quot;            &quot;01&quot;
</code></pre>

<script>
$('#tab-get-classes-from-hierarchical-partition-8-a').parent().next().next().hide();
$('#tab-get-classes-from-hierarchical-partition-8-a').click(function(){
  $('#tab-get-classes-from-hierarchical-partition-8-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>



### Top rows heatmap

Heatmaps of the top rows:





```r
top_rows_heatmap(res_rh)
```

![plot of chunk top-rows-heatmap](figure_cola/top-rows-heatmap-1.png)

```
#> Error in h(simpleError(msg, call)) : 
#>   error in evaluating the argument 'object' in selecting a method for function 'draw': no applicable method for 'height' applied to an object of class "list"
```

Top rows on each node:


```r
top_rows_overlap(res_rh, method = "upset")
```

![plot of chunk top-rows-overlap](figure_cola/top-rows-overlap-1.png)


### UMAP plot

UMAP plot which shows how samples are separated.




<script>
$( function() {
	$( '#tabs-dimension-reduction-by-depth' ).tabs();
} );
</script>
<div id='tabs-dimension-reduction-by-depth'>
<ul>
<li><a href='#tab-dimension-reduction-by-depth-1'>n_signatures ≥ 1217</a></li>
<li><a href='#tab-dimension-reduction-by-depth-2'>n_signatures ≥ 2183</a></li>
<li><a href='#tab-dimension-reduction-by-depth-3'>n_signatures ≥ 3210</a></li>
<li><a href='#tab-dimension-reduction-by-depth-4'>n_signatures ≥ 3371</a></li>
<li><a href='#tab-dimension-reduction-by-depth-5'>n_signatures ≥ 3794</a></li>
<li><a href='#tab-dimension-reduction-by-depth-6'>n_signatures ≥ 14315</a></li>
<li><a href='#tab-dimension-reduction-by-depth-7'>n_signatures ≥ 14944</a></li>
<li><a href='#tab-dimension-reduction-by-depth-8'>n_signatures ≥ 24376</a></li>
</ul>
<div id='tab-dimension-reduction-by-depth-1'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 1217),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 1217),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-1-1.png" title="plot of chunk tab-dimension-reduction-by-depth-1" alt="plot of chunk tab-dimension-reduction-by-depth-1" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-2'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 2183),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 2183),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-2-1.png" title="plot of chunk tab-dimension-reduction-by-depth-2" alt="plot of chunk tab-dimension-reduction-by-depth-2" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-3'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3210),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3210),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-3-1.png" title="plot of chunk tab-dimension-reduction-by-depth-3" alt="plot of chunk tab-dimension-reduction-by-depth-3" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-4'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3371),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3371),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-4-1.png" title="plot of chunk tab-dimension-reduction-by-depth-4" alt="plot of chunk tab-dimension-reduction-by-depth-4" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-5'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3794),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 3794),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-5-1.png" title="plot of chunk tab-dimension-reduction-by-depth-5" alt="plot of chunk tab-dimension-reduction-by-depth-5" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-6'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 14315),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 14315),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-6-1.png" title="plot of chunk tab-dimension-reduction-by-depth-6" alt="plot of chunk tab-dimension-reduction-by-depth-6" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-7'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 14944),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 14944),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-7-1.png" title="plot of chunk tab-dimension-reduction-by-depth-7" alt="plot of chunk tab-dimension-reduction-by-depth-7" width="100%" /></p>

</div>
<div id='tab-dimension-reduction-by-depth-8'>
<pre><code class="r">par(mfrow = c(1, 2))
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 24376),
    method = &quot;UMAP&quot;, top_value_method = &quot;SD&quot;, top_n = 40000, scale_rows = FALSE)
dimension_reduction(res_rh, merge_node = merge_node_param(min_n_signatures = 24376),
    method = &quot;UMAP&quot;, top_value_method = &quot;ATC&quot;, top_n = 40000, scale_rows = TRUE)
</code></pre>

<p><img src="figure_cola/tab-dimension-reduction-by-depth-8-1.png" title="plot of chunk tab-dimension-reduction-by-depth-8" alt="plot of chunk tab-dimension-reduction-by-depth-8" width="100%" /></p>

</div>
</div>




### Signature heatmap

Signatures on the heatmap are the union of all signatures found on every node
on the hierarchy. The number of k-means on rows are automatically selected by the function.




<script>
$( function() {
	$( '#tabs-get-signatures-from-hierarchical-partition' ).tabs();
} );
</script>
<div id='tabs-get-signatures-from-hierarchical-partition'>
<ul>
<li><a href='#tab-get-signatures-from-hierarchical-partition-1'>n_signatures ≥ 1217</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-2'>n_signatures ≥ 2183</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-3'>n_signatures ≥ 3210</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-4'>n_signatures ≥ 3371</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-5'>n_signatures ≥ 3794</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-6'>n_signatures ≥ 14315</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-7'>n_signatures ≥ 14944</a></li>
<li><a href='#tab-get-signatures-from-hierarchical-partition-8'>n_signatures ≥ 24376</a></li>
</ul>
<div id='tab-get-signatures-from-hierarchical-partition-1'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 1217))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-1-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-1"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-2'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 2183))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-2-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-2"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-3'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 3210))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-3-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-3"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-4'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 3371))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-4-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-4"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-5'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 3794))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-5-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-5"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-6'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 14315))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-6-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-6"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-7'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 14944))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-7-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-7"/></p>

</div>
<div id='tab-get-signatures-from-hierarchical-partition-8'>
<pre><code class="r">get_signatures(res_rh, merge_node = merge_node_param(min_n_signatures = 24376))
</code></pre>

<p><img src="figure_cola/tab-get-signatures-from-hierarchical-partition-8-1.png" alt="plot of chunk tab-get-signatures-from-hierarchical-partition-8"/></p>

</div>
</div>




Compare signatures from different nodes:


```r
compare_signatures(res_rh, verbose = FALSE)
```

![plot of chunk unnamed-chunk-24](figure_cola/unnamed-chunk-24-1.png)

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs. Note it only works on every node and the final signatures
are the union of all signatures of all nodes.


```r
# code only for demonstration
# e.g. to show the top 500 most significant rows on each node.
tb = get_signature(res_rh, top_signatures = 500)
```


## Results for each node


---------------------------------------------------




### Node0


Child nodes: 
                [Node01](#Node01)
        ,
                [Node02](#Node02)
        ,
                [Node03](#Node03)
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["0"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 106 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'kmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 3.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-0-collect-plots](figure_cola/node-0-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-0-select-partition-number](figure_cola/node-0-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           0.999       0.999         0.4963 0.504   0.504
#> 3 3 1.000           0.985       0.989         0.3147 0.651   0.418
#> 4 4 0.739           0.742       0.877         0.1298 0.789   0.487
#> 5 5 0.734           0.577       0.789         0.0650 0.836   0.492
#> 6 6 0.762           0.749       0.836         0.0456 0.896   0.571
#> 7 7 0.810           0.732       0.852         0.0285 0.994   0.961
#> 8 8 0.833           0.753       0.834         0.0198 0.981   0.881
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 3
#> attr(,"optional")
#> [1] 2
```

There is also optional best $k$ = 2 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-0-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-0-get-classes'>
<ul>
<li><a href='#tab-node-0-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-0-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-0-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-0-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-0-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-0-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-0-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-0-get-classes-1'>
<p><a id='tab-node-0-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2
#&gt; TCGA.F5.6812.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.BM.6198.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AH.6644.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AH.6903.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.G5.6572.02     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DC.6157.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.3592.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.3591.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DT.5265.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6506.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.CI.6620.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AH.6549.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.A036.11     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6514.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DY.A1DE.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.3731.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6510.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6513.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.G5.6233.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.F5.6465.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DY.A1H8.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.A026.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.CL.5917.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.4110.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6511.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.CI.6619.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AH.6544.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AF.6136.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.7004.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.F5.6702.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6512.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.F5.6861.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.F5.6810.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.2690.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EF.5830.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6881.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AF.2693.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DY.A0XA.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.F5.6863.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AF.6655.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AG.3731.11     2   0.000      0.999 0.00 1.00
#&gt; TCGA.CI.6624.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DC.4745.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6883.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AG.A036.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6507.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.CI.6623.01     2   0.141      0.980 0.02 0.98
#&gt; TCGA.DC.5337.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.CL.5918.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DC.6156.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.3725.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.F5.6864.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DC.6160.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AF.3911.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6508.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6917.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DC.6681.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.F5.6814.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.F5.6464.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DC.6158.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DC.5869.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.A56N.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.4022.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DY.A1DG.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EF.5831.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.3725.11     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AG.3732.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DY.A1DC.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6885.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.A56L.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.A56K.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.A01Y.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DC.6683.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AH.6897.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.2687.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6882.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AH.6643.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.6672.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DY.A1DF.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DC.6155.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.CL.4957.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.G5.6641.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.3742.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.4021.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.A01W.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.F5.6813.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.F5.6571.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DC.6682.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.EI.6509.01     2   0.141      0.980 0.02 0.98
#&gt; TCGA.CI.6622.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.G5.6572.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.CI.6621.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.F5.6811.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.G5.6235.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DC.6154.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AH.6547.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DY.A1DD.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.7002.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6884.01     2   0.000      0.999 0.00 1.00
#&gt; TCGA.DC.4749.01     2   0.141      0.980 0.02 0.98
#&gt; TCGA.AG.A020.11     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AG.A01Y.11     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AG.A01W.11     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AG.A02N.11     2   0.000      0.999 0.00 1.00
#&gt; TCGA.AG.A02N.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.A020.01     1   0.000      1.000 1.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-1-a').parent().next().next().hide();
$('#tab-node-0-get-classes-1-a').click(function(){
  $('#tab-node-0-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-2'>
<p><a id='tab-node-0-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.F5.6812.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.BM.6198.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.AH.6644.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AH.6903.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.G5.6572.02     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.DC.6157.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.AG.3592.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.AG.3591.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DT.5265.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.EI.6506.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.CI.6620.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.AH.6549.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AG.A036.11     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.EI.6514.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DY.A1DE.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AG.3731.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.EI.6510.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.EI.6513.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.G5.6233.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.F5.6465.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.DY.A1H8.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AG.A026.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.CL.5917.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AF.4110.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.EI.6511.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.CI.6619.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AH.6544.01     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.AF.6136.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.EI.7004.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.F5.6702.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.EI.6512.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.F5.6861.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.F5.6810.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AF.2690.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.EF.5830.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.EI.6881.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.AF.2693.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.DY.A0XA.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.F5.6863.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AF.6655.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AG.3731.11     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.CI.6624.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.DC.4745.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.EI.6883.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AG.A036.01     3   0.334      0.882 0.12 0.00 0.88
#&gt; TCGA.EI.6507.01     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.CI.6623.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.DC.5337.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.CL.5918.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DC.6156.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.AG.3725.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.F5.6864.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.DC.6160.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AF.3911.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.EI.6508.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.EI.6917.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.DC.6681.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.F5.6814.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.F5.6464.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.DC.6158.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DC.5869.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AF.A56N.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AG.4022.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DY.A1DG.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.EF.5831.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.AG.3725.11     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.AG.3732.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.DY.A1DC.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.EI.6885.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.AF.A56L.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AF.A56K.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AG.A01Y.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.DC.6683.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AH.6897.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AF.2687.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.EI.6882.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AH.6643.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.AF.6672.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DY.A1DF.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DC.6155.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.CL.4957.01     3   0.153      0.964 0.04 0.00 0.96
#&gt; TCGA.G5.6641.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AG.3742.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AG.4021.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.F5.6813.01     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.F5.6571.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.DC.6682.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.EI.6509.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.CI.6622.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.G5.6572.01     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.CI.6621.01     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.F5.6811.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.G5.6235.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.DC.6154.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AH.6547.01     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.DY.A1DD.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.EI.7002.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.EI.6884.01     2   0.153      0.978 0.00 0.96 0.04
#&gt; TCGA.DC.4749.01     3   0.000      0.985 0.00 0.00 1.00
#&gt; TCGA.AG.A020.11     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.AG.A01Y.11     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.AG.A01W.11     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.AG.A02N.11     2   0.000      0.979 0.00 1.00 0.00
#&gt; TCGA.AG.A02N.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AG.A020.01     1   0.000      1.000 1.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-2-a').parent().next().next().hide();
$('#tab-node-0-get-classes-2-a').click(function(){
  $('#tab-node-0-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-3'>
<p><a id='tab-node-0-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.F5.6812.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.BM.6198.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.AH.6644.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.AH.6903.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.G5.6572.02     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.DC.6157.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.3592.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.3591.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.DT.5265.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.EI.6506.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.CI.6620.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AH.6549.01     1  0.4406      0.694 0.70 0.00 0.30 0.00
#&gt; TCGA.AG.A036.11     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6514.01     3  0.3801      0.542 0.22 0.00 0.78 0.00
#&gt; TCGA.DY.A1DE.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.3731.01     4  0.4522      0.284 0.00 0.00 0.32 0.68
#&gt; TCGA.EI.6510.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6513.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.G5.6233.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.F5.6465.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.DY.A1H8.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.AG.A026.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.CL.5917.01     3  0.0707      0.809 0.00 0.00 0.98 0.02
#&gt; TCGA.AF.4110.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.EI.6511.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.CI.6619.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.AH.6544.01     2  0.4277      0.575 0.00 0.72 0.00 0.28
#&gt; TCGA.AF.6136.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.EI.7004.01     4  0.4134      0.433 0.00 0.00 0.26 0.74
#&gt; TCGA.F5.6702.01     4  0.4134      0.433 0.00 0.00 0.26 0.74
#&gt; TCGA.EI.6512.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.F5.6861.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.F5.6810.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.AF.2690.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.EF.5830.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6881.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.AF.2693.01     4  0.2647      0.698 0.00 0.12 0.00 0.88
#&gt; TCGA.DY.A0XA.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.F5.6863.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.AF.6655.01     4  0.1211      0.724 0.00 0.00 0.04 0.96
#&gt; TCGA.AG.3731.11     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.CI.6624.01     4  0.4134      0.433 0.00 0.00 0.26 0.74
#&gt; TCGA.DC.4745.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.EI.6883.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.AG.A036.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.EI.6507.01     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.CI.6623.01     3  0.4790      0.563 0.00 0.00 0.62 0.38
#&gt; TCGA.DC.5337.01     1  0.3801      0.773 0.78 0.00 0.22 0.00
#&gt; TCGA.CL.5918.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.6156.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.3725.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6864.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.DC.6160.01     4  0.4977     -0.208 0.00 0.00 0.46 0.54
#&gt; TCGA.AF.3911.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6508.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6917.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.DC.6681.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.F5.6814.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.F5.6464.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.DC.6158.01     3  0.4624      0.257 0.34 0.00 0.66 0.00
#&gt; TCGA.DC.5869.01     1  0.4406      0.694 0.70 0.00 0.30 0.00
#&gt; TCGA.AF.A56N.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.4022.01     3  0.1211      0.787 0.04 0.00 0.96 0.00
#&gt; TCGA.DY.A1DG.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.EF.5831.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.3725.11     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.4134      0.706 0.00 0.00 0.74 0.26
#&gt; TCGA.DY.A1DC.01     4  0.0707      0.735 0.00 0.00 0.02 0.98
#&gt; TCGA.EI.6885.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AF.A56L.01     3  0.4406      0.681 0.00 0.00 0.70 0.30
#&gt; TCGA.AF.A56K.01     3  0.3801      0.727 0.00 0.00 0.78 0.22
#&gt; TCGA.AG.A01Y.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.DC.6683.01     1  0.4713      0.597 0.64 0.00 0.36 0.00
#&gt; TCGA.AH.6897.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.AF.2687.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.EI.6882.01     1  0.3610      0.789 0.80 0.00 0.20 0.00
#&gt; TCGA.AH.6643.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.AF.6672.01     1  0.4406      0.694 0.70 0.00 0.30 0.00
#&gt; TCGA.DY.A1DF.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.CL.4957.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.G5.6641.01     1  0.4406      0.694 0.70 0.00 0.30 0.00
#&gt; TCGA.AG.3742.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.4021.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     3  0.4134      0.462 0.26 0.00 0.74 0.00
#&gt; TCGA.F5.6813.01     2  0.4277      0.575 0.00 0.72 0.00 0.28
#&gt; TCGA.F5.6571.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.DC.6682.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.EI.6509.01     3  0.4994      0.345 0.00 0.00 0.52 0.48
#&gt; TCGA.CI.6622.01     4  0.0000      0.745 0.00 0.00 0.00 1.00
#&gt; TCGA.G5.6572.01     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.CI.6621.01     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6811.01     3  0.1211      0.787 0.04 0.00 0.96 0.00
#&gt; TCGA.G5.6235.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.DC.6154.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.AH.6547.01     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.DY.A1DD.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.7002.01     3  0.0000      0.813 0.00 0.00 1.00 0.00
#&gt; TCGA.EI.6884.01     4  0.4406      0.585 0.00 0.30 0.00 0.70
#&gt; TCGA.DC.4749.01     3  0.4994      0.345 0.00 0.00 0.52 0.48
#&gt; TCGA.AG.A020.11     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A01Y.11     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A01W.11     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A02N.11     2  0.0000      0.948 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.A020.01     1  0.0000      0.915 1.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-3-a').parent().next().next().hide();
$('#tab-node-0-get-classes-3-a').click(function(){
  $('#tab-node-0-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-4'>
<p><a id='tab-node-0-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.F5.6812.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.BM.6198.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.AH.6644.01     3  0.0000     0.6421 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.AH.6903.01     4  0.4263     0.7651 0.18 0.00 0.06 0.76 0.00
#&gt; TCGA.G5.6572.02     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.6157.01     3  0.4307    -0.2068 0.00 0.00 0.50 0.00 0.50
#&gt; TCGA.AG.3592.01     3  0.1410     0.6030 0.00 0.00 0.94 0.00 0.06
#&gt; TCGA.AG.3591.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.DT.5265.01     4  0.4263     0.7651 0.18 0.00 0.06 0.76 0.00
#&gt; TCGA.EI.6506.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.CI.6620.01     5  0.4307     0.1402 0.00 0.00 0.50 0.00 0.50
#&gt; TCGA.AH.6549.01     5  0.0000     0.4252 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.AG.A036.11     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     5  0.3983     0.4520 0.00 0.00 0.34 0.00 0.66
#&gt; TCGA.DY.A1DE.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.AG.3731.01     3  0.4854     0.5381 0.26 0.00 0.68 0.06 0.00
#&gt; TCGA.EI.6510.01     1  0.4307     0.8222 0.50 0.00 0.00 0.00 0.50
#&gt; TCGA.EI.6513.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.G5.6233.01     4  0.4263     0.7651 0.18 0.00 0.06 0.76 0.00
#&gt; TCGA.F5.6465.01     3  0.3895     0.2179 0.00 0.00 0.68 0.00 0.32
#&gt; TCGA.DY.A1H8.01     3  0.0000     0.6421 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A026.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.CL.5917.01     3  0.3868     0.5653 0.14 0.00 0.80 0.06 0.00
#&gt; TCGA.AF.4110.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.EI.6511.01     3  0.0000     0.6421 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.CI.6619.01     3  0.3424     0.6099 0.24 0.00 0.76 0.00 0.00
#&gt; TCGA.AH.6544.01     4  0.3983     0.4231 0.00 0.34 0.00 0.66 0.00
#&gt; TCGA.AF.6136.01     3  0.1410     0.6450 0.06 0.00 0.94 0.00 0.00
#&gt; TCGA.EI.7004.01     3  0.6705     0.0416 0.26 0.00 0.42 0.32 0.00
#&gt; TCGA.F5.6702.01     3  0.6705     0.0416 0.26 0.00 0.42 0.32 0.00
#&gt; TCGA.EI.6512.01     3  0.2020     0.6408 0.10 0.00 0.90 0.00 0.00
#&gt; TCGA.F5.6861.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.F5.6810.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.AF.2690.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.EF.5830.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.EI.6881.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.AF.2693.01     4  0.1648     0.8181 0.00 0.02 0.04 0.94 0.00
#&gt; TCGA.DY.A0XA.01     3  0.0000     0.6421 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6863.01     4  0.4263     0.7651 0.18 0.00 0.06 0.76 0.00
#&gt; TCGA.AF.6655.01     3  0.6746    -0.0968 0.26 0.00 0.38 0.36 0.00
#&gt; TCGA.AG.3731.11     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6624.01     3  0.6705     0.0416 0.26 0.00 0.42 0.32 0.00
#&gt; TCGA.DC.4745.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.EI.6883.01     4  0.3390     0.7943 0.10 0.00 0.06 0.84 0.00
#&gt; TCGA.AG.A036.01     5  0.4126     0.4004 0.00 0.00 0.38 0.00 0.62
#&gt; TCGA.EI.6507.01     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6623.01     3  0.3561     0.6003 0.26 0.00 0.74 0.00 0.00
#&gt; TCGA.DC.5337.01     5  0.0000     0.4252 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.CL.5918.01     5  0.4307    -0.8412 0.50 0.00 0.00 0.00 0.50
#&gt; TCGA.DC.6156.01     3  0.4302    -0.1598 0.00 0.00 0.52 0.00 0.48
#&gt; TCGA.AG.3725.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.F5.6864.01     3  0.1732     0.6416 0.08 0.00 0.92 0.00 0.00
#&gt; TCGA.DC.6160.01     3  0.4967     0.5272 0.28 0.00 0.66 0.06 0.00
#&gt; TCGA.AF.3911.01     5  0.4302    -0.8099 0.48 0.00 0.00 0.00 0.52
#&gt; TCGA.EI.6508.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.EI.6917.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.DC.6681.01     4  0.1410     0.8146 0.00 0.00 0.06 0.94 0.00
#&gt; TCGA.F5.6814.01     5  0.4126     0.4004 0.00 0.00 0.38 0.00 0.62
#&gt; TCGA.F5.6464.01     4  0.4263     0.7651 0.18 0.00 0.06 0.76 0.00
#&gt; TCGA.DC.6158.01     5  0.3895     0.4684 0.00 0.00 0.32 0.00 0.68
#&gt; TCGA.DC.5869.01     5  0.0000     0.4252 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.AF.A56N.01     3  0.1410     0.6030 0.00 0.00 0.94 0.00 0.06
#&gt; TCGA.AG.4022.01     5  0.4126     0.4004 0.00 0.00 0.38 0.00 0.62
#&gt; TCGA.DY.A1DG.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.EF.5831.01     3  0.3983     0.1745 0.00 0.00 0.66 0.00 0.34
#&gt; TCGA.AG.3725.11     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.0000     0.6421 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.DY.A1DC.01     4  0.6785     0.0611 0.28 0.00 0.36 0.36 0.00
#&gt; TCGA.EI.6885.01     5  0.5979     0.3030 0.12 0.00 0.36 0.00 0.52
#&gt; TCGA.AF.A56L.01     3  0.3274     0.6162 0.22 0.00 0.78 0.00 0.00
#&gt; TCGA.AF.A56K.01     3  0.0000     0.6421 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A01Y.01     5  0.7420     0.1713 0.16 0.00 0.36 0.06 0.42
#&gt; TCGA.DC.6683.01     5  0.2732     0.5437 0.00 0.00 0.16 0.00 0.84
#&gt; TCGA.AH.6897.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.AF.2687.01     3  0.4307    -0.2068 0.00 0.00 0.50 0.00 0.50
#&gt; TCGA.EI.6882.01     5  0.0000     0.4252 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.AH.6643.01     3  0.3983     0.1745 0.00 0.00 0.66 0.00 0.34
#&gt; TCGA.AF.6672.01     5  0.1648     0.4785 0.02 0.00 0.04 0.00 0.94
#&gt; TCGA.DY.A1DF.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.DC.6155.01     3  0.1410     0.6030 0.00 0.00 0.94 0.00 0.06
#&gt; TCGA.CL.4957.01     3  0.4307    -0.2068 0.00 0.00 0.50 0.00 0.50
#&gt; TCGA.G5.6641.01     5  0.0000     0.4252 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.AG.3742.01     1  0.4307     0.8222 0.50 0.00 0.00 0.00 0.50
#&gt; TCGA.AG.4021.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.AG.A01W.01     5  0.3983     0.4520 0.00 0.00 0.34 0.00 0.66
#&gt; TCGA.F5.6813.01     4  0.3983     0.4231 0.00 0.34 0.00 0.66 0.00
#&gt; TCGA.F5.6571.01     4  0.6732     0.1558 0.26 0.00 0.34 0.40 0.00
#&gt; TCGA.DC.6682.01     4  0.4854     0.6937 0.26 0.00 0.06 0.68 0.00
#&gt; TCGA.EI.6509.01     3  0.4967     0.5272 0.28 0.00 0.66 0.06 0.00
#&gt; TCGA.CI.6622.01     4  0.4263     0.7651 0.18 0.00 0.06 0.76 0.00
#&gt; TCGA.G5.6572.01     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6621.01     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6811.01     5  0.4126     0.4004 0.00 0.00 0.38 0.00 0.62
#&gt; TCGA.G5.6235.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.DC.6154.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
#&gt; TCGA.AH.6547.01     2  0.0609     0.9796 0.00 0.98 0.00 0.02 0.00
#&gt; TCGA.DY.A1DD.01     5  0.4302    -0.8099 0.48 0.00 0.00 0.00 0.52
#&gt; TCGA.EI.7002.01     3  0.1410     0.6030 0.00 0.00 0.94 0.00 0.06
#&gt; TCGA.EI.6884.01     4  0.1410     0.8203 0.00 0.06 0.00 0.94 0.00
#&gt; TCGA.DC.4749.01     3  0.4132     0.5820 0.26 0.00 0.72 0.02 0.00
#&gt; TCGA.AG.A020.11     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01Y.11     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.11     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.11     2  0.0000     0.9982 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     5  0.4302    -0.8099 0.48 0.00 0.00 0.00 0.52
#&gt; TCGA.AG.A020.01     1  0.4126     0.9773 0.62 0.00 0.00 0.00 0.38
</code></pre>

<script>
$('#tab-node-0-get-classes-4-a').parent().next().next().hide();
$('#tab-node-0-get-classes-4-a').click(function(){
  $('#tab-node-0-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-5'>
<p><a id='tab-node-0-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.F5.6812.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.BM.6198.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.AH.6644.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.AH.6903.01     4   0.392     0.5885 0.00 0.00 0.00 0.68 0.02 0.30
#&gt; TCGA.G5.6572.02     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.6157.01     3   0.386    -0.1997 0.00 0.00 0.52 0.00 0.48 0.00
#&gt; TCGA.AG.3592.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.AG.3591.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DT.5265.01     4   0.392     0.5885 0.00 0.00 0.00 0.68 0.02 0.30
#&gt; TCGA.EI.6506.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.CI.6620.01     5   0.425     0.7153 0.00 0.00 0.24 0.00 0.70 0.06
#&gt; TCGA.AH.6549.01     5   0.226     0.7817 0.14 0.00 0.00 0.00 0.86 0.00
#&gt; TCGA.AG.A036.11     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     5   0.375     0.7926 0.00 0.00 0.14 0.00 0.78 0.08
#&gt; TCGA.DY.A1DE.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3731.01     6   0.368     0.6333 0.00 0.00 0.18 0.02 0.02 0.78
#&gt; TCGA.EI.6510.01     1   0.375     0.8132 0.78 0.00 0.00 0.00 0.14 0.08
#&gt; TCGA.EI.6513.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.G5.6233.01     4   0.392     0.5885 0.00 0.00 0.00 0.68 0.02 0.30
#&gt; TCGA.F5.6465.01     3   0.412     0.5696 0.00 0.00 0.72 0.00 0.22 0.06
#&gt; TCGA.DY.A1H8.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.AG.A026.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CL.5917.01     3   0.450     0.3443 0.00 0.00 0.68 0.00 0.08 0.24
#&gt; TCGA.AF.4110.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6511.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.CI.6619.01     6   0.371     0.5286 0.00 0.00 0.26 0.00 0.02 0.72
#&gt; TCGA.AH.6544.01     4   0.279     0.6353 0.00 0.20 0.00 0.80 0.00 0.00
#&gt; TCGA.AF.6136.01     3   0.331     0.7651 0.00 0.00 0.78 0.00 0.02 0.20
#&gt; TCGA.EI.7004.01     6   0.383     0.6636 0.00 0.00 0.02 0.20 0.02 0.76
#&gt; TCGA.F5.6702.01     6   0.383     0.6636 0.00 0.00 0.02 0.20 0.02 0.76
#&gt; TCGA.EI.6512.01     3   0.331     0.7651 0.00 0.00 0.78 0.00 0.02 0.20
#&gt; TCGA.F5.6861.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6810.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.2690.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.EF.5830.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6881.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.AF.2693.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.DY.A0XA.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.F5.6863.01     4   0.427     0.5661 0.00 0.00 0.00 0.66 0.04 0.30
#&gt; TCGA.AF.6655.01     6   0.446     0.6231 0.00 0.00 0.04 0.24 0.02 0.70
#&gt; TCGA.AG.3731.11     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6624.01     6   0.383     0.6636 0.00 0.00 0.02 0.20 0.02 0.76
#&gt; TCGA.DC.4745.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6883.01     4   0.412     0.6496 0.00 0.00 0.00 0.72 0.06 0.22
#&gt; TCGA.AG.A036.01     5   0.279     0.7894 0.00 0.00 0.20 0.00 0.80 0.00
#&gt; TCGA.EI.6507.01     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6623.01     6   0.392     0.5504 0.00 0.00 0.30 0.00 0.02 0.68
#&gt; TCGA.DC.5337.01     5   0.279     0.7738 0.14 0.00 0.00 0.00 0.84 0.02
#&gt; TCGA.CL.5918.01     1   0.409     0.7810 0.74 0.00 0.00 0.00 0.18 0.08
#&gt; TCGA.DC.6156.01     5   0.425     0.7153 0.00 0.00 0.24 0.00 0.70 0.06
#&gt; TCGA.AG.3725.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6864.01     6   0.434    -0.1538 0.00 0.00 0.48 0.00 0.02 0.50
#&gt; TCGA.DC.6160.01     6   0.316     0.6171 0.00 0.00 0.18 0.00 0.02 0.80
#&gt; TCGA.AF.3911.01     1   0.409     0.7810 0.74 0.00 0.00 0.00 0.18 0.08
#&gt; TCGA.EI.6508.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6917.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.DC.6681.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6814.01     5   0.279     0.7894 0.00 0.00 0.20 0.00 0.80 0.00
#&gt; TCGA.F5.6464.01     4   0.392     0.5885 0.00 0.00 0.00 0.68 0.02 0.30
#&gt; TCGA.DC.6158.01     5   0.205     0.8208 0.00 0.00 0.12 0.00 0.88 0.00
#&gt; TCGA.DC.5869.01     5   0.279     0.7738 0.14 0.00 0.00 0.00 0.84 0.02
#&gt; TCGA.AF.A56N.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.AG.4022.01     5   0.205     0.8208 0.00 0.00 0.12 0.00 0.88 0.00
#&gt; TCGA.DY.A1DG.01     1   0.127     0.8983 0.94 0.00 0.00 0.00 0.00 0.06
#&gt; TCGA.EF.5831.01     3   0.245     0.6852 0.00 0.00 0.84 0.00 0.16 0.00
#&gt; TCGA.AG.3725.11     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.DY.A1DC.01     6   0.417     0.5476 0.00 0.00 0.00 0.28 0.04 0.68
#&gt; TCGA.EI.6885.01     5   0.438     0.7143 0.00 0.00 0.16 0.00 0.72 0.12
#&gt; TCGA.AF.A56L.01     6   0.387    -0.2225 0.00 0.00 0.50 0.00 0.00 0.50
#&gt; TCGA.AF.A56K.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.AG.A01Y.01     5   0.588     0.4288 0.00 0.00 0.26 0.00 0.48 0.26
#&gt; TCGA.DC.6683.01     5   0.332     0.8154 0.06 0.00 0.08 0.00 0.84 0.02
#&gt; TCGA.AH.6897.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.2687.01     5   0.425     0.7153 0.00 0.00 0.24 0.00 0.70 0.06
#&gt; TCGA.EI.6882.01     5   0.375     0.7286 0.14 0.00 0.00 0.00 0.78 0.08
#&gt; TCGA.AH.6643.01     3   0.245     0.6852 0.00 0.00 0.84 0.00 0.16 0.00
#&gt; TCGA.AF.6672.01     5   0.205     0.7910 0.12 0.00 0.00 0.00 0.88 0.00
#&gt; TCGA.DY.A1DF.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     3   0.331     0.7604 0.00 0.00 0.78 0.00 0.02 0.20
#&gt; TCGA.CL.4957.01     5   0.359     0.7420 0.00 0.00 0.24 0.00 0.74 0.02
#&gt; TCGA.G5.6641.01     5   0.226     0.7817 0.14 0.00 0.00 0.00 0.86 0.00
#&gt; TCGA.AG.3742.01     1   0.393     0.7984 0.76 0.00 0.00 0.00 0.16 0.08
#&gt; TCGA.AG.4021.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     5   0.258     0.8186 0.00 0.00 0.12 0.00 0.86 0.02
#&gt; TCGA.F5.6813.01     4   0.279     0.6353 0.00 0.20 0.00 0.80 0.00 0.00
#&gt; TCGA.F5.6571.01     6   0.486     0.5978 0.00 0.00 0.06 0.26 0.02 0.66
#&gt; TCGA.DC.6682.01     6   0.383     0.0639 0.00 0.00 0.00 0.44 0.00 0.56
#&gt; TCGA.EI.6509.01     6   0.320     0.5898 0.00 0.00 0.26 0.00 0.00 0.74
#&gt; TCGA.CI.6622.01     4   0.392     0.5885 0.00 0.00 0.00 0.68 0.02 0.30
#&gt; TCGA.G5.6572.01     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6621.01     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6811.01     5   0.205     0.8208 0.00 0.00 0.12 0.00 0.88 0.00
#&gt; TCGA.G5.6235.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.DC.6154.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AH.6547.01     2   0.226     0.8432 0.00 0.86 0.00 0.14 0.00 0.00
#&gt; TCGA.DY.A1DD.01     1   0.409     0.7810 0.74 0.00 0.00 0.00 0.18 0.08
#&gt; TCGA.EI.7002.01     3   0.263     0.8194 0.00 0.00 0.82 0.00 0.00 0.18
#&gt; TCGA.EI.6884.01     4   0.000     0.8400 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.DC.4749.01     6   0.392     0.5504 0.00 0.00 0.30 0.00 0.02 0.68
#&gt; TCGA.AG.A020.11     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01Y.11     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.11     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.11     2   0.000     0.9866 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     1   0.409     0.7810 0.74 0.00 0.00 0.00 0.18 0.08
#&gt; TCGA.AG.A020.01     1   0.000     0.9205 1.00 0.00 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-5-a').parent().next().next().hide();
$('#tab-node-0-get-classes-5-a').click(function(){
  $('#tab-node-0-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-6'>
<p><a id='tab-node-0-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.F5.6812.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.BM.6198.01     4  0.0863      0.778 0.00 0.00 0.00 0.96 0.00 0.00 0.04
#&gt; TCGA.AH.6644.01     3  0.0504      0.880 0.00 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.AH.6903.01     4  0.4622      0.453 0.00 0.00 0.00 0.56 0.02 0.38 0.04
#&gt; TCGA.G5.6572.02     2  0.2278      0.909 0.00 0.88 0.00 0.00 0.04 0.00 0.08
#&gt; TCGA.DC.6157.01     3  0.4461      0.276 0.00 0.00 0.62 0.00 0.32 0.04 0.02
#&gt; TCGA.AG.3592.01     3  0.0000      0.878 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3591.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DT.5265.01     4  0.4622      0.453 0.00 0.00 0.00 0.56 0.02 0.38 0.04
#&gt; TCGA.EI.6506.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6620.01     5  0.5363      0.482 0.00 0.00 0.22 0.00 0.60 0.04 0.14
#&gt; TCGA.AH.6549.01     5  0.1433      0.715 0.08 0.00 0.00 0.00 0.92 0.00 0.00
#&gt; TCGA.AG.A036.11     2  0.0000      0.937 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     5  0.3670      0.639 0.00 0.00 0.10 0.00 0.76 0.00 0.14
#&gt; TCGA.DY.A1DE.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3731.01     6  0.2654      0.825 0.00 0.00 0.10 0.00 0.02 0.86 0.02
#&gt; TCGA.EI.6510.01     1  0.4939      0.554 0.56 0.00 0.00 0.00 0.30 0.00 0.14
#&gt; TCGA.EI.6513.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.G5.6233.01     4  0.4622      0.453 0.00 0.00 0.00 0.56 0.02 0.38 0.04
#&gt; TCGA.F5.6465.01     3  0.4667      0.505 0.00 0.00 0.70 0.00 0.12 0.04 0.14
#&gt; TCGA.DY.A1H8.01     3  0.0504      0.880 0.00 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.AG.A026.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CL.5917.01     7  0.4033      0.601 0.00 0.00 0.22 0.00 0.00 0.08 0.70
#&gt; TCGA.AF.4110.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6511.01     3  0.0504      0.880 0.00 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.CI.6619.01     6  0.3965      0.663 0.00 0.00 0.10 0.00 0.02 0.76 0.12
#&gt; TCGA.AH.6544.01     4  0.4079      0.597 0.00 0.08 0.00 0.76 0.04 0.00 0.12
#&gt; TCGA.AF.6136.01     3  0.1363      0.839 0.00 0.00 0.94 0.00 0.02 0.04 0.00
#&gt; TCGA.EI.7004.01     6  0.2911      0.835 0.00 0.00 0.02 0.08 0.02 0.86 0.02
#&gt; TCGA.F5.6702.01     6  0.2911      0.835 0.00 0.00 0.02 0.08 0.02 0.86 0.02
#&gt; TCGA.EI.6512.01     3  0.1363      0.839 0.00 0.00 0.94 0.00 0.02 0.04 0.00
#&gt; TCGA.F5.6861.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6810.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.2690.01     4  0.0863      0.778 0.00 0.00 0.00 0.96 0.00 0.00 0.04
#&gt; TCGA.EF.5830.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6881.01     4  0.0863      0.778 0.00 0.00 0.00 0.96 0.00 0.00 0.04
#&gt; TCGA.AF.2693.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.DY.A0XA.01     3  0.0504      0.880 0.00 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.F5.6863.01     4  0.4622      0.453 0.00 0.00 0.00 0.56 0.02 0.38 0.04
#&gt; TCGA.AF.6655.01     6  0.1928      0.827 0.00 0.00 0.02 0.08 0.00 0.90 0.00
#&gt; TCGA.AG.3731.11     2  0.0000      0.937 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6624.01     6  0.2911      0.835 0.00 0.00 0.02 0.08 0.02 0.86 0.02
#&gt; TCGA.DC.4745.01     4  0.0863      0.778 0.00 0.00 0.00 0.96 0.00 0.00 0.04
#&gt; TCGA.EI.6883.01     4  0.4211      0.599 0.00 0.00 0.00 0.68 0.02 0.26 0.04
#&gt; TCGA.AG.A036.01     5  0.4466      0.623 0.00 0.00 0.20 0.00 0.70 0.04 0.06
#&gt; TCGA.EI.6507.01     2  0.2278      0.909 0.00 0.88 0.00 0.00 0.04 0.00 0.08
#&gt; TCGA.CI.6623.01     6  0.2376      0.822 0.00 0.00 0.12 0.00 0.02 0.86 0.00
#&gt; TCGA.DC.5337.01     5  0.1433      0.715 0.08 0.00 0.00 0.00 0.92 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.5047      0.515 0.52 0.00 0.00 0.00 0.34 0.00 0.14
#&gt; TCGA.DC.6156.01     5  0.5363      0.482 0.00 0.00 0.22 0.00 0.60 0.04 0.14
#&gt; TCGA.AG.3725.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6864.01     6  0.4939      0.513 0.00 0.00 0.20 0.00 0.02 0.64 0.14
#&gt; TCGA.DC.6160.01     6  0.2278      0.822 0.00 0.00 0.08 0.00 0.00 0.88 0.04
#&gt; TCGA.AF.3911.01     1  0.5047      0.515 0.52 0.00 0.00 0.00 0.34 0.00 0.14
#&gt; TCGA.EI.6508.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6917.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.6681.01     4  0.0504      0.786 0.00 0.00 0.00 0.98 0.00 0.00 0.02
#&gt; TCGA.F5.6814.01     5  0.4466      0.623 0.00 0.00 0.20 0.00 0.70 0.04 0.06
#&gt; TCGA.F5.6464.01     4  0.4622      0.453 0.00 0.00 0.00 0.56 0.02 0.38 0.04
#&gt; TCGA.DC.6158.01     5  0.2159      0.740 0.02 0.00 0.06 0.00 0.90 0.02 0.00
#&gt; TCGA.DC.5869.01     5  0.1433      0.715 0.08 0.00 0.00 0.00 0.92 0.00 0.00
#&gt; TCGA.AF.A56N.01     3  0.0000      0.878 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.4022.01     5  0.2163      0.733 0.00 0.00 0.10 0.00 0.88 0.02 0.00
#&gt; TCGA.DY.A1DG.01     1  0.2081      0.743 0.86 0.00 0.00 0.00 0.00 0.00 0.14
#&gt; TCGA.EF.5831.01     3  0.0863      0.852 0.00 0.00 0.96 0.00 0.00 0.04 0.00
#&gt; TCGA.AG.3725.11     2  0.0000      0.937 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.0504      0.880 0.00 0.00 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.DY.A1DC.01     6  0.3061      0.784 0.00 0.00 0.00 0.08 0.02 0.84 0.06
#&gt; TCGA.EI.6885.01     5  0.5083      0.336 0.00 0.00 0.06 0.00 0.56 0.04 0.34
#&gt; TCGA.AF.A56L.01     6  0.4992      0.510 0.00 0.00 0.28 0.00 0.02 0.60 0.10
#&gt; TCGA.AF.A56K.01     3  0.1006      0.874 0.00 0.00 0.96 0.00 0.00 0.02 0.02
#&gt; TCGA.AG.A01Y.01     7  0.4378      0.588 0.00 0.00 0.02 0.00 0.20 0.08 0.70
#&gt; TCGA.DC.6683.01     5  0.1664      0.737 0.02 0.00 0.06 0.00 0.92 0.00 0.00
#&gt; TCGA.AH.6897.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.2687.01     5  0.5363      0.482 0.00 0.00 0.22 0.00 0.60 0.04 0.14
#&gt; TCGA.EI.6882.01     5  0.3449      0.577 0.08 0.00 0.00 0.00 0.78 0.00 0.14
#&gt; TCGA.AH.6643.01     3  0.1718      0.821 0.00 0.00 0.92 0.00 0.00 0.04 0.04
#&gt; TCGA.AF.6672.01     5  0.1433      0.715 0.08 0.00 0.00 0.00 0.92 0.00 0.00
#&gt; TCGA.DY.A1DF.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     3  0.2912      0.705 0.00 0.00 0.82 0.00 0.00 0.04 0.14
#&gt; TCGA.CL.4957.01     5  0.5460      0.481 0.00 0.00 0.24 0.00 0.58 0.04 0.14
#&gt; TCGA.G5.6641.01     5  0.1433      0.715 0.08 0.00 0.00 0.00 0.92 0.00 0.00
#&gt; TCGA.AG.3742.01     1  0.5047      0.515 0.52 0.00 0.00 0.00 0.34 0.00 0.14
#&gt; TCGA.AG.4021.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     5  0.1433      0.735 0.00 0.00 0.08 0.00 0.92 0.00 0.00
#&gt; TCGA.F5.6813.01     4  0.4079      0.597 0.00 0.08 0.00 0.76 0.04 0.00 0.12
#&gt; TCGA.F5.6571.01     6  0.3485      0.776 0.00 0.00 0.02 0.10 0.02 0.82 0.04
#&gt; TCGA.DC.6682.01     6  0.2163      0.805 0.00 0.00 0.00 0.10 0.00 0.88 0.02
#&gt; TCGA.EI.6509.01     6  0.2163      0.828 0.00 0.00 0.10 0.00 0.00 0.88 0.02
#&gt; TCGA.CI.6622.01     4  0.4622      0.453 0.00 0.00 0.00 0.56 0.02 0.38 0.04
#&gt; TCGA.G5.6572.01     2  0.2278      0.909 0.00 0.88 0.00 0.00 0.04 0.00 0.08
#&gt; TCGA.CI.6621.01     2  0.2278      0.909 0.00 0.88 0.00 0.00 0.04 0.00 0.08
#&gt; TCGA.F5.6811.01     5  0.2163      0.733 0.00 0.00 0.10 0.00 0.88 0.02 0.00
#&gt; TCGA.G5.6235.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.6154.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AH.6547.01     2  0.3879      0.801 0.00 0.78 0.00 0.10 0.04 0.00 0.08
#&gt; TCGA.DY.A1DD.01     1  0.5047      0.515 0.52 0.00 0.00 0.00 0.34 0.00 0.14
#&gt; TCGA.EI.7002.01     3  0.0000      0.878 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6884.01     4  0.0000      0.791 0.00 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.4749.01     6  0.1886      0.822 0.00 0.00 0.12 0.00 0.00 0.88 0.00
#&gt; TCGA.AG.A020.11     2  0.0000      0.937 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01Y.11     2  0.0000      0.937 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.11     2  0.0000      0.937 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.11     2  0.0000      0.937 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     1  0.5047      0.515 0.52 0.00 0.00 0.00 0.34 0.00 0.14
#&gt; TCGA.AG.A020.01     1  0.0000      0.816 1.00 0.00 0.00 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-6-a').parent().next().next().hide();
$('#tab-node-0-get-classes-6-a').click(function(){
  $('#tab-node-0-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0-get-classes-7'>
<p><a id='tab-node-0-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7   p8
#&gt; TCGA.F5.6812.01     4  0.0000      0.893 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.BM.6198.01     4  0.1341      0.869 0.00 0.00 0.00 0.92 0.00 0.00 0.00 0.08
#&gt; TCGA.AH.6644.01     3  0.0471      0.849 0.00 0.00 0.98 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.AH.6903.01     8  0.5381      0.936 0.00 0.00 0.02 0.38 0.00 0.18 0.00 0.42
#&gt; TCGA.G5.6572.02     2  0.2020      0.909 0.00 0.90 0.00 0.00 0.02 0.00 0.02 0.06
#&gt; TCGA.DC.6157.01     3  0.5379      0.277 0.00 0.00 0.52 0.00 0.28 0.00 0.04 0.16
#&gt; TCGA.AG.3592.01     3  0.0471      0.849 0.00 0.00 0.98 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.AG.3591.01     1  0.0000      0.772 1.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DT.5265.01     8  0.4999      0.933 0.00 0.00 0.00 0.40 0.00 0.18 0.00 0.42
#&gt; TCGA.EI.6506.01     4  0.0000      0.893 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6620.01     5  0.5566      0.585 0.00 0.00 0.10 0.00 0.62 0.06 0.06 0.16
#&gt; TCGA.AH.6549.01     5  0.1091      0.712 0.06 0.00 0.00 0.00 0.94 0.00 0.00 0.00
#&gt; TCGA.AG.A036.11     2  0.0000      0.935 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     5  0.3036      0.630 0.00 0.00 0.04 0.00 0.78 0.00 0.18 0.00
#&gt; TCGA.DY.A1DE.01     1  0.0471      0.771 0.98 0.00 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.AG.3731.01     6  0.0808      0.819 0.00 0.00 0.04 0.00 0.00 0.96 0.00 0.00
#&gt; TCGA.EI.6510.01     1  0.4952      0.471 0.50 0.00 0.00 0.00 0.30 0.00 0.20 0.00
#&gt; TCGA.EI.6513.01     1  0.0471      0.771 0.98 0.00 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.G5.6233.01     8  0.5381      0.936 0.00 0.00 0.02 0.38 0.00 0.18 0.00 0.42
#&gt; TCGA.F5.6465.01     3  0.5887      0.406 0.00 0.00 0.56 0.00 0.16 0.04 0.06 0.18
#&gt; TCGA.DY.A1H8.01     3  0.1557      0.814 0.00 0.00 0.92 0.00 0.00 0.00 0.02 0.06
#&gt; TCGA.AG.A026.01     1  0.0000      0.772 1.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CL.5917.01     7  0.4428      0.867 0.00 0.00 0.08 0.00 0.04 0.02 0.72 0.14
#&gt; TCGA.AF.4110.01     4  0.0000      0.893 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6511.01     3  0.0471      0.839 0.00 0.00 0.98 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.CI.6619.01     6  0.2484      0.732 0.00 0.00 0.02 0.00 0.00 0.86 0.02 0.10
#&gt; TCGA.AH.6544.01     4  0.3627      0.722 0.00 0.04 0.00 0.78 0.02 0.00 0.02 0.14
#&gt; TCGA.AF.6136.01     3  0.1275      0.821 0.00 0.00 0.94 0.00 0.00 0.00 0.02 0.04
#&gt; TCGA.EI.7004.01     6  0.0808      0.827 0.00 0.00 0.00 0.04 0.00 0.96 0.00 0.00
#&gt; TCGA.F5.6702.01     6  0.0808      0.827 0.00 0.00 0.00 0.04 0.00 0.96 0.00 0.00
#&gt; TCGA.EI.6512.01     3  0.1275      0.821 0.00 0.00 0.94 0.00 0.00 0.00 0.02 0.04
#&gt; TCGA.F5.6861.01     4  0.0000      0.893 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6810.01     1  0.0000      0.772 1.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.2690.01     4  0.1341      0.869 0.00 0.00 0.00 0.92 0.00 0.00 0.00 0.08
#&gt; TCGA.EF.5830.01     1  0.0471      0.771 0.98 0.00 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.EI.6881.01     4  0.1804      0.863 0.00 0.00 0.00 0.90 0.00 0.00 0.02 0.08
#&gt; TCGA.AF.2693.01     4  0.0471      0.877 0.00 0.00 0.00 0.98 0.00 0.00 0.00 0.02
#&gt; TCGA.DY.A0XA.01     3  0.0941      0.834 0.00 0.00 0.96 0.00 0.00 0.00 0.02 0.02
#&gt; TCGA.F5.6863.01     8  0.4786      0.908 0.00 0.00 0.00 0.38 0.00 0.14 0.00 0.48
#&gt; TCGA.AF.6655.01     6  0.2591      0.794 0.00 0.00 0.00 0.04 0.00 0.86 0.02 0.08
#&gt; TCGA.AG.3731.11     2  0.0000      0.935 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6624.01     6  0.0808      0.827 0.00 0.00 0.00 0.04 0.00 0.96 0.00 0.00
#&gt; TCGA.DC.4745.01     4  0.1804      0.863 0.00 0.00 0.00 0.90 0.00 0.00 0.02 0.08
#&gt; TCGA.EI.6883.01     8  0.4216      0.790 0.00 0.00 0.00 0.44 0.00 0.06 0.00 0.50
#&gt; TCGA.AG.A036.01     5  0.4337      0.658 0.00 0.00 0.10 0.00 0.70 0.00 0.04 0.16
#&gt; TCGA.EI.6507.01     2  0.2020      0.909 0.00 0.90 0.00 0.00 0.02 0.00 0.02 0.06
#&gt; TCGA.CI.6623.01     6  0.2348      0.818 0.00 0.00 0.06 0.00 0.00 0.88 0.02 0.04
#&gt; TCGA.DC.5337.01     5  0.2407      0.677 0.06 0.00 0.00 0.00 0.86 0.00 0.08 0.00
#&gt; TCGA.CL.5918.01     1  0.5054      0.400 0.44 0.00 0.00 0.00 0.36 0.00 0.20 0.00
#&gt; TCGA.DC.6156.01     5  0.5851      0.538 0.00 0.00 0.12 0.00 0.58 0.06 0.06 0.18
#&gt; TCGA.AG.3725.01     1  0.0471      0.766 0.98 0.00 0.00 0.00 0.00 0.00 0.02 0.00
#&gt; TCGA.F5.6864.01     6  0.2807      0.710 0.00 0.00 0.04 0.00 0.00 0.84 0.02 0.10
#&gt; TCGA.DC.6160.01     6  0.2020      0.816 0.00 0.00 0.02 0.00 0.00 0.90 0.02 0.06
#&gt; TCGA.AF.3911.01     1  0.5054      0.400 0.44 0.00 0.00 0.00 0.36 0.00 0.20 0.00
#&gt; TCGA.EI.6508.01     1  0.0000      0.772 1.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6917.01     4  0.0000      0.893 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.6681.01     4  0.1947      0.655 0.00 0.00 0.00 0.86 0.00 0.00 0.00 0.14
#&gt; TCGA.F5.6814.01     5  0.4337      0.658 0.00 0.00 0.10 0.00 0.70 0.00 0.04 0.16
#&gt; TCGA.F5.6464.01     8  0.4999      0.933 0.00 0.00 0.00 0.40 0.00 0.18 0.00 0.42
#&gt; TCGA.DC.6158.01     5  0.2350      0.735 0.00 0.00 0.04 0.00 0.86 0.00 0.00 0.10
#&gt; TCGA.DC.5869.01     5  0.2407      0.677 0.06 0.00 0.00 0.00 0.86 0.00 0.08 0.00
#&gt; TCGA.AF.A56N.01     3  0.0471      0.849 0.00 0.00 0.98 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.AG.4022.01     5  0.2350      0.735 0.00 0.00 0.04 0.00 0.86 0.00 0.00 0.10
#&gt; TCGA.DY.A1DG.01     1  0.2114      0.691 0.84 0.00 0.00 0.00 0.00 0.00 0.16 0.00
#&gt; TCGA.EF.5831.01     3  0.0941      0.843 0.00 0.00 0.96 0.00 0.02 0.00 0.00 0.02
#&gt; TCGA.AG.3725.11     2  0.0000      0.935 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.0941      0.847 0.00 0.00 0.96 0.00 0.02 0.00 0.02 0.00
#&gt; TCGA.DY.A1DC.01     6  0.4137      0.212 0.00 0.00 0.00 0.02 0.00 0.50 0.02 0.46
#&gt; TCGA.EI.6885.01     5  0.4651      0.441 0.00 0.00 0.00 0.00 0.58 0.00 0.24 0.18
#&gt; TCGA.AF.A56L.01     6  0.2807      0.745 0.00 0.00 0.10 0.00 0.00 0.84 0.02 0.04
#&gt; TCGA.AF.A56K.01     3  0.2204      0.822 0.00 0.00 0.90 0.00 0.02 0.02 0.02 0.04
#&gt; TCGA.AG.A01Y.01     7  0.4204      0.867 0.00 0.00 0.00 0.00 0.12 0.04 0.72 0.12
#&gt; TCGA.DC.6683.01     5  0.2132      0.709 0.00 0.00 0.04 0.00 0.88 0.00 0.08 0.00
#&gt; TCGA.AH.6897.01     1  0.0471      0.771 0.98 0.00 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.AF.2687.01     5  0.5689      0.567 0.00 0.00 0.10 0.00 0.60 0.06 0.06 0.18
#&gt; TCGA.EI.6882.01     5  0.3431      0.560 0.06 0.00 0.00 0.00 0.74 0.00 0.20 0.00
#&gt; TCGA.AH.6643.01     3  0.3337      0.703 0.00 0.00 0.78 0.00 0.02 0.00 0.04 0.16
#&gt; TCGA.AF.6672.01     5  0.0808      0.713 0.04 0.00 0.00 0.00 0.96 0.00 0.00 0.00
#&gt; TCGA.DY.A1DF.01     1  0.0471      0.771 0.98 0.00 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.DC.6155.01     3  0.3744      0.661 0.00 0.00 0.74 0.00 0.02 0.00 0.06 0.18
#&gt; TCGA.CL.4957.01     5  0.4590      0.641 0.00 0.00 0.10 0.00 0.68 0.00 0.06 0.16
#&gt; TCGA.G5.6641.01     5  0.1091      0.712 0.06 0.00 0.00 0.00 0.94 0.00 0.00 0.00
#&gt; TCGA.AG.3742.01     1  0.5054      0.400 0.44 0.00 0.00 0.00 0.36 0.00 0.20 0.00
#&gt; TCGA.AG.4021.01     1  0.0000      0.772 1.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     5  0.2914      0.722 0.00 0.00 0.04 0.00 0.84 0.00 0.08 0.04
#&gt; TCGA.F5.6813.01     4  0.3627      0.722 0.00 0.04 0.00 0.78 0.02 0.00 0.02 0.14
#&gt; TCGA.F5.6571.01     6  0.4383      0.134 0.00 0.00 0.02 0.04 0.00 0.52 0.00 0.42
#&gt; TCGA.DC.6682.01     6  0.2165      0.795 0.00 0.00 0.00 0.06 0.00 0.88 0.00 0.06
#&gt; TCGA.EI.6509.01     6  0.2025      0.807 0.00 0.00 0.00 0.00 0.00 0.88 0.02 0.10
#&gt; TCGA.CI.6622.01     8  0.5445      0.913 0.00 0.00 0.02 0.36 0.00 0.20 0.00 0.42
#&gt; TCGA.G5.6572.01     2  0.2020      0.909 0.00 0.90 0.00 0.00 0.02 0.00 0.02 0.06
#&gt; TCGA.CI.6621.01     2  0.2020      0.909 0.00 0.90 0.00 0.00 0.02 0.00 0.02 0.06
#&gt; TCGA.F5.6811.01     5  0.2350      0.735 0.00 0.00 0.04 0.00 0.86 0.00 0.00 0.10
#&gt; TCGA.G5.6235.01     4  0.0471      0.874 0.00 0.00 0.00 0.98 0.00 0.02 0.00 0.00
#&gt; TCGA.DC.6154.01     1  0.0471      0.771 0.98 0.00 0.00 0.00 0.00 0.00 0.00 0.02
#&gt; TCGA.AH.6547.01     2  0.4186      0.678 0.00 0.72 0.00 0.18 0.02 0.00 0.02 0.06
#&gt; TCGA.DY.A1DD.01     1  0.5054      0.400 0.44 0.00 0.00 0.00 0.36 0.00 0.20 0.00
#&gt; TCGA.EI.7002.01     3  0.1408      0.843 0.00 0.00 0.94 0.00 0.02 0.00 0.02 0.02
#&gt; TCGA.EI.6884.01     4  0.0000      0.893 0.00 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.4749.01     6  0.2864      0.801 0.00 0.00 0.06 0.00 0.00 0.84 0.02 0.08
#&gt; TCGA.AG.A020.11     2  0.0000      0.935 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01Y.11     2  0.0000      0.935 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.11     2  0.0000      0.935 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.11     2  0.0000      0.935 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     1  0.5073      0.306 0.40 0.00 0.00 0.00 0.40 0.00 0.20 0.00
#&gt; TCGA.AG.A020.01     1  0.0000      0.772 1.00 0.00 0.00 0.00 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0-get-classes-7-a').parent().next().next().hide();
$('#tab-node-0-get-classes-7-a').click(function(){
  $('#tab-node-0-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-0-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-0-consensus-heatmap'>
<ul>
<li><a href='#tab-node-0-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-0-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-0-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-0-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-0-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-0-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-0-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-0-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-0-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-0-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-0-membership-heatmap'>
<ul>
<li><a href='#tab-node-0-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-0-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-0-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-0-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-0-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-0-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-0-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-1-1.png" alt="plot of chunk tab-node-0-membership-heatmap-1"/></p>

</div>
<div id='tab-node-0-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-2-1.png" alt="plot of chunk tab-node-0-membership-heatmap-2"/></p>

</div>
<div id='tab-node-0-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-3-1.png" alt="plot of chunk tab-node-0-membership-heatmap-3"/></p>

</div>
<div id='tab-node-0-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-4-1.png" alt="plot of chunk tab-node-0-membership-heatmap-4"/></p>

</div>
<div id='tab-node-0-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-5-1.png" alt="plot of chunk tab-node-0-membership-heatmap-5"/></p>

</div>
<div id='tab-node-0-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-6-1.png" alt="plot of chunk tab-node-0-membership-heatmap-6"/></p>

</div>
<div id='tab-node-0-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0-membership-heatmap-7-1.png" alt="plot of chunk tab-node-0-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-0-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-0-get-signatures'>
<ul>
<li><a href='#tab-node-0-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-0-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-0-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-0-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-0-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-0-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-0-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-1-1.png" alt="plot of chunk tab-node-0-get-signatures-1"/></p>

</div>
<div id='tab-node-0-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-2-1.png" alt="plot of chunk tab-node-0-get-signatures-2"/></p>

</div>
<div id='tab-node-0-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-3-1.png" alt="plot of chunk tab-node-0-get-signatures-3"/></p>

</div>
<div id='tab-node-0-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-4-1.png" alt="plot of chunk tab-node-0-get-signatures-4"/></p>

</div>
<div id='tab-node-0-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-5-1.png" alt="plot of chunk tab-node-0-get-signatures-5"/></p>

</div>
<div id='tab-node-0-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-6-1.png" alt="plot of chunk tab-node-0-get-signatures-6"/></p>

</div>
<div id='tab-node-0-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0-get-signatures-7-1.png" alt="plot of chunk tab-node-0-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-0-signature_compare](figure_cola/node-0-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-0-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-0-dimension-reduction'>
<ul>
<li><a href='#tab-node-0-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-0-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-0-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-0-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-0-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-0-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-0-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-0-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-1-1.png" alt="plot of chunk tab-node-0-dimension-reduction-1"/></p>

</div>
<div id='tab-node-0-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-2-1.png" alt="plot of chunk tab-node-0-dimension-reduction-2"/></p>

</div>
<div id='tab-node-0-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-3-1.png" alt="plot of chunk tab-node-0-dimension-reduction-3"/></p>

</div>
<div id='tab-node-0-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-4-1.png" alt="plot of chunk tab-node-0-dimension-reduction-4"/></p>

</div>
<div id='tab-node-0-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-5-1.png" alt="plot of chunk tab-node-0-dimension-reduction-5"/></p>

</div>
<div id='tab-node-0-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-6-1.png" alt="plot of chunk tab-node-0-dimension-reduction-6"/></p>

</div>
<div id='tab-node-0-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0-dimension-reduction-7-1.png" alt="plot of chunk tab-node-0-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-0-collect-classes](figure_cola/node-0-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node01


Parent node: [Node0](#Node0).
Child nodes: 
                [Node011](#Node011)
        ,
                Node012-leaf
        ,
                Node013-leaf
        ,
                Node021-leaf
        ,
                Node022-leaf
        ,
                Node023-leaf
        ,
                [Node031](#Node031)
        ,
                [Node032](#Node032)
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["01"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 32 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'kmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 3.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-01-collect-plots](figure_cola/node-01-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-01-select-partition-number](figure_cola/node-01-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           0.993       0.997         0.4826 0.516   0.516
#> 3 3 1.000           0.999       0.999         0.2419 0.829   0.685
#> 4 4 0.783           0.915       0.914         0.2147 0.839   0.598
#> 5 5 0.692           0.834       0.863         0.0557 1.000   1.000
#> 6 6 0.828           0.730       0.870         0.0571 0.984   0.933
#> 7 7 0.802           0.584       0.799         0.0182 0.954   0.795
#> 8 8 0.800           0.578       0.831         0.0181 0.982   0.902
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 3
#> attr(,"optional")
#> [1] 2
```

There is also optional best $k$ = 2 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-01-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-01-get-classes'>
<ul>
<li><a href='#tab-node-01-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-01-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-01-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-01-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-01-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-01-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-01-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-01-get-classes-1'>
<p><a id='tab-node-01-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette  p1  p2
#&gt; TCGA.AG.3591.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AH.6549.01     2   0.469      0.889 0.1 0.9
#&gt; TCGA.EI.6514.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.DY.A1DE.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.EI.6510.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.EI.6513.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.AG.A026.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.F5.6810.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.EF.5830.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.DC.5337.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.CL.5918.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AG.3725.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AF.3911.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.EI.6508.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.DC.6158.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.DC.5869.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AG.4022.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.DY.A1DG.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.DC.6683.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AH.6897.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.EI.6882.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AF.6672.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.DY.A1DF.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.G5.6641.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.AG.3742.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AG.4021.01     2   0.000      0.991 0.0 1.0
#&gt; TCGA.AG.A01W.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.F5.6811.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.DC.6154.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.DY.A1DD.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AG.A02N.01     1   0.000      1.000 1.0 0.0
#&gt; TCGA.AG.A020.01     1   0.000      1.000 1.0 0.0
</code></pre>

<script>
$('#tab-node-01-get-classes-1-a').parent().next().next().hide();
$('#tab-node-01-get-classes-1-a').click(function(){
  $('#tab-node-01-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-2'>
<p><a id='tab-node-01-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1   p2   p3
#&gt; TCGA.AG.3591.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AH.6549.01     2  0.0000      0.997  0 1.00 0.00
#&gt; TCGA.EI.6514.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.DY.A1DE.01     3  0.0000      1.000  0 0.00 1.00
#&gt; TCGA.EI.6510.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.EI.6513.01     3  0.0000      1.000  0 0.00 1.00
#&gt; TCGA.AG.A026.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.F5.6810.01     3  0.0000      1.000  0 0.00 1.00
#&gt; TCGA.EF.5830.01     3  0.0000      1.000  0 0.00 1.00
#&gt; TCGA.DC.5337.01     2  0.0000      0.997  0 1.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AG.3725.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AF.3911.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.EI.6508.01     2  0.0000      0.997  0 1.00 0.00
#&gt; TCGA.DC.6158.01     2  0.0000      0.997  0 1.00 0.00
#&gt; TCGA.DC.5869.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AG.4022.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.DY.A1DG.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.DC.6683.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AH.6897.01     2  0.0000      0.997  0 1.00 0.00
#&gt; TCGA.EI.6882.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AF.6672.01     2  0.0892      0.980  0 0.98 0.02
#&gt; TCGA.DY.A1DF.01     3  0.0000      1.000  0 0.00 1.00
#&gt; TCGA.G5.6641.01     2  0.0000      0.997  0 1.00 0.00
#&gt; TCGA.AG.3742.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AG.4021.01     2  0.0000      0.997  0 1.00 0.00
#&gt; TCGA.AG.A01W.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.F5.6811.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.DC.6154.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.DY.A1DD.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AG.A02N.01     1  0.0000      1.000  1 0.00 0.00
#&gt; TCGA.AG.A020.01     2  0.0000      0.997  0 1.00 0.00
</code></pre>

<script>
$('#tab-node-01-get-classes-2-a').parent().next().next().hide();
$('#tab-node-01-get-classes-2-a').click(function(){
  $('#tab-node-01-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-3'>
<p><a id='tab-node-01-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2 p3   p4
#&gt; TCGA.AG.3591.01     4   0.317      0.809 0.16 0.00  0 0.84
#&gt; TCGA.AH.6549.01     2   0.000      0.948 0.00 1.00  0 0.00
#&gt; TCGA.EI.6514.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.DY.A1DE.01     3   0.000      1.000 0.00 0.00  1 0.00
#&gt; TCGA.EI.6510.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.EI.6513.01     3   0.000      1.000 0.00 0.00  1 0.00
#&gt; TCGA.AG.A026.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.F5.6810.01     3   0.000      1.000 0.00 0.00  1 0.00
#&gt; TCGA.EF.5830.01     3   0.000      1.000 0.00 0.00  1 0.00
#&gt; TCGA.DC.5337.01     2   0.000      0.948 0.00 1.00  0 0.00
#&gt; TCGA.CL.5918.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.AG.3725.01     4   0.498      0.647 0.46 0.00  0 0.54
#&gt; TCGA.AF.3911.01     4   0.317      0.809 0.16 0.00  0 0.84
#&gt; TCGA.EI.6508.01     2   0.000      0.948 0.00 1.00  0 0.00
#&gt; TCGA.DC.6158.01     2   0.164      0.922 0.00 0.94  0 0.06
#&gt; TCGA.DC.5869.01     4   0.491      0.716 0.42 0.00  0 0.58
#&gt; TCGA.AG.4022.01     4   0.491      0.716 0.42 0.00  0 0.58
#&gt; TCGA.DY.A1DG.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.DC.6683.01     4   0.317      0.809 0.16 0.00  0 0.84
#&gt; TCGA.AH.6897.01     2   0.000      0.948 0.00 1.00  0 0.00
#&gt; TCGA.EI.6882.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.AF.6672.01     2   0.317      0.859 0.00 0.84  0 0.16
#&gt; TCGA.DY.A1DF.01     3   0.000      1.000 0.00 0.00  1 0.00
#&gt; TCGA.G5.6641.01     2   0.000      0.948 0.00 1.00  0 0.00
#&gt; TCGA.AG.3742.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.AG.4021.01     2   0.000      0.948 0.00 1.00  0 0.00
#&gt; TCGA.AG.A01W.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.F5.6811.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.DC.6154.01     4   0.317      0.809 0.16 0.00  0 0.84
#&gt; TCGA.DY.A1DD.01     1   0.000      1.000 1.00 0.00  0 0.00
#&gt; TCGA.AG.A02N.01     4   0.471      0.760 0.36 0.00  0 0.64
#&gt; TCGA.AG.A020.01     2   0.398      0.737 0.00 0.76  0 0.24
</code></pre>

<script>
$('#tab-node-01-get-classes-3-a').parent().next().next().hide();
$('#tab-node-01-get-classes-3-a').click(function(){
  $('#tab-node-01-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-4'>
<p><a id='tab-node-01-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.AG.3591.01     4  0.5263      0.750 0.10 0.00 0.24 0.66 0.00
#&gt; TCGA.AH.6549.01     2  0.0000      0.858 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     1  0.0000      0.930 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DY.A1DE.01     5  0.0000      0.993 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.EI.6510.01     1  0.0609      0.922 0.98 0.00 0.00 0.02 0.00
#&gt; TCGA.EI.6513.01     5  0.0000      0.993 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.AG.A026.01     1  0.1043      0.910 0.96 0.00 0.04 0.00 0.00
#&gt; TCGA.F5.6810.01     5  0.0000      0.993 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.EF.5830.01     5  0.0609      0.990 0.00 0.00 0.00 0.02 0.98
#&gt; TCGA.DC.5337.01     2  0.0000      0.858 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0000      0.930 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3725.01     4  0.5659      0.659 0.32 0.00 0.10 0.58 0.00
#&gt; TCGA.AF.3911.01     4  0.4216      0.760 0.10 0.00 0.12 0.78 0.00
#&gt; TCGA.EI.6508.01     2  0.2616      0.825 0.00 0.88 0.10 0.02 0.00
#&gt; TCGA.DC.6158.01     2  0.3109      0.798 0.00 0.80 0.20 0.00 0.00
#&gt; TCGA.DC.5869.01     4  0.3796      0.720 0.30 0.00 0.00 0.70 0.00
#&gt; TCGA.AG.4022.01     4  0.3796      0.720 0.30 0.00 0.00 0.70 0.00
#&gt; TCGA.DY.A1DG.01     1  0.4398      0.632 0.72 0.00 0.24 0.04 0.00
#&gt; TCGA.DC.6683.01     4  0.4216      0.760 0.10 0.00 0.12 0.78 0.00
#&gt; TCGA.AH.6897.01     2  0.4433      0.765 0.00 0.74 0.20 0.06 0.00
#&gt; TCGA.EI.6882.01     1  0.0000      0.930 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.6672.01     2  0.4767      0.623 0.00 0.56 0.42 0.00 0.02
#&gt; TCGA.DY.A1DF.01     5  0.0609      0.990 0.00 0.00 0.00 0.02 0.98
#&gt; TCGA.G5.6641.01     2  0.0609      0.856 0.00 0.98 0.02 0.00 0.00
#&gt; TCGA.AG.3742.01     1  0.0000      0.930 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.4021.01     2  0.0000      0.858 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     1  0.1732      0.879 0.92 0.00 0.00 0.08 0.00
#&gt; TCGA.F5.6811.01     1  0.1732      0.879 0.92 0.00 0.00 0.08 0.00
#&gt; TCGA.DC.6154.01     4  0.5130      0.731 0.10 0.00 0.22 0.68 0.00
#&gt; TCGA.DY.A1DD.01     1  0.1043      0.910 0.96 0.00 0.04 0.00 0.00
#&gt; TCGA.AG.A02N.01     4  0.5013      0.745 0.24 0.00 0.08 0.68 0.00
#&gt; TCGA.AG.A020.01     2  0.5130      0.602 0.00 0.68 0.10 0.22 0.00
</code></pre>

<script>
$('#tab-node-01-get-classes-4-a').parent().next().next().hide();
$('#tab-node-01-get-classes-4-a').click(function(){
  $('#tab-node-01-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-5'>
<p><a id='tab-node-01-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.AG.3591.01     4  0.3864     0.5858 0.00 0.48 0.00 0.52 0.00 0.00
#&gt; TCGA.AH.6549.01     3  0.0000     0.7781 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     1  0.0000     0.9161 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DY.A1DE.01     5  0.0000     0.9910 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.EI.6510.01     1  0.0547     0.9078 0.98 0.00 0.00 0.02 0.00 0.00
#&gt; TCGA.EI.6513.01     5  0.0000     0.9910 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.A026.01     1  0.0000     0.9161 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6810.01     5  0.0000     0.9910 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.EF.5830.01     5  0.0547     0.9865 0.00 0.02 0.00 0.00 0.98 0.00
#&gt; TCGA.DC.5337.01     3  0.0000     0.7781 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0000     0.9161 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3725.01     4  0.4727     0.6168 0.10 0.24 0.00 0.66 0.00 0.00
#&gt; TCGA.AF.3911.01     4  0.2941     0.6603 0.00 0.22 0.00 0.78 0.00 0.00
#&gt; TCGA.EI.6508.01     3  0.3073     0.7216 0.00 0.08 0.84 0.00 0.00 0.08
#&gt; TCGA.DC.6158.01     3  0.3756     0.0257 0.00 0.00 0.60 0.00 0.00 0.40
#&gt; TCGA.DC.5869.01     4  0.0547     0.7294 0.02 0.00 0.00 0.98 0.00 0.00
#&gt; TCGA.AG.4022.01     4  0.0547     0.7294 0.02 0.00 0.00 0.98 0.00 0.00
#&gt; TCGA.DY.A1DG.01     1  0.6904     0.1811 0.46 0.28 0.00 0.16 0.00 0.10
#&gt; TCGA.DC.6683.01     4  0.2941     0.6603 0.00 0.22 0.00 0.78 0.00 0.00
#&gt; TCGA.AH.6897.01     3  0.3746     0.6471 0.00 0.14 0.78 0.00 0.00 0.08
#&gt; TCGA.EI.6882.01     1  0.0000     0.9161 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.6672.01     6  0.3156     0.0000 0.00 0.00 0.18 0.00 0.02 0.80
#&gt; TCGA.DY.A1DF.01     5  0.0547     0.9865 0.00 0.02 0.00 0.00 0.98 0.00
#&gt; TCGA.G5.6641.01     3  0.0000     0.7781 0.00 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AG.3742.01     1  0.0000     0.9161 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.4021.01     3  0.0937     0.7685 0.00 0.04 0.96 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     1  0.1556     0.8720 0.92 0.00 0.00 0.08 0.00 0.00
#&gt; TCGA.F5.6811.01     1  0.1556     0.8720 0.92 0.00 0.00 0.08 0.00 0.00
#&gt; TCGA.DC.6154.01     4  0.4631     0.6059 0.00 0.32 0.00 0.62 0.00 0.06
#&gt; TCGA.DY.A1DD.01     1  0.0000     0.9161 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     4  0.4105     0.6717 0.02 0.24 0.00 0.72 0.00 0.02
#&gt; TCGA.AG.A020.01     3  0.4534     0.3360 0.00 0.38 0.58 0.04 0.00 0.00
</code></pre>

<script>
$('#tab-node-01-get-classes-5-a').parent().next().next().hide();
$('#tab-node-01-get-classes-5-a').click(function(){
  $('#tab-node-01-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-6'>
<p><a id='tab-node-01-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.AG.3591.01     2  0.5606     0.0000 0.00 0.38 0.00 0.34 0.00 0.00 0.28
#&gt; TCGA.AH.6549.01     3  0.0000     0.7554 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     1  0.0000     0.9559 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DY.A1DE.01     5  0.0000     0.9635 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6510.01     1  0.0863     0.9341 0.96 0.00 0.00 0.04 0.00 0.00 0.00
#&gt; TCGA.EI.6513.01     5  0.0000     0.9635 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A026.01     1  0.0000     0.9559 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6810.01     5  0.0000     0.9635 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.EF.5830.01     5  0.1664     0.9445 0.00 0.06 0.00 0.00 0.92 0.00 0.02
#&gt; TCGA.DC.5337.01     3  0.0000     0.7554 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0000     0.9559 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3725.01     4  0.4681    -0.1314 0.10 0.32 0.00 0.58 0.00 0.00 0.00
#&gt; TCGA.AF.3911.01     4  0.4671     0.3532 0.00 0.14 0.00 0.68 0.00 0.02 0.16
#&gt; TCGA.EI.6508.01     3  0.1860     0.7352 0.00 0.02 0.92 0.00 0.00 0.02 0.04
#&gt; TCGA.DC.6158.01     3  0.3525     0.0791 0.00 0.00 0.56 0.00 0.00 0.44 0.00
#&gt; TCGA.DC.5869.01     4  0.1671     0.4479 0.10 0.00 0.00 0.90 0.00 0.00 0.00
#&gt; TCGA.AG.4022.01     4  0.1671     0.4479 0.10 0.00 0.00 0.90 0.00 0.00 0.00
#&gt; TCGA.DY.A1DG.01     7  0.5535     0.1505 0.30 0.04 0.00 0.12 0.00 0.00 0.54
#&gt; TCGA.DC.6683.01     4  0.3927     0.3896 0.00 0.08 0.00 0.76 0.00 0.02 0.14
#&gt; TCGA.AH.6897.01     3  0.4778     0.3800 0.00 0.34 0.58 0.00 0.00 0.02 0.06
#&gt; TCGA.EI.6882.01     1  0.0000     0.9559 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.6672.01     6  0.1433     0.0000 0.00 0.00 0.08 0.00 0.00 0.92 0.00
#&gt; TCGA.DY.A1DF.01     5  0.1664     0.9445 0.00 0.06 0.00 0.00 0.92 0.00 0.02
#&gt; TCGA.G5.6641.01     3  0.0000     0.7554 0.00 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3742.01     1  0.0000     0.9559 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.4021.01     3  0.1006     0.7464 0.00 0.02 0.96 0.00 0.00 0.00 0.02
#&gt; TCGA.AG.A01W.01     1  0.1886     0.8656 0.88 0.00 0.00 0.12 0.00 0.00 0.00
#&gt; TCGA.F5.6811.01     1  0.1886     0.8656 0.88 0.00 0.00 0.12 0.00 0.00 0.00
#&gt; TCGA.DC.6154.01     7  0.3525    -0.2136 0.00 0.00 0.00 0.44 0.00 0.00 0.56
#&gt; TCGA.DY.A1DD.01     1  0.0000     0.9559 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     4  0.4577    -0.3637 0.00 0.36 0.00 0.58 0.00 0.02 0.04
#&gt; TCGA.AG.A020.01     3  0.6415     0.2114 0.00 0.12 0.48 0.08 0.00 0.02 0.30
</code></pre>

<script>
$('#tab-node-01-get-classes-6-a').parent().next().next().hide();
$('#tab-node-01-get-classes-6-a').click(function(){
  $('#tab-node-01-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-01-get-classes-7'>
<p><a id='tab-node-01-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4  p5   p6   p7   p8
#&gt; TCGA.AG.3591.01     7  0.6481      0.120 0.00 0.06 0.00 0.30 0.0 0.08 0.44 0.12
#&gt; TCGA.AH.6549.01     3  0.0000      0.620 0.00 0.00 1.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     1  0.0000      0.922 1.00 0.00 0.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.DY.A1DE.01     5  0.0000      0.905 0.00 0.00 0.00 0.00 1.0 0.00 0.00 0.00
#&gt; TCGA.EI.6510.01     1  0.1563      0.869 0.90 0.00 0.00 0.10 0.0 0.00 0.00 0.00
#&gt; TCGA.EI.6513.01     5  0.0000      0.905 0.00 0.00 0.00 0.00 1.0 0.00 0.00 0.00
#&gt; TCGA.AG.A026.01     1  0.0000      0.922 1.00 0.00 0.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.F5.6810.01     5  0.0000      0.905 0.00 0.00 0.00 0.00 1.0 0.00 0.00 0.00
#&gt; TCGA.EF.5830.01     5  0.3314      0.853 0.00 0.00 0.00 0.00 0.8 0.08 0.10 0.02
#&gt; TCGA.DC.5337.01     3  0.0000      0.620 0.00 0.00 1.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0000      0.922 1.00 0.00 0.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.AG.3725.01     4  0.4960      0.470 0.06 0.02 0.00 0.70 0.0 0.02 0.12 0.08
#&gt; TCGA.AF.3911.01     4  0.5539      0.201 0.00 0.00 0.00 0.50 0.0 0.30 0.06 0.14
#&gt; TCGA.EI.6508.01     3  0.3675      0.194 0.00 0.00 0.66 0.00 0.0 0.30 0.00 0.04
#&gt; TCGA.DC.6158.01     3  0.3737     -0.148 0.00 0.48 0.50 0.00 0.0 0.00 0.02 0.00
#&gt; TCGA.DC.5869.01     4  0.0808      0.615 0.04 0.00 0.00 0.96 0.0 0.00 0.00 0.00
#&gt; TCGA.AG.4022.01     4  0.0808      0.615 0.04 0.00 0.00 0.96 0.0 0.00 0.00 0.00
#&gt; TCGA.DY.A1DG.01     7  0.3735      0.264 0.22 0.00 0.00 0.04 0.0 0.00 0.72 0.02
#&gt; TCGA.DC.6683.01     4  0.2623      0.503 0.00 0.00 0.00 0.84 0.0 0.10 0.06 0.00
#&gt; TCGA.AH.6897.01     8  0.3193      0.000 0.00 0.00 0.38 0.00 0.0 0.00 0.00 0.62
#&gt; TCGA.EI.6882.01     1  0.0000      0.922 1.00 0.00 0.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.AF.6672.01     2  0.1091      0.000 0.00 0.94 0.06 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.DY.A1DF.01     5  0.3314      0.853 0.00 0.00 0.00 0.00 0.8 0.08 0.10 0.02
#&gt; TCGA.G5.6641.01     3  0.0000      0.620 0.00 0.00 1.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.AG.3742.01     1  0.0000      0.922 1.00 0.00 0.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.AG.4021.01     3  0.0808      0.608 0.00 0.00 0.96 0.00 0.0 0.04 0.00 0.00
#&gt; TCGA.AG.A01W.01     1  0.2267      0.802 0.82 0.00 0.00 0.18 0.0 0.00 0.00 0.00
#&gt; TCGA.F5.6811.01     1  0.2756      0.702 0.74 0.00 0.00 0.26 0.0 0.00 0.00 0.00
#&gt; TCGA.DC.6154.01     7  0.3943      0.277 0.00 0.00 0.00 0.40 0.0 0.04 0.56 0.00
#&gt; TCGA.DY.A1DD.01     1  0.0000      0.922 1.00 0.00 0.00 0.00 0.0 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     4  0.5833      0.393 0.02 0.06 0.00 0.60 0.0 0.06 0.06 0.20
#&gt; TCGA.AG.A020.01     3  0.4777      0.183 0.00 0.00 0.50 0.08 0.0 0.40 0.02 0.00
</code></pre>

<script>
$('#tab-node-01-get-classes-7-a').parent().next().next().hide();
$('#tab-node-01-get-classes-7-a').click(function(){
  $('#tab-node-01-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-01-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-01-consensus-heatmap'>
<ul>
<li><a href='#tab-node-01-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-01-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-01-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-01-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-01-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-01-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-01-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-01-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-01-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-01-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-01-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-01-membership-heatmap'>
<ul>
<li><a href='#tab-node-01-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-01-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-01-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-01-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-01-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-01-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-01-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-1-1.png" alt="plot of chunk tab-node-01-membership-heatmap-1"/></p>

</div>
<div id='tab-node-01-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-2-1.png" alt="plot of chunk tab-node-01-membership-heatmap-2"/></p>

</div>
<div id='tab-node-01-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-3-1.png" alt="plot of chunk tab-node-01-membership-heatmap-3"/></p>

</div>
<div id='tab-node-01-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-4-1.png" alt="plot of chunk tab-node-01-membership-heatmap-4"/></p>

</div>
<div id='tab-node-01-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-5-1.png" alt="plot of chunk tab-node-01-membership-heatmap-5"/></p>

</div>
<div id='tab-node-01-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-6-1.png" alt="plot of chunk tab-node-01-membership-heatmap-6"/></p>

</div>
<div id='tab-node-01-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-01-membership-heatmap-7-1.png" alt="plot of chunk tab-node-01-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-01-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-01-get-signatures'>
<ul>
<li><a href='#tab-node-01-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-01-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-01-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-01-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-01-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-01-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-01-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-1-1.png" alt="plot of chunk tab-node-01-get-signatures-1"/></p>

</div>
<div id='tab-node-01-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-2-1.png" alt="plot of chunk tab-node-01-get-signatures-2"/></p>

</div>
<div id='tab-node-01-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-3-1.png" alt="plot of chunk tab-node-01-get-signatures-3"/></p>

</div>
<div id='tab-node-01-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-4-1.png" alt="plot of chunk tab-node-01-get-signatures-4"/></p>

</div>
<div id='tab-node-01-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-5-1.png" alt="plot of chunk tab-node-01-get-signatures-5"/></p>

</div>
<div id='tab-node-01-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-6-1.png" alt="plot of chunk tab-node-01-get-signatures-6"/></p>

</div>
<div id='tab-node-01-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-01-get-signatures-7-1.png" alt="plot of chunk tab-node-01-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-01-signature_compare](figure_cola/node-01-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-01-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-01-dimension-reduction'>
<ul>
<li><a href='#tab-node-01-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-01-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-01-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-01-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-01-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-01-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-01-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-01-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-1-1.png" alt="plot of chunk tab-node-01-dimension-reduction-1"/></p>

</div>
<div id='tab-node-01-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-2-1.png" alt="plot of chunk tab-node-01-dimension-reduction-2"/></p>

</div>
<div id='tab-node-01-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-3-1.png" alt="plot of chunk tab-node-01-dimension-reduction-3"/></p>

</div>
<div id='tab-node-01-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-4-1.png" alt="plot of chunk tab-node-01-dimension-reduction-4"/></p>

</div>
<div id='tab-node-01-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-5-1.png" alt="plot of chunk tab-node-01-dimension-reduction-5"/></p>

</div>
<div id='tab-node-01-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-6-1.png" alt="plot of chunk tab-node-01-dimension-reduction-6"/></p>

</div>
<div id='tab-node-01-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-01-dimension-reduction-7-1.png" alt="plot of chunk tab-node-01-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-01-collect-classes](figure_cola/node-01-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node011


Parent node: [Node01](#Node01).
Child nodes: 
                Node0111-leaf
        ,
                Node0112-leaf
        ,
                Node0113-leaf
        ,
                Node0311-leaf
        ,
                Node0312-leaf
        ,
                Node0321-leaf
        ,
                [Node0322](#Node0322)
        ,
                Node0323-leaf
        ,
                Node0324-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["011"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 18 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 3.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-011-collect-plots](figure_cola/node-011-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-011-select-partition-number](figure_cola/node-011-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.4254 0.575   0.575
#> 3 3 1.000           0.986       0.996         0.2334 0.869   0.778
#> 4 4 0.987           0.922       0.989         0.0449 0.987   0.972
#> 5 5 0.856           0.690       0.944         0.1068 0.993   0.986
#> 6 6 0.693           0.623       0.889         0.1718 0.824   0.609
#> 7 7 0.634           0.584       0.888         0.0371 0.987   0.952
#> 8 8 0.712           0.478       0.900         0.0494 0.987   0.950
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 3
#> attr(,"optional")
#> [1] 2
```

There is also optional best $k$ = 2 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-011-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-011-get-classes'>
<ul>
<li><a href='#tab-node-011-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-011-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-011-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-011-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-011-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-011-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-011-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-011-get-classes-1'>
<p><a id='tab-node-011-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.AG.3591.01     2       0          1  0  1
#&gt; TCGA.EI.6514.01     1       0          1  1  0
#&gt; TCGA.EI.6510.01     2       0          1  0  1
#&gt; TCGA.AG.A026.01     1       0          1  1  0
#&gt; TCGA.CL.5918.01     1       0          1  1  0
#&gt; TCGA.AG.3725.01     2       0          1  0  1
#&gt; TCGA.AF.3911.01     1       0          1  1  0
#&gt; TCGA.DC.5869.01     1       0          1  1  0
#&gt; TCGA.AG.4022.01     1       0          1  1  0
#&gt; TCGA.DY.A1DG.01     1       0          1  1  0
#&gt; TCGA.DC.6683.01     1       0          1  1  0
#&gt; TCGA.EI.6882.01     2       0          1  0  1
#&gt; TCGA.AG.3742.01     1       0          1  1  0
#&gt; TCGA.AG.A01W.01     1       0          1  1  0
#&gt; TCGA.F5.6811.01     1       0          1  1  0
#&gt; TCGA.DC.6154.01     1       0          1  1  0
#&gt; TCGA.DY.A1DD.01     1       0          1  1  0
#&gt; TCGA.AG.A02N.01     2       0          1  0  1
</code></pre>

<script>
$('#tab-node-011-get-classes-1-a').parent().next().next().hide();
$('#tab-node-011-get-classes-1-a').click(function(){
  $('#tab-node-011-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-011-get-classes-2'>
<p><a id='tab-node-011-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2   p3
#&gt; TCGA.AG.3591.01     2   0.000      1.000 0.00  1 0.00
#&gt; TCGA.EI.6514.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.EI.6510.01     3   0.000      0.936 0.00  0 1.00
#&gt; TCGA.AG.A026.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.CL.5918.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.AG.3725.01     3   0.000      0.936 0.00  0 1.00
#&gt; TCGA.AF.3911.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.DC.5869.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.AG.4022.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.DY.A1DG.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.DC.6683.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.EI.6882.01     2   0.000      1.000 0.00  1 0.00
#&gt; TCGA.AG.3742.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.AG.A01W.01     3   0.254      0.871 0.08  0 0.92
#&gt; TCGA.F5.6811.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.DC.6154.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.DY.A1DD.01     1   0.000      1.000 1.00  0 0.00
#&gt; TCGA.AG.A02N.01     2   0.000      1.000 0.00  1 0.00
</code></pre>

<script>
$('#tab-node-011-get-classes-2-a').parent().next().next().hide();
$('#tab-node-011-get-classes-2-a').click(function(){
  $('#tab-node-011-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-011-get-classes-3'>
<p><a id='tab-node-011-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2   p3  p4
#&gt; TCGA.AG.3591.01     2  0.0000      1.000 0.00  1 0.00 0.0
#&gt; TCGA.EI.6514.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.EI.6510.01     3  0.2345      0.882 0.00  0 0.90 0.1
#&gt; TCGA.AG.A026.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.CL.5918.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.AG.3725.01     4  0.0000      0.000 0.00  0 0.00 1.0
#&gt; TCGA.AF.3911.01     1  0.0707      0.980 0.98  0 0.02 0.0
#&gt; TCGA.DC.5869.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.AG.4022.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.DY.A1DG.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.DC.6683.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.EI.6882.01     2  0.0000      1.000 0.00  1 0.00 0.0
#&gt; TCGA.AG.3742.01     1  0.1211      0.966 0.96  0 0.04 0.0
#&gt; TCGA.AG.A01W.01     3  0.0000      0.887 0.00  0 1.00 0.0
#&gt; TCGA.F5.6811.01     1  0.1211      0.966 0.96  0 0.04 0.0
#&gt; TCGA.DC.6154.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.DY.A1DD.01     1  0.0000      0.991 1.00  0 0.00 0.0
#&gt; TCGA.AG.A02N.01     2  0.0000      1.000 0.00  1 0.00 0.0
</code></pre>

<script>
$('#tab-node-011-get-classes-3-a').parent().next().next().hide();
$('#tab-node-011-get-classes-3-a').click(function(){
  $('#tab-node-011-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-011-get-classes-4'>
<p><a id='tab-node-011-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2 p3 p4   p5
#&gt; TCGA.AG.3591.01     2  0.0000      1.000 0.00  1  0  0 0.00
#&gt; TCGA.EI.6514.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.EI.6510.01     3  0.0000      0.000 0.00  0  1  0 0.00
#&gt; TCGA.AG.A026.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.CL.5918.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.AG.3725.01     4  0.0000      0.000 0.00  0  0  1 0.00
#&gt; TCGA.AF.3911.01     1  0.1043      0.878 0.96  0  0  0 0.04
#&gt; TCGA.DC.5869.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.AG.4022.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.DY.A1DG.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.DC.6683.01     1  0.0609      0.892 0.98  0  0  0 0.02
#&gt; TCGA.EI.6882.01     2  0.0000      1.000 0.00  1  0  0 0.00
#&gt; TCGA.AG.3742.01     1  0.4302      0.186 0.52  0  0  0 0.48
#&gt; TCGA.AG.A01W.01     5  0.0000      0.000 0.00  0  0  0 1.00
#&gt; TCGA.F5.6811.01     1  0.4287      0.240 0.54  0  0  0 0.46
#&gt; TCGA.DC.6154.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.DY.A1DD.01     1  0.0000      0.902 1.00  0  0  0 0.00
#&gt; TCGA.AG.A02N.01     2  0.0000      1.000 0.00  1  0  0 0.00
</code></pre>

<script>
$('#tab-node-011-get-classes-4-a').parent().next().next().hide();
$('#tab-node-011-get-classes-4-a').click(function(){
  $('#tab-node-011-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-011-get-classes-5'>
<p><a id='tab-node-011-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2 p3 p4   p5   p6
#&gt; TCGA.AG.3591.01     2  0.0000     0.9736 0.00 1.00  0  0 0.00 0.00
#&gt; TCGA.EI.6514.01     1  0.0000     0.8706 1.00 0.00  0  0 0.00 0.00
#&gt; TCGA.EI.6510.01     3  0.0000     0.0000 0.00 0.00  1  0 0.00 0.00
#&gt; TCGA.AG.A026.01     1  0.0000     0.8706 1.00 0.00  0  0 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0547     0.8548 0.98 0.00  0  0 0.00 0.02
#&gt; TCGA.AG.3725.01     4  0.0000     0.0000 0.00 0.00  0  1 0.00 0.00
#&gt; TCGA.AF.3911.01     6  0.5039     0.4038 0.18 0.00  0  0 0.18 0.64
#&gt; TCGA.DC.5869.01     1  0.2048     0.8061 0.88 0.00  0  0 0.00 0.12
#&gt; TCGA.AG.4022.01     1  0.0000     0.8706 1.00 0.00  0  0 0.00 0.00
#&gt; TCGA.DY.A1DG.01     1  0.1556     0.8426 0.92 0.00  0  0 0.00 0.08
#&gt; TCGA.DC.6683.01     1  0.3828    -0.0666 0.56 0.00  0  0 0.00 0.44
#&gt; TCGA.EI.6882.01     2  0.1480     0.9465 0.00 0.94  0  0 0.02 0.04
#&gt; TCGA.AG.3742.01     6  0.4631     0.5454 0.32 0.00  0  0 0.06 0.62
#&gt; TCGA.AG.A01W.01     5  0.2793     0.0000 0.00 0.00  0  0 0.80 0.20
#&gt; TCGA.F5.6811.01     6  0.3592     0.6159 0.24 0.00  0  0 0.02 0.74
#&gt; TCGA.DC.6154.01     1  0.1556     0.8426 0.92 0.00  0  0 0.00 0.08
#&gt; TCGA.DY.A1DD.01     1  0.0000     0.8706 1.00 0.00  0  0 0.00 0.00
#&gt; TCGA.AG.A02N.01     2  0.0000     0.9736 0.00 1.00  0  0 0.00 0.00
</code></pre>

<script>
$('#tab-node-011-get-classes-5-a').parent().next().next().hide();
$('#tab-node-011-get-classes-5-a').click(function(){
  $('#tab-node-011-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-011-get-classes-6'>
<p><a id='tab-node-011-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2 p3 p4   p5   p6   p7
#&gt; TCGA.AG.3591.01     2  0.2569      0.748 0.00 0.84  0  0 0.00 0.02 0.14
#&gt; TCGA.EI.6514.01     1  0.0000      0.880 1.00 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.EI.6510.01     3  0.0000      0.000 0.00 0.00  1  0 0.00 0.00 0.00
#&gt; TCGA.AG.A026.01     1  0.0000      0.880 1.00 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0504      0.867 0.98 0.00  0  0 0.00 0.02 0.00
#&gt; TCGA.AG.3725.01     4  0.0000      0.000 0.00 0.00  0  1 0.00 0.00 0.00
#&gt; TCGA.AF.3911.01     7  0.3835      0.000 0.10 0.00  0  0 0.00 0.16 0.74
#&gt; TCGA.DC.5869.01     1  0.2376      0.823 0.86 0.00  0  0 0.00 0.02 0.12
#&gt; TCGA.AG.4022.01     1  0.0000      0.880 1.00 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.DY.A1DG.01     1  0.1671      0.851 0.90 0.00  0  0 0.00 0.00 0.10
#&gt; TCGA.DC.6683.01     1  0.4594      0.459 0.64 0.00  0  0 0.00 0.14 0.22
#&gt; TCGA.EI.6882.01     2  0.4162      0.690 0.00 0.74  0  0 0.02 0.12 0.12
#&gt; TCGA.AG.3742.01     6  0.2569      0.501 0.14 0.00  0  0 0.02 0.84 0.00
#&gt; TCGA.AG.A01W.01     5  0.0504      0.000 0.00 0.00  0  0 0.98 0.02 0.00
#&gt; TCGA.F5.6811.01     6  0.4698      0.445 0.24 0.00  0  0 0.00 0.62 0.14
#&gt; TCGA.DC.6154.01     1  0.2569      0.812 0.84 0.00  0  0 0.00 0.02 0.14
#&gt; TCGA.DY.A1DD.01     1  0.0000      0.880 1.00 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     2  0.0000      0.798 0.00 1.00  0  0 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-011-get-classes-6-a').parent().next().next().hide();
$('#tab-node-011-get-classes-6-a').click(function(){
  $('#tab-node-011-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-011-get-classes-7'>
<p><a id='tab-node-011-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2 p3 p4   p5   p6   p7   p8
#&gt; TCGA.AG.3591.01     2  0.3083     0.5752 0.00 0.66  0  0 0.34 0.00 0.00 0.00
#&gt; TCGA.EI.6514.01     1  0.0000     0.8821 1.00 0.00  0  0 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6510.01     3  0.0000     0.0000 0.00 0.00  1  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A026.01     1  0.0000     0.8821 1.00 0.00  0  0 0.00 0.00 0.00 0.00
#&gt; TCGA.CL.5918.01     1  0.0471     0.8750 0.98 0.00  0  0 0.00 0.02 0.00 0.00
#&gt; TCGA.AG.3725.01     4  0.0000     0.0000 0.00 0.00  0  1 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.3911.01     7  0.0000     0.0000 0.00 0.00  0  0 0.00 0.00 1.00 0.00
#&gt; TCGA.DC.5869.01     1  0.2350     0.8257 0.86 0.00  0  0 0.00 0.04 0.10 0.00
#&gt; TCGA.AG.4022.01     1  0.0000     0.8821 1.00 0.00  0  0 0.00 0.00 0.00 0.00
#&gt; TCGA.DY.A1DG.01     1  0.2025     0.8449 0.88 0.00  0  0 0.00 0.00 0.10 0.02
#&gt; TCGA.DC.6683.01     1  0.4747     0.3171 0.54 0.00  0  0 0.00 0.16 0.30 0.00
#&gt; TCGA.EI.6882.01     8  0.3193     0.0000 0.00 0.38  0  0 0.00 0.00 0.00 0.62
#&gt; TCGA.AG.3742.01     6  0.0000     0.3025 0.00 0.00  0  0 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A01W.01     5  0.3083     0.0000 0.00 0.00  0  0 0.66 0.00 0.00 0.34
#&gt; TCGA.F5.6811.01     6  0.5062     0.0642 0.12 0.00  0  0 0.00 0.48 0.38 0.02
#&gt; TCGA.DC.6154.01     1  0.2114     0.8166 0.84 0.00  0  0 0.00 0.00 0.16 0.00
#&gt; TCGA.DY.A1DD.01     1  0.0000     0.8821 1.00 0.00  0  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.01     2  0.0000     0.4516 0.00 1.00  0  0 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-011-get-classes-7-a').parent().next().next().hide();
$('#tab-node-011-get-classes-7-a').click(function(){
  $('#tab-node-011-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-011-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-011-consensus-heatmap'>
<ul>
<li><a href='#tab-node-011-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-011-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-011-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-011-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-011-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-011-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-011-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-011-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-011-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-011-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-011-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-011-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-011-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-011-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-011-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-011-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-011-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-011-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-011-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-011-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-011-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-011-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-011-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-011-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-011-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-011-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-011-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-011-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-011-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-011-membership-heatmap'>
<ul>
<li><a href='#tab-node-011-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-011-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-011-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-011-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-011-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-011-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-011-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-011-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-011-membership-heatmap-1-1.png" alt="plot of chunk tab-node-011-membership-heatmap-1"/></p>

</div>
<div id='tab-node-011-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-011-membership-heatmap-2-1.png" alt="plot of chunk tab-node-011-membership-heatmap-2"/></p>

</div>
<div id='tab-node-011-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-011-membership-heatmap-3-1.png" alt="plot of chunk tab-node-011-membership-heatmap-3"/></p>

</div>
<div id='tab-node-011-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-011-membership-heatmap-4-1.png" alt="plot of chunk tab-node-011-membership-heatmap-4"/></p>

</div>
<div id='tab-node-011-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-011-membership-heatmap-5-1.png" alt="plot of chunk tab-node-011-membership-heatmap-5"/></p>

</div>
<div id='tab-node-011-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-011-membership-heatmap-6-1.png" alt="plot of chunk tab-node-011-membership-heatmap-6"/></p>

</div>
<div id='tab-node-011-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-011-membership-heatmap-7-1.png" alt="plot of chunk tab-node-011-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-011-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-011-get-signatures'>
<ul>
<li><a href='#tab-node-011-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-011-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-011-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-011-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-011-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-011-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-011-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-011-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-011-get-signatures-1-1.png" alt="plot of chunk tab-node-011-get-signatures-1"/></p>

</div>
<div id='tab-node-011-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-011-get-signatures-2-1.png" alt="plot of chunk tab-node-011-get-signatures-2"/></p>

</div>
<div id='tab-node-011-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-011-get-signatures-3-1.png" alt="plot of chunk tab-node-011-get-signatures-3"/></p>

</div>
<div id='tab-node-011-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-011-get-signatures-4-1.png" alt="plot of chunk tab-node-011-get-signatures-4"/></p>

</div>
<div id='tab-node-011-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-011-get-signatures-5-1.png" alt="plot of chunk tab-node-011-get-signatures-5"/></p>

</div>
<div id='tab-node-011-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-011-get-signatures-6-1.png" alt="plot of chunk tab-node-011-get-signatures-6"/></p>

</div>
<div id='tab-node-011-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-011-get-signatures-7-1.png" alt="plot of chunk tab-node-011-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-011-signature_compare](figure_cola/node-011-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-011-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-011-dimension-reduction'>
<ul>
<li><a href='#tab-node-011-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-011-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-011-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-011-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-011-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-011-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-011-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-011-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-011-dimension-reduction-1-1.png" alt="plot of chunk tab-node-011-dimension-reduction-1"/></p>

</div>
<div id='tab-node-011-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-011-dimension-reduction-2-1.png" alt="plot of chunk tab-node-011-dimension-reduction-2"/></p>

</div>
<div id='tab-node-011-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-011-dimension-reduction-3-1.png" alt="plot of chunk tab-node-011-dimension-reduction-3"/></p>

</div>
<div id='tab-node-011-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-011-dimension-reduction-4-1.png" alt="plot of chunk tab-node-011-dimension-reduction-4"/></p>

</div>
<div id='tab-node-011-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-011-dimension-reduction-5-1.png" alt="plot of chunk tab-node-011-dimension-reduction-5"/></p>

</div>
<div id='tab-node-011-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-011-dimension-reduction-6-1.png" alt="plot of chunk tab-node-011-dimension-reduction-6"/></p>

</div>
<div id='tab-node-011-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-011-dimension-reduction-7-1.png" alt="plot of chunk tab-node-011-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-011-collect-classes](figure_cola/node-011-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node02


Parent node: [Node0](#Node0).
Child nodes: 
                [Node011](#Node011)
        ,
                Node012-leaf
        ,
                Node013-leaf
        ,
                Node021-leaf
        ,
                Node022-leaf
        ,
                Node023-leaf
        ,
                [Node031](#Node031)
        ,
                [Node032](#Node032)
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["02"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 27 columns.
#>   Top rows (1000) are extracted by 'SD' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 5.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-02-collect-plots](figure_cola/node-02-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-02-select-partition-number](figure_cola/node-02-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.3995 0.601   0.601
#> 3 3 0.920           0.974       0.967         0.5623 0.761   0.602
#> 4 4 0.977           0.962       0.953         0.0823 0.966   0.906
#> 5 5 0.903           0.858       0.943         0.1273 0.906   0.713
#> 6 6 0.893           0.854       0.934         0.0523 0.963   0.843
#> 7 7 0.890           0.821       0.930         0.0401 0.969   0.847
#> 8 8 0.951           0.774       0.935         0.0209 0.997   0.984
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 5
#> attr(,"optional")
#> [1] 2 3
```

There is also optional best $k$ = 2 3 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-02-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-02-get-classes'>
<ul>
<li><a href='#tab-node-02-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-02-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-02-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-02-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-02-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-02-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-02-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-02-get-classes-1'>
<p><a id='tab-node-02-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.F5.6812.01     2       0          1  0  1
#&gt; TCGA.BM.6198.01     2       0          1  0  1
#&gt; TCGA.G5.6572.02     2       0          1  0  1
#&gt; TCGA.EI.6506.01     2       0          1  0  1
#&gt; TCGA.AG.A036.11     1       0          1  1  0
#&gt; TCGA.AF.4110.01     2       0          1  0  1
#&gt; TCGA.AH.6544.01     2       0          1  0  1
#&gt; TCGA.F5.6861.01     2       0          1  0  1
#&gt; TCGA.AF.2690.01     2       0          1  0  1
#&gt; TCGA.EI.6881.01     2       0          1  0  1
#&gt; TCGA.AF.2693.01     2       0          1  0  1
#&gt; TCGA.AG.3731.11     1       0          1  1  0
#&gt; TCGA.DC.4745.01     2       0          1  0  1
#&gt; TCGA.EI.6507.01     2       0          1  0  1
#&gt; TCGA.EI.6917.01     2       0          1  0  1
#&gt; TCGA.DC.6681.01     2       0          1  0  1
#&gt; TCGA.AG.3725.11     1       0          1  1  0
#&gt; TCGA.F5.6813.01     2       0          1  0  1
#&gt; TCGA.G5.6572.01     2       0          1  0  1
#&gt; TCGA.CI.6621.01     2       0          1  0  1
#&gt; TCGA.G5.6235.01     2       0          1  0  1
#&gt; TCGA.AH.6547.01     2       0          1  0  1
#&gt; TCGA.EI.6884.01     2       0          1  0  1
#&gt; TCGA.AG.A020.11     1       0          1  1  0
#&gt; TCGA.AG.A01Y.11     1       0          1  1  0
#&gt; TCGA.AG.A01W.11     1       0          1  1  0
#&gt; TCGA.AG.A02N.11     1       0          1  1  0
</code></pre>

<script>
$('#tab-node-02-get-classes-1-a').parent().next().next().hide();
$('#tab-node-02-get-classes-1-a').click(function(){
  $('#tab-node-02-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-2'>
<p><a id='tab-node-02-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.F5.6812.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.BM.6198.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.G5.6572.02     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.EI.6506.01     3   0.254      0.971 0.00 0.08 0.92
#&gt; TCGA.AG.A036.11     1   0.254      0.931 0.92 0.00 0.08
#&gt; TCGA.AF.4110.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.AH.6544.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.F5.6861.01     3   0.254      0.971 0.00 0.08 0.92
#&gt; TCGA.AF.2690.01     3   0.296      0.950 0.00 0.10 0.90
#&gt; TCGA.EI.6881.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.AF.2693.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.AG.3731.11     1   0.254      0.931 0.92 0.00 0.08
#&gt; TCGA.DC.4745.01     3   0.254      0.971 0.00 0.08 0.92
#&gt; TCGA.EI.6507.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.EI.6917.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.DC.6681.01     3   0.254      0.971 0.00 0.08 0.92
#&gt; TCGA.AG.3725.11     1   0.153      0.948 0.96 0.00 0.04
#&gt; TCGA.F5.6813.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.G5.6572.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.CI.6621.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.G5.6235.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.AH.6547.01     3   0.254      0.873 0.08 0.00 0.92
#&gt; TCGA.EI.6884.01     2   0.000      1.000 0.00 1.00 0.00
#&gt; TCGA.AG.A020.11     1   0.153      0.948 0.96 0.00 0.04
#&gt; TCGA.AG.A01Y.11     1   0.153      0.948 0.96 0.00 0.04
#&gt; TCGA.AG.A01W.11     1   0.153      0.948 0.96 0.00 0.04
#&gt; TCGA.AG.A02N.11     1   0.254      0.931 0.92 0.00 0.08
</code></pre>

<script>
$('#tab-node-02-get-classes-2-a').parent().next().next().hide();
$('#tab-node-02-get-classes-2-a').click(function(){
  $('#tab-node-02-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-3'>
<p><a id='tab-node-02-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.F5.6812.01     2  0.0000      0.956 0.00 1.00 0.00 0.00
#&gt; TCGA.BM.6198.01     2  0.2411      0.916 0.04 0.92 0.04 0.00
#&gt; TCGA.G5.6572.02     2  0.4372      0.861 0.04 0.84 0.04 0.08
#&gt; TCGA.EI.6506.01     3  0.1211      0.982 0.00 0.04 0.96 0.00
#&gt; TCGA.AG.A036.11     4  0.2011      1.000 0.08 0.00 0.00 0.92
#&gt; TCGA.AF.4110.01     2  0.0707      0.958 0.00 0.98 0.02 0.00
#&gt; TCGA.AH.6544.01     2  0.0000      0.956 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6861.01     3  0.1211      0.982 0.00 0.04 0.96 0.00
#&gt; TCGA.AF.2690.01     3  0.1637      0.970 0.00 0.06 0.94 0.00
#&gt; TCGA.EI.6881.01     2  0.0707      0.958 0.00 0.98 0.02 0.00
#&gt; TCGA.AF.2693.01     2  0.0707      0.958 0.00 0.98 0.02 0.00
#&gt; TCGA.AG.3731.11     4  0.2011      1.000 0.08 0.00 0.00 0.92
#&gt; TCGA.DC.4745.01     3  0.1637      0.970 0.00 0.06 0.94 0.00
#&gt; TCGA.EI.6507.01     2  0.0707      0.958 0.00 0.98 0.02 0.00
#&gt; TCGA.EI.6917.01     2  0.0707      0.958 0.00 0.98 0.02 0.00
#&gt; TCGA.DC.6681.01     3  0.1211      0.982 0.00 0.04 0.96 0.00
#&gt; TCGA.AG.3725.11     1  0.1211      1.000 0.96 0.00 0.04 0.00
#&gt; TCGA.F5.6813.01     2  0.0000      0.956 0.00 1.00 0.00 0.00
#&gt; TCGA.G5.6572.01     2  0.4372      0.861 0.04 0.84 0.04 0.08
#&gt; TCGA.CI.6621.01     2  0.1913      0.928 0.00 0.94 0.04 0.02
#&gt; TCGA.G5.6235.01     2  0.0707      0.958 0.00 0.98 0.02 0.00
#&gt; TCGA.AH.6547.01     3  0.1411      0.959 0.02 0.02 0.96 0.00
#&gt; TCGA.EI.6884.01     2  0.0707      0.958 0.00 0.98 0.02 0.00
#&gt; TCGA.AG.A020.11     1  0.1211      1.000 0.96 0.00 0.04 0.00
#&gt; TCGA.AG.A01Y.11     1  0.1211      1.000 0.96 0.00 0.04 0.00
#&gt; TCGA.AG.A01W.11     1  0.1211      1.000 0.96 0.00 0.04 0.00
#&gt; TCGA.AG.A02N.11     4  0.2011      1.000 0.08 0.00 0.00 0.92
</code></pre>

<script>
$('#tab-node-02-get-classes-3-a').parent().next().next().hide();
$('#tab-node-02-get-classes-3-a').click(function(){
  $('#tab-node-02-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-4'>
<p><a id='tab-node-02-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1   p2 p3 p4   p5
#&gt; TCGA.F5.6812.01     2   0.311      0.733  0 0.80  0  0 0.20
#&gt; TCGA.BM.6198.01     5   0.430     -0.176  0 0.48  0  0 0.52
#&gt; TCGA.G5.6572.02     5   0.228      0.642  0 0.12  0  0 0.88
#&gt; TCGA.EI.6506.01     3   0.000      1.000  0 0.00  1  0 0.00
#&gt; TCGA.AG.A036.11     4   0.000      1.000  0 0.00  0  1 0.00
#&gt; TCGA.AF.4110.01     2   0.141      0.883  0 0.94  0  0 0.06
#&gt; TCGA.AH.6544.01     2   0.104      0.888  0 0.96  0  0 0.04
#&gt; TCGA.F5.6861.01     3   0.000      1.000  0 0.00  1  0 0.00
#&gt; TCGA.AF.2690.01     3   0.000      1.000  0 0.00  1  0 0.00
#&gt; TCGA.EI.6881.01     2   0.000      0.897  0 1.00  0  0 0.00
#&gt; TCGA.AF.2693.01     2   0.173      0.874  0 0.92  0  0 0.08
#&gt; TCGA.AG.3731.11     4   0.000      1.000  0 0.00  0  1 0.00
#&gt; TCGA.DC.4745.01     3   0.000      1.000  0 0.00  1  0 0.00
#&gt; TCGA.EI.6507.01     2   0.000      0.897  0 1.00  0  0 0.00
#&gt; TCGA.EI.6917.01     2   0.000      0.897  0 1.00  0  0 0.00
#&gt; TCGA.DC.6681.01     3   0.000      1.000  0 0.00  1  0 0.00
#&gt; TCGA.AG.3725.11     1   0.000      1.000  1 0.00  0  0 0.00
#&gt; TCGA.F5.6813.01     2   0.173      0.872  0 0.92  0  0 0.08
#&gt; TCGA.G5.6572.01     5   0.228      0.642  0 0.12  0  0 0.88
#&gt; TCGA.CI.6621.01     2   0.406      0.326  0 0.64  0  0 0.36
#&gt; TCGA.G5.6235.01     2   0.000      0.897  0 1.00  0  0 0.00
#&gt; TCGA.AH.6547.01     3   0.000      1.000  0 0.00  1  0 0.00
#&gt; TCGA.EI.6884.01     2   0.000      0.897  0 1.00  0  0 0.00
#&gt; TCGA.AG.A020.11     1   0.000      1.000  1 0.00  0  0 0.00
#&gt; TCGA.AG.A01Y.11     1   0.000      1.000  1 0.00  0  0 0.00
#&gt; TCGA.AG.A01W.11     1   0.000      1.000  1 0.00  0  0 0.00
#&gt; TCGA.AG.A02N.11     4   0.000      1.000  0 0.00  0  1 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-4-a').parent().next().next().hide();
$('#tab-node-02-get-classes-4-a').click(function(){
  $('#tab-node-02-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-5'>
<p><a id='tab-node-02-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1   p2 p3 p4   p5   p6
#&gt; TCGA.F5.6812.01     2  0.4993     0.0795  0 0.56  0  0 0.08 0.36
#&gt; TCGA.BM.6198.01     6  0.3985     0.4074  0 0.14  0  0 0.10 0.76
#&gt; TCGA.G5.6572.02     5  0.0547     1.0000  0 0.02  0  0 0.98 0.00
#&gt; TCGA.EI.6506.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00
#&gt; TCGA.AG.A036.11     4  0.0000     1.0000  0 0.00  0  1 0.00 0.00
#&gt; TCGA.AF.4110.01     2  0.2631     0.7215  0 0.82  0  0 0.00 0.18
#&gt; TCGA.AH.6544.01     2  0.0000     0.8468  0 1.00  0  0 0.00 0.00
#&gt; TCGA.F5.6861.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00
#&gt; TCGA.AF.2690.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00
#&gt; TCGA.EI.6881.01     2  0.0000     0.8468  0 1.00  0  0 0.00 0.00
#&gt; TCGA.AF.2693.01     2  0.2631     0.7222  0 0.82  0  0 0.00 0.18
#&gt; TCGA.AG.3731.11     4  0.0000     1.0000  0 0.00  0  1 0.00 0.00
#&gt; TCGA.DC.4745.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00
#&gt; TCGA.EI.6507.01     2  0.1267     0.8130  0 0.94  0  0 0.00 0.06
#&gt; TCGA.EI.6917.01     2  0.0000     0.8468  0 1.00  0  0 0.00 0.00
#&gt; TCGA.DC.6681.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00
#&gt; TCGA.AG.3725.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00
#&gt; TCGA.F5.6813.01     2  0.2794     0.7582  0 0.86  0  0 0.06 0.08
#&gt; TCGA.G5.6572.01     5  0.0547     1.0000  0 0.02  0  0 0.98 0.00
#&gt; TCGA.CI.6621.01     6  0.4873     0.3202  0 0.42  0  0 0.06 0.52
#&gt; TCGA.G5.6235.01     2  0.0547     0.8382  0 0.98  0  0 0.00 0.02
#&gt; TCGA.AH.6547.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00
#&gt; TCGA.EI.6884.01     2  0.0000     0.8468  0 1.00  0  0 0.00 0.00
#&gt; TCGA.AG.A020.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00
#&gt; TCGA.AG.A01Y.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00
#&gt; TCGA.AG.A01W.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00
#&gt; TCGA.AG.A02N.11     4  0.0000     1.0000  0 0.00  0  1 0.00 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-5-a').parent().next().next().hide();
$('#tab-node-02-get-classes-5-a').click(function(){
  $('#tab-node-02-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-6'>
<p><a id='tab-node-02-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1   p2 p3 p4   p5   p6   p7
#&gt; TCGA.F5.6812.01     6  0.3396     0.1875  0 0.14  0  0 0.02 0.80 0.04
#&gt; TCGA.BM.6198.01     7  0.1928     0.0000  0 0.02  0  0 0.08 0.00 0.90
#&gt; TCGA.G5.6572.02     5  0.0000     1.0000  0 0.00  0  0 1.00 0.00 0.00
#&gt; TCGA.EI.6506.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00 0.00
#&gt; TCGA.AG.A036.11     4  0.0000     1.0000  0 0.00  0  1 0.00 0.00 0.00
#&gt; TCGA.AF.4110.01     2  0.2803     0.7751  0 0.84  0  0 0.00 0.06 0.10
#&gt; TCGA.AH.6544.01     2  0.1006     0.8532  0 0.96  0  0 0.02 0.02 0.00
#&gt; TCGA.F5.6861.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00 0.00
#&gt; TCGA.AF.2690.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00 0.00
#&gt; TCGA.EI.6881.01     2  0.0000     0.8623  0 1.00  0  0 0.00 0.00 0.00
#&gt; TCGA.AF.2693.01     2  0.4742     0.4850  0 0.62  0  0 0.00 0.22 0.16
#&gt; TCGA.AG.3731.11     4  0.0000     1.0000  0 0.00  0  1 0.00 0.00 0.00
#&gt; TCGA.DC.4745.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00 0.00
#&gt; TCGA.EI.6507.01     2  0.1928     0.8185  0 0.90  0  0 0.00 0.08 0.02
#&gt; TCGA.EI.6917.01     2  0.0504     0.8597  0 0.98  0  0 0.00 0.00 0.02
#&gt; TCGA.DC.6681.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00 0.00
#&gt; TCGA.AG.3725.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.F5.6813.01     2  0.3661     0.6579  0 0.74  0  0 0.02 0.02 0.22
#&gt; TCGA.G5.6572.01     5  0.0000     1.0000  0 0.00  0  0 1.00 0.00 0.00
#&gt; TCGA.CI.6621.01     6  0.6264    -0.0517  0 0.12  0  0 0.10 0.40 0.38
#&gt; TCGA.G5.6235.01     2  0.0504     0.8597  0 0.98  0  0 0.00 0.00 0.02
#&gt; TCGA.AH.6547.01     3  0.0000     1.0000  0 0.00  1  0 0.00 0.00 0.00
#&gt; TCGA.EI.6884.01     2  0.0000     0.8623  0 1.00  0  0 0.00 0.00 0.00
#&gt; TCGA.AG.A020.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.AG.A01Y.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.11     1  0.0000     1.0000  1 0.00  0  0 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.11     4  0.0000     1.0000  0 0.00  0  1 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-6-a').parent().next().next().hide();
$('#tab-node-02-get-classes-6-a').click(function(){
  $('#tab-node-02-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-02-get-classes-7'>
<p><a id='tab-node-02-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1   p2   p3 p4   p5   p6   p7   p8
#&gt; TCGA.F5.6812.01     6  0.0000    0.00000  0 0.00 0.00  0 0.00 1.00 0.00 0.00
#&gt; TCGA.BM.6198.01     7  0.1341    0.00000  0 0.00 0.00  0 0.00 0.08 0.92 0.00
#&gt; TCGA.G5.6572.02     5  0.0000    1.00000  0 0.00 0.00  0 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6506.01     3  0.0000    0.99257  0 0.00 1.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A036.11     4  0.0000    1.00000  0 0.00 0.00  1 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.4110.01     2  0.4204    0.63448  0 0.72 0.00  0 0.00 0.04 0.12 0.12
#&gt; TCGA.AH.6544.01     2  0.0471    0.81709  0 0.98 0.00  0 0.00 0.00 0.00 0.02
#&gt; TCGA.F5.6861.01     3  0.0000    0.99257  0 0.00 1.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.2690.01     3  0.0000    0.99257  0 0.00 1.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6881.01     2  0.0471    0.81728  0 0.98 0.00  0 0.00 0.00 0.00 0.02
#&gt; TCGA.AF.2693.01     2  0.6166   -0.00975  0 0.38 0.00  0 0.00 0.16 0.12 0.34
#&gt; TCGA.AG.3731.11     4  0.0000    1.00000  0 0.00 0.00  1 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.4745.01     3  0.0808    0.96199  0 0.00 0.96  0 0.00 0.00 0.00 0.04
#&gt; TCGA.EI.6507.01     2  0.1275    0.79650  0 0.94 0.00  0 0.00 0.00 0.02 0.04
#&gt; TCGA.EI.6917.01     2  0.0000    0.82231  0 1.00 0.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.6681.01     3  0.0000    0.99257  0 0.00 1.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.3725.11     1  0.0000    1.00000  1 0.00 0.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6813.01     2  0.5130    0.43787  0 0.62 0.00  0 0.02 0.04 0.10 0.22
#&gt; TCGA.G5.6572.01     5  0.0000    1.00000  0 0.00 0.00  0 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6621.01     8  0.3928    0.00000  0 0.02 0.00  0 0.02 0.04 0.18 0.74
#&gt; TCGA.G5.6235.01     2  0.0000    0.82231  0 1.00 0.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AH.6547.01     3  0.0000    0.99257  0 0.00 1.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6884.01     2  0.0000    0.82231  0 1.00 0.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A020.11     1  0.0000    1.00000  1 0.00 0.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01Y.11     1  0.0000    1.00000  1 0.00 0.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A01W.11     1  0.0000    1.00000  1 0.00 0.00  0 0.00 0.00 0.00 0.00
#&gt; TCGA.AG.A02N.11     4  0.0000    1.00000  0 0.00 0.00  1 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-02-get-classes-7-a').parent().next().next().hide();
$('#tab-node-02-get-classes-7-a').click(function(){
  $('#tab-node-02-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-02-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-02-consensus-heatmap'>
<ul>
<li><a href='#tab-node-02-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-02-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-02-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-02-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-02-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-02-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-02-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-02-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-02-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-02-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-02-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-02-membership-heatmap'>
<ul>
<li><a href='#tab-node-02-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-02-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-02-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-02-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-02-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-02-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-02-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-1-1.png" alt="plot of chunk tab-node-02-membership-heatmap-1"/></p>

</div>
<div id='tab-node-02-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-2-1.png" alt="plot of chunk tab-node-02-membership-heatmap-2"/></p>

</div>
<div id='tab-node-02-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-3-1.png" alt="plot of chunk tab-node-02-membership-heatmap-3"/></p>

</div>
<div id='tab-node-02-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-4-1.png" alt="plot of chunk tab-node-02-membership-heatmap-4"/></p>

</div>
<div id='tab-node-02-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-5-1.png" alt="plot of chunk tab-node-02-membership-heatmap-5"/></p>

</div>
<div id='tab-node-02-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-6-1.png" alt="plot of chunk tab-node-02-membership-heatmap-6"/></p>

</div>
<div id='tab-node-02-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-02-membership-heatmap-7-1.png" alt="plot of chunk tab-node-02-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-02-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-02-get-signatures'>
<ul>
<li><a href='#tab-node-02-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-02-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-02-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-02-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-02-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-02-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-02-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-1-1.png" alt="plot of chunk tab-node-02-get-signatures-1"/></p>

</div>
<div id='tab-node-02-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-2-1.png" alt="plot of chunk tab-node-02-get-signatures-2"/></p>

</div>
<div id='tab-node-02-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-3-1.png" alt="plot of chunk tab-node-02-get-signatures-3"/></p>

</div>
<div id='tab-node-02-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-4-1.png" alt="plot of chunk tab-node-02-get-signatures-4"/></p>

</div>
<div id='tab-node-02-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-5-1.png" alt="plot of chunk tab-node-02-get-signatures-5"/></p>

</div>
<div id='tab-node-02-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-6-1.png" alt="plot of chunk tab-node-02-get-signatures-6"/></p>

</div>
<div id='tab-node-02-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-02-get-signatures-7-1.png" alt="plot of chunk tab-node-02-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-02-signature_compare](figure_cola/node-02-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-02-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-02-dimension-reduction'>
<ul>
<li><a href='#tab-node-02-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-02-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-02-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-02-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-02-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-02-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-02-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-02-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-1-1.png" alt="plot of chunk tab-node-02-dimension-reduction-1"/></p>

</div>
<div id='tab-node-02-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-2-1.png" alt="plot of chunk tab-node-02-dimension-reduction-2"/></p>

</div>
<div id='tab-node-02-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-3-1.png" alt="plot of chunk tab-node-02-dimension-reduction-3"/></p>

</div>
<div id='tab-node-02-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-4-1.png" alt="plot of chunk tab-node-02-dimension-reduction-4"/></p>

</div>
<div id='tab-node-02-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-5-1.png" alt="plot of chunk tab-node-02-dimension-reduction-5"/></p>

</div>
<div id='tab-node-02-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-6-1.png" alt="plot of chunk tab-node-02-dimension-reduction-6"/></p>

</div>
<div id='tab-node-02-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-02-dimension-reduction-7-1.png" alt="plot of chunk tab-node-02-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-02-collect-classes](figure_cola/node-02-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node03


Parent node: [Node0](#Node0).
Child nodes: 
                [Node011](#Node011)
        ,
                Node012-leaf
        ,
                Node013-leaf
        ,
                Node021-leaf
        ,
                Node022-leaf
        ,
                Node023-leaf
        ,
                [Node031](#Node031)
        ,
                [Node032](#Node032)
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["03"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 47 columns.
#>   Top rows (1000) are extracted by 'SD' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 2.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-03-collect-plots](figure_cola/node-03-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-03-select-partition-number](figure_cola/node-03-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           0.965       0.985         0.4544 0.556   0.556
#> 3 3 0.518           0.706       0.836         0.3952 0.796   0.634
#> 4 4 0.539           0.653       0.818         0.1131 0.845   0.601
#> 5 5 0.547           0.482       0.714         0.0277 0.902   0.701
#> 6 6 0.543           0.485       0.703         0.0375 0.857   0.580
#> 7 7 0.527           0.421       0.646         0.0124 0.846   0.564
#> 8 8 0.551           0.377       0.630         0.0382 0.881   0.622
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 2
```


Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-03-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-03-get-classes'>
<ul>
<li><a href='#tab-node-03-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-03-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-03-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-03-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-03-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-03-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-03-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-03-get-classes-1'>
<p><a id='tab-node-03-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2
#&gt; TCGA.AH.6644.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.AH.6903.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.DC.6157.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.3592.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.DT.5265.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.CI.6620.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.AG.3731.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.G5.6233.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.F5.6465.01     2   0.971      0.364 0.40 0.60
#&gt; TCGA.DY.A1H8.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.CL.5917.01     2   0.402      0.911 0.08 0.92
#&gt; TCGA.EI.6511.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.CI.6619.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.6136.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.EI.7004.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.F5.6702.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6512.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.DY.A0XA.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.F5.6863.01     2   0.402      0.910 0.08 0.92
#&gt; TCGA.AF.6655.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.CI.6624.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.EI.6883.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.AG.A036.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.CI.6623.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DC.6156.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.F5.6864.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.DC.6160.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.F5.6814.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.F5.6464.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.AF.A56N.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.EF.5831.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.AG.3732.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.DY.A1DC.01     2   0.141      0.963 0.02 0.98
#&gt; TCGA.EI.6885.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.A56L.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.AF.A56K.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AG.A01Y.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AF.2687.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.AH.6643.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.DC.6155.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.CL.4957.01     2   0.141      0.963 0.02 0.98
#&gt; TCGA.F5.6571.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.DC.6682.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.EI.6509.01     1   0.000      1.000 1.00 0.00
#&gt; TCGA.CI.6622.01     2   0.000      0.977 0.00 1.00
#&gt; TCGA.EI.7002.01     2   0.529      0.863 0.12 0.88
#&gt; TCGA.DC.4749.01     1   0.000      1.000 1.00 0.00
</code></pre>

<script>
$('#tab-node-03-get-classes-1-a').parent().next().next().hide();
$('#tab-node-03-get-classes-1-a').click(function(){
  $('#tab-node-03-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-2'>
<p><a id='tab-node-03-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.AH.6644.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.AH.6903.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.DC.6157.01     1  0.2066      0.747 0.94 0.00 0.06
#&gt; TCGA.AG.3592.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.DT.5265.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.CI.6620.01     2  0.5706      0.360 0.00 0.68 0.32
#&gt; TCGA.AG.3731.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.G5.6233.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.F5.6465.01     3  0.4209      0.808 0.02 0.12 0.86
#&gt; TCGA.DY.A1H8.01     3  0.5016      0.843 0.00 0.24 0.76
#&gt; TCGA.CL.5917.01     3  0.3340      0.809 0.00 0.12 0.88
#&gt; TCGA.EI.6511.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.CI.6619.01     1  0.2066      0.746 0.94 0.00 0.06
#&gt; TCGA.AF.6136.01     2  0.5835      0.306 0.00 0.66 0.34
#&gt; TCGA.EI.7004.01     2  0.2537      0.797 0.00 0.92 0.08
#&gt; TCGA.F5.6702.01     1  0.0000      0.750 1.00 0.00 0.00
#&gt; TCGA.EI.6512.01     2  0.0892      0.854 0.00 0.98 0.02
#&gt; TCGA.DY.A0XA.01     1  0.6244      0.491 0.56 0.00 0.44
#&gt; TCGA.F5.6863.01     3  0.2959      0.782 0.00 0.10 0.90
#&gt; TCGA.AF.6655.01     1  0.6651      0.579 0.64 0.02 0.34
#&gt; TCGA.CI.6624.01     1  0.6302      0.417 0.52 0.00 0.48
#&gt; TCGA.EI.6883.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.AG.A036.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.CI.6623.01     1  0.5643      0.696 0.76 0.02 0.22
#&gt; TCGA.DC.6156.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.F5.6864.01     1  0.5835      0.614 0.66 0.00 0.34
#&gt; TCGA.DC.6160.01     1  0.5643      0.694 0.76 0.02 0.22
#&gt; TCGA.F5.6814.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.F5.6464.01     3  0.5948      0.675 0.00 0.36 0.64
#&gt; TCGA.AF.A56N.01     2  0.6244     -0.112 0.00 0.56 0.44
#&gt; TCGA.EF.5831.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.AG.3732.01     3  0.5706      0.746 0.00 0.32 0.68
#&gt; TCGA.DY.A1DC.01     3  0.5016      0.813 0.00 0.24 0.76
#&gt; TCGA.EI.6885.01     1  0.6045      0.574 0.62 0.00 0.38
#&gt; TCGA.AF.A56L.01     3  0.5706      0.763 0.00 0.32 0.68
#&gt; TCGA.AF.A56K.01     1  0.0000      0.750 1.00 0.00 0.00
#&gt; TCGA.AG.A01Y.01     1  0.5948      0.596 0.64 0.00 0.36
#&gt; TCGA.AF.2687.01     1  0.2066      0.746 0.94 0.00 0.06
#&gt; TCGA.AH.6643.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.DC.6155.01     3  0.5216      0.828 0.00 0.26 0.74
#&gt; TCGA.CL.4957.01     3  0.4291      0.844 0.00 0.18 0.82
#&gt; TCGA.F5.6571.01     2  0.6302     -0.272 0.00 0.52 0.48
#&gt; TCGA.DC.6682.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.EI.6509.01     1  0.4291      0.722 0.82 0.00 0.18
#&gt; TCGA.CI.6622.01     2  0.0000      0.871 0.00 1.00 0.00
#&gt; TCGA.EI.7002.01     2  0.7144      0.471 0.22 0.70 0.08
#&gt; TCGA.DC.4749.01     1  0.5858      0.685 0.74 0.02 0.24
</code></pre>

<script>
$('#tab-node-03-get-classes-2-a').parent().next().next().hide();
$('#tab-node-03-get-classes-2-a').click(function(){
  $('#tab-node-03-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-3'>
<p><a id='tab-node-03-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.AH.6644.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.AH.6903.01     2  0.2706    0.83975 0.00 0.90 0.08 0.02
#&gt; TCGA.DC.6157.01     4  0.4713    0.32332 0.36 0.00 0.00 0.64
#&gt; TCGA.AG.3592.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.DT.5265.01     2  0.0707    0.89979 0.00 0.98 0.02 0.00
#&gt; TCGA.CI.6620.01     3  0.4994    0.34591 0.00 0.48 0.52 0.00
#&gt; TCGA.AG.3731.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.G5.6233.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6465.01     3  0.6253    0.53408 0.18 0.02 0.70 0.10
#&gt; TCGA.DY.A1H8.01     3  0.3935    0.68633 0.06 0.06 0.86 0.02
#&gt; TCGA.CL.5917.01     3  0.4372    0.64464 0.08 0.04 0.84 0.04
#&gt; TCGA.EI.6511.01     2  0.2335    0.85815 0.00 0.92 0.02 0.06
#&gt; TCGA.CI.6619.01     1  0.4624    0.38587 0.66 0.00 0.00 0.34
#&gt; TCGA.AF.6136.01     3  0.4948    0.44456 0.00 0.44 0.56 0.00
#&gt; TCGA.EI.7004.01     2  0.3801    0.60440 0.00 0.78 0.22 0.00
#&gt; TCGA.F5.6702.01     4  0.4994   -0.13494 0.48 0.00 0.00 0.52
#&gt; TCGA.EI.6512.01     2  0.3975    0.55724 0.00 0.76 0.24 0.00
#&gt; TCGA.DY.A0XA.01     1  0.2335    0.64587 0.92 0.00 0.06 0.02
#&gt; TCGA.F5.6863.01     3  0.2706    0.62600 0.00 0.02 0.90 0.08
#&gt; TCGA.AF.6655.01     4  0.2706    0.66031 0.00 0.02 0.08 0.90
#&gt; TCGA.CI.6624.01     1  0.6089    0.40978 0.64 0.00 0.28 0.08
#&gt; TCGA.EI.6883.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.A036.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.CI.6623.01     4  0.2830    0.65909 0.04 0.00 0.06 0.90
#&gt; TCGA.DC.6156.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6864.01     1  0.1211    0.69903 0.96 0.00 0.00 0.04
#&gt; TCGA.DC.6160.01     4  0.6755    0.58869 0.10 0.08 0.12 0.70
#&gt; TCGA.F5.6814.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6464.01     3  0.1637    0.68785 0.00 0.06 0.94 0.00
#&gt; TCGA.AF.A56N.01     3  0.5487    0.52036 0.02 0.40 0.58 0.00
#&gt; TCGA.EF.5831.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.1637    0.68908 0.00 0.06 0.94 0.00
#&gt; TCGA.DY.A1DC.01     3  0.8215    0.56121 0.16 0.32 0.48 0.04
#&gt; TCGA.EI.6885.01     1  0.0000    0.69327 1.00 0.00 0.00 0.00
#&gt; TCGA.AF.A56L.01     3  0.8241    0.51071 0.22 0.34 0.42 0.02
#&gt; TCGA.AF.A56K.01     1  0.4994    0.00293 0.52 0.00 0.00 0.48
#&gt; TCGA.AG.A01Y.01     1  0.0707    0.69978 0.98 0.00 0.00 0.02
#&gt; TCGA.AF.2687.01     1  0.3610    0.59095 0.80 0.00 0.00 0.20
#&gt; TCGA.AH.6643.01     2  0.2335    0.85833 0.00 0.92 0.02 0.06
#&gt; TCGA.DC.6155.01     3  0.3606    0.71325 0.02 0.14 0.84 0.00
#&gt; TCGA.CL.4957.01     3  0.5512    0.71033 0.08 0.14 0.76 0.02
#&gt; TCGA.F5.6571.01     3  0.4790    0.55154 0.00 0.38 0.62 0.00
#&gt; TCGA.DC.6682.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6509.01     4  0.5902    0.54640 0.16 0.00 0.14 0.70
#&gt; TCGA.CI.6622.01     2  0.0000    0.91435 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.7002.01     2  0.7736    0.39117 0.20 0.60 0.06 0.14
#&gt; TCGA.DC.4749.01     4  0.5531    0.61439 0.06 0.08 0.08 0.78
</code></pre>

<script>
$('#tab-node-03-get-classes-3-a').parent().next().next().hide();
$('#tab-node-03-get-classes-3-a').click(function(){
  $('#tab-node-03-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-4'>
<p><a id='tab-node-03-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.AH.6644.01     2  0.0609     0.8222 0.00 0.98 0.02 0.00 0.00
#&gt; TCGA.AH.6903.01     2  0.3421     0.7301 0.00 0.84 0.08 0.08 0.00
#&gt; TCGA.DC.6157.01     4  0.7144     0.0281 0.32 0.00 0.02 0.42 0.24
#&gt; TCGA.AG.3592.01     2  0.0609     0.8222 0.00 0.98 0.02 0.00 0.00
#&gt; TCGA.DT.5265.01     2  0.0000     0.8238 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6620.01     2  0.4818    -0.0288 0.00 0.52 0.46 0.00 0.02
#&gt; TCGA.AG.3731.01     2  0.0000     0.8238 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.G5.6233.01     2  0.0000     0.8238 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6465.01     3  0.7022     0.3826 0.18 0.00 0.58 0.14 0.10
#&gt; TCGA.DY.A1H8.01     3  0.4278     0.6554 0.02 0.14 0.80 0.02 0.02
#&gt; TCGA.CL.5917.01     3  0.5818     0.4842 0.12 0.00 0.70 0.08 0.10
#&gt; TCGA.EI.6511.01     2  0.3463     0.7419 0.00 0.84 0.02 0.12 0.02
#&gt; TCGA.CI.6619.01     1  0.5979     0.3281 0.52 0.00 0.00 0.36 0.12
#&gt; TCGA.AF.6136.01     2  0.4262     0.1513 0.00 0.56 0.44 0.00 0.00
#&gt; TCGA.EI.7004.01     2  0.2516     0.7254 0.00 0.86 0.14 0.00 0.00
#&gt; TCGA.F5.6702.01     1  0.6422     0.2321 0.46 0.00 0.00 0.36 0.18
#&gt; TCGA.EI.6512.01     2  0.2929     0.6750 0.00 0.82 0.18 0.00 0.00
#&gt; TCGA.DY.A0XA.01     1  0.7231     0.2462 0.52 0.00 0.22 0.06 0.20
#&gt; TCGA.F5.6863.01     3  0.5208     0.4922 0.02 0.00 0.72 0.16 0.10
#&gt; TCGA.AF.6655.01     4  0.4373     0.0323 0.00 0.00 0.08 0.76 0.16
#&gt; TCGA.CI.6624.01     1  0.7798     0.1610 0.46 0.00 0.26 0.12 0.16
#&gt; TCGA.EI.6883.01     2  0.0609     0.8222 0.00 0.98 0.02 0.00 0.00
#&gt; TCGA.AG.A036.01     2  0.0609     0.8194 0.00 0.98 0.00 0.02 0.00
#&gt; TCGA.CI.6623.01     4  0.4634     0.2352 0.04 0.00 0.06 0.78 0.12
#&gt; TCGA.DC.6156.01     2  0.1216     0.8143 0.00 0.96 0.00 0.02 0.02
#&gt; TCGA.F5.6864.01     1  0.4974     0.4320 0.76 0.00 0.06 0.12 0.06
#&gt; TCGA.DC.6160.01     4  0.6335     0.2255 0.08 0.06 0.06 0.70 0.10
#&gt; TCGA.F5.6814.01     2  0.0000     0.8238 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6464.01     3  0.5409     0.6471 0.02 0.18 0.72 0.02 0.06
#&gt; TCGA.AF.A56N.01     2  0.4829    -0.0257 0.00 0.50 0.48 0.00 0.02
#&gt; TCGA.EF.5831.01     2  0.0609     0.8209 0.00 0.98 0.00 0.00 0.02
#&gt; TCGA.AG.3732.01     3  0.3977     0.6340 0.00 0.10 0.82 0.02 0.06
#&gt; TCGA.DY.A1DC.01     3  0.9137     0.3619 0.08 0.26 0.38 0.14 0.14
#&gt; TCGA.EI.6885.01     1  0.4281     0.3950 0.80 0.00 0.10 0.02 0.08
#&gt; TCGA.AF.A56L.01     3  0.8471     0.4178 0.14 0.34 0.36 0.02 0.14
#&gt; TCGA.AF.A56K.01     1  0.6194     0.2112 0.48 0.00 0.02 0.42 0.08
#&gt; TCGA.AG.A01Y.01     1  0.2610     0.4344 0.90 0.00 0.02 0.06 0.02
#&gt; TCGA.AF.2687.01     1  0.5680     0.3590 0.62 0.00 0.00 0.24 0.14
#&gt; TCGA.AH.6643.01     2  0.1648     0.8085 0.00 0.94 0.00 0.04 0.02
#&gt; TCGA.DC.6155.01     3  0.4050     0.6618 0.02 0.12 0.82 0.02 0.02
#&gt; TCGA.CL.4957.01     3  0.5449     0.6238 0.06 0.08 0.76 0.06 0.04
#&gt; TCGA.F5.6571.01     3  0.4726     0.2965 0.00 0.40 0.58 0.00 0.02
#&gt; TCGA.DC.6682.01     2  0.0000     0.8238 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6509.01     5  0.6671     0.0000 0.14 0.00 0.02 0.36 0.48
#&gt; TCGA.CI.6622.01     2  0.1216     0.8136 0.00 0.96 0.02 0.00 0.02
#&gt; TCGA.EI.7002.01     2  0.9285    -0.0951 0.12 0.38 0.12 0.24 0.14
#&gt; TCGA.DC.4749.01     4  0.6827     0.1623 0.04 0.04 0.06 0.58 0.28
</code></pre>

<script>
$('#tab-node-03-get-classes-4-a').parent().next().next().hide();
$('#tab-node-03-get-classes-4-a').click(function(){
  $('#tab-node-03-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-5'>
<p><a id='tab-node-03-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.AH.6644.01     2  0.0937     0.7961 0.00 0.96 0.00 0.00 0.00 0.04
#&gt; TCGA.AH.6903.01     2  0.5924     0.5495 0.00 0.66 0.14 0.12 0.04 0.04
#&gt; TCGA.DC.6157.01     5  0.5190     0.1373 0.04 0.00 0.00 0.10 0.68 0.18
#&gt; TCGA.AG.3592.01     2  0.1092     0.7984 0.00 0.96 0.00 0.02 0.00 0.02
#&gt; TCGA.DT.5265.01     2  0.0547     0.7962 0.00 0.98 0.02 0.00 0.00 0.00
#&gt; TCGA.CI.6620.01     3  0.3706     0.4625 0.00 0.38 0.62 0.00 0.00 0.00
#&gt; TCGA.AG.3731.01     2  0.0547     0.7984 0.00 0.98 0.00 0.00 0.00 0.02
#&gt; TCGA.G5.6233.01     2  0.1092     0.7941 0.00 0.96 0.02 0.00 0.00 0.02
#&gt; TCGA.F5.6465.01     3  0.7645     0.1185 0.22 0.04 0.48 0.18 0.06 0.02
#&gt; TCGA.DY.A1H8.01     3  0.4664     0.5915 0.00 0.14 0.74 0.06 0.00 0.06
#&gt; TCGA.CL.5917.01     3  0.7416     0.2085 0.24 0.02 0.48 0.06 0.02 0.18
#&gt; TCGA.EI.6511.01     2  0.4983     0.6863 0.02 0.76 0.04 0.10 0.02 0.06
#&gt; TCGA.CI.6619.01     5  0.4558     0.6167 0.18 0.00 0.02 0.02 0.74 0.04
#&gt; TCGA.AF.6136.01     3  0.4646     0.2313 0.00 0.46 0.50 0.00 0.00 0.04
#&gt; TCGA.EI.7004.01     2  0.3916     0.4263 0.00 0.68 0.30 0.00 0.00 0.02
#&gt; TCGA.F5.6702.01     5  0.4247     0.6073 0.24 0.00 0.00 0.06 0.70 0.00
#&gt; TCGA.EI.6512.01     2  0.3499     0.3912 0.00 0.68 0.32 0.00 0.00 0.00
#&gt; TCGA.DY.A0XA.01     1  0.5607     0.4561 0.68 0.00 0.16 0.02 0.06 0.08
#&gt; TCGA.F5.6863.01     3  0.5831     0.4184 0.10 0.04 0.64 0.20 0.00 0.02
#&gt; TCGA.AF.6655.01     4  0.5603     0.4327 0.02 0.00 0.06 0.64 0.24 0.04
#&gt; TCGA.CI.6624.01     1  0.7096     0.3109 0.56 0.00 0.12 0.10 0.16 0.06
#&gt; TCGA.EI.6883.01     2  0.0547     0.8004 0.00 0.98 0.00 0.02 0.00 0.00
#&gt; TCGA.AG.A036.01     2  0.1267     0.7927 0.00 0.94 0.00 0.06 0.00 0.00
#&gt; TCGA.CI.6623.01     4  0.4844     0.3955 0.02 0.00 0.04 0.62 0.32 0.00
#&gt; TCGA.DC.6156.01     2  0.2938     0.7738 0.04 0.88 0.02 0.02 0.00 0.04
#&gt; TCGA.F5.6864.01     1  0.4162     0.4167 0.78 0.00 0.04 0.06 0.12 0.00
#&gt; TCGA.DC.6160.01     4  0.7316     0.2438 0.08 0.02 0.06 0.40 0.40 0.04
#&gt; TCGA.F5.6814.01     2  0.0000     0.7995 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6464.01     3  0.4066     0.5938 0.00 0.12 0.78 0.08 0.00 0.02
#&gt; TCGA.AF.A56N.01     3  0.4787     0.2731 0.02 0.44 0.52 0.02 0.00 0.00
#&gt; TCGA.EF.5831.01     2  0.0547     0.8004 0.00 0.98 0.00 0.02 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.3697     0.5603 0.00 0.06 0.82 0.04 0.00 0.08
#&gt; TCGA.DY.A1DC.01     1  0.8902    -0.0719 0.28 0.28 0.18 0.16 0.02 0.08
#&gt; TCGA.EI.6885.01     1  0.3103     0.4790 0.86 0.00 0.04 0.00 0.06 0.04
#&gt; TCGA.AF.A56L.01     2  0.6540    -0.3466 0.30 0.36 0.32 0.00 0.00 0.02
#&gt; TCGA.AF.A56K.01     5  0.4703     0.5745 0.18 0.00 0.00 0.04 0.72 0.06
#&gt; TCGA.AG.A01Y.01     1  0.3928     0.3665 0.76 0.00 0.00 0.00 0.08 0.16
#&gt; TCGA.AF.2687.01     5  0.4913     0.4991 0.34 0.00 0.02 0.00 0.60 0.04
#&gt; TCGA.AH.6643.01     2  0.3795     0.7092 0.00 0.80 0.02 0.06 0.00 0.12
#&gt; TCGA.DC.6155.01     3  0.3846     0.5728 0.08 0.10 0.80 0.00 0.00 0.02
#&gt; TCGA.CL.4957.01     3  0.7063     0.3621 0.18 0.08 0.54 0.04 0.00 0.16
#&gt; TCGA.F5.6571.01     3  0.4502     0.5248 0.02 0.32 0.64 0.00 0.00 0.02
#&gt; TCGA.DC.6682.01     2  0.0937     0.7968 0.00 0.96 0.00 0.00 0.00 0.04
#&gt; TCGA.EI.6509.01     4  0.6884     0.2251 0.06 0.00 0.02 0.42 0.12 0.38
#&gt; TCGA.CI.6622.01     2  0.1092     0.7984 0.00 0.96 0.00 0.02 0.00 0.02
#&gt; TCGA.EI.7002.01     2  0.9185     0.0130 0.12 0.38 0.10 0.10 0.18 0.12
#&gt; TCGA.DC.4749.01     4  0.8191     0.2191 0.08 0.12 0.00 0.38 0.26 0.16
</code></pre>

<script>
$('#tab-node-03-get-classes-5-a').parent().next().next().hide();
$('#tab-node-03-get-classes-5-a').click(function(){
  $('#tab-node-03-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-6'>
<p><a id='tab-node-03-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.AH.6644.01     2  0.1505     0.7138 0.00 0.94 0.00 0.02 0.02 0.02 0.00
#&gt; TCGA.AH.6903.01     2  0.6813     0.3087 0.00 0.54 0.18 0.14 0.02 0.04 0.08
#&gt; TCGA.DC.6157.01     1  0.7609     0.0911 0.40 0.00 0.02 0.28 0.08 0.14 0.08
#&gt; TCGA.AG.3592.01     2  0.1006     0.7202 0.00 0.96 0.00 0.02 0.02 0.00 0.00
#&gt; TCGA.DT.5265.01     2  0.0504     0.7204 0.00 0.98 0.02 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6620.01     2  0.4720     0.2371 0.00 0.58 0.36 0.02 0.02 0.02 0.00
#&gt; TCGA.AG.3731.01     2  0.0504     0.7204 0.00 0.98 0.02 0.00 0.00 0.00 0.00
#&gt; TCGA.G5.6233.01     2  0.0000     0.7212 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6465.01     3  0.7487     0.3154 0.08 0.04 0.52 0.18 0.06 0.10 0.02
#&gt; TCGA.DY.A1H8.01     3  0.6608     0.4391 0.00 0.18 0.50 0.06 0.22 0.04 0.00
#&gt; TCGA.CL.5917.01     3  0.6667     0.3771 0.02 0.06 0.50 0.00 0.26 0.14 0.02
#&gt; TCGA.EI.6511.01     2  0.5036     0.5363 0.00 0.68 0.04 0.18 0.08 0.02 0.00
#&gt; TCGA.CI.6619.01     1  0.2509     0.5117 0.88 0.00 0.00 0.06 0.00 0.04 0.02
#&gt; TCGA.AF.6136.01     2  0.4852    -0.0749 0.00 0.48 0.46 0.02 0.02 0.02 0.00
#&gt; TCGA.EI.7004.01     2  0.3055     0.6461 0.00 0.82 0.14 0.02 0.00 0.02 0.00
#&gt; TCGA.F5.6702.01     1  0.4364     0.4519 0.76 0.00 0.00 0.12 0.04 0.04 0.04
#&gt; TCGA.EI.6512.01     2  0.2708     0.5871 0.00 0.78 0.22 0.00 0.00 0.00 0.00
#&gt; TCGA.DY.A0XA.01     1  0.6834     0.3540 0.40 0.00 0.20 0.00 0.08 0.30 0.02
#&gt; TCGA.F5.6863.01     3  0.6112     0.3975 0.00 0.04 0.64 0.04 0.14 0.08 0.06
#&gt; TCGA.AF.6655.01     4  0.5976     0.1175 0.06 0.00 0.04 0.62 0.06 0.02 0.20
#&gt; TCGA.CI.6624.01     1  0.6612     0.3241 0.42 0.00 0.14 0.02 0.00 0.34 0.08
#&gt; TCGA.EI.6883.01     2  0.1006     0.7202 0.00 0.96 0.00 0.02 0.02 0.00 0.00
#&gt; TCGA.AG.A036.01     2  0.3670     0.6269 0.00 0.76 0.00 0.14 0.10 0.00 0.00
#&gt; TCGA.CI.6623.01     4  0.6138     0.2897 0.10 0.02 0.04 0.60 0.04 0.00 0.20
#&gt; TCGA.DC.6156.01     2  0.2706     0.7040 0.00 0.88 0.04 0.04 0.02 0.00 0.02
#&gt; TCGA.F5.6864.01     1  0.5897     0.5095 0.56 0.00 0.06 0.06 0.04 0.28 0.00
#&gt; TCGA.DC.6160.01     4  0.7820     0.1875 0.22 0.10 0.02 0.42 0.04 0.02 0.18
#&gt; TCGA.F5.6814.01     2  0.1505     0.7212 0.00 0.94 0.02 0.02 0.02 0.00 0.00
#&gt; TCGA.F5.6464.01     3  0.4533     0.5006 0.00 0.26 0.66 0.00 0.04 0.04 0.00
#&gt; TCGA.AF.A56N.01     2  0.4718     0.2937 0.00 0.60 0.32 0.02 0.06 0.00 0.00
#&gt; TCGA.EF.5831.01     2  0.0863     0.7211 0.00 0.96 0.00 0.04 0.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.4405     0.4674 0.00 0.08 0.74 0.00 0.08 0.10 0.00
#&gt; TCGA.DY.A1DC.01     2  0.8400    -0.3173 0.00 0.28 0.26 0.08 0.20 0.14 0.04
#&gt; TCGA.EI.6885.01     1  0.4657     0.5150 0.54 0.00 0.04 0.00 0.02 0.40 0.00
#&gt; TCGA.AF.A56L.01     3  0.7609     0.3592 0.14 0.30 0.34 0.00 0.08 0.14 0.00
#&gt; TCGA.AF.A56K.01     1  0.4809     0.4649 0.70 0.00 0.00 0.12 0.02 0.14 0.02
#&gt; TCGA.AG.A01Y.01     1  0.6244     0.3841 0.44 0.00 0.04 0.02 0.08 0.40 0.02
#&gt; TCGA.AF.2687.01     1  0.2159     0.5413 0.90 0.00 0.00 0.00 0.02 0.06 0.02
#&gt; TCGA.AH.6643.01     2  0.5240     0.5595 0.00 0.70 0.06 0.08 0.10 0.00 0.06
#&gt; TCGA.DC.6155.01     3  0.5482     0.5460 0.00 0.22 0.62 0.02 0.04 0.10 0.00
#&gt; TCGA.CL.4957.01     3  0.5717     0.4124 0.00 0.06 0.54 0.00 0.28 0.12 0.00
#&gt; TCGA.F5.6571.01     3  0.4852     0.0336 0.00 0.46 0.48 0.02 0.02 0.02 0.00
#&gt; TCGA.DC.6682.01     2  0.0504     0.7204 0.00 0.98 0.02 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6509.01     7  0.1505     0.0000 0.02 0.00 0.02 0.02 0.00 0.00 0.94
#&gt; TCGA.CI.6622.01     2  0.2509     0.6976 0.00 0.88 0.00 0.04 0.06 0.02 0.00
#&gt; TCGA.EI.7002.01     2  0.8112    -0.0802 0.06 0.38 0.06 0.22 0.22 0.02 0.04
#&gt; TCGA.DC.4749.01     5  0.6052     0.0000 0.06 0.02 0.00 0.40 0.46 0.02 0.04
</code></pre>

<script>
$('#tab-node-03-get-classes-6-a').parent().next().next().hide();
$('#tab-node-03-get-classes-6-a').click(function(){
  $('#tab-node-03-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-03-get-classes-7'>
<p><a id='tab-node-03-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7   p8
#&gt; TCGA.AH.6644.01     2  0.0471     0.7646 0.00 0.98 0.00 0.00 0.00 0.00 0.02 0.00
#&gt; TCGA.AH.6903.01     2  0.6034     0.3173 0.00 0.58 0.18 0.06 0.02 0.12 0.04 0.00
#&gt; TCGA.DC.6157.01     5  0.7158    -0.0674 0.10 0.00 0.00 0.20 0.32 0.02 0.04 0.32
#&gt; TCGA.AG.3592.01     2  0.0471     0.7646 0.00 0.98 0.00 0.00 0.00 0.00 0.02 0.00
#&gt; TCGA.DT.5265.01     2  0.0808     0.7612 0.00 0.96 0.04 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.CI.6620.01     2  0.4624    -0.1910 0.00 0.46 0.46 0.00 0.06 0.02 0.00 0.00
#&gt; TCGA.AG.3731.01     2  0.1741     0.7627 0.00 0.92 0.04 0.00 0.02 0.00 0.02 0.00
#&gt; TCGA.G5.6233.01     2  0.0000     0.7641 0.00 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6465.01     6  0.5497     0.1985 0.06 0.00 0.30 0.08 0.02 0.54 0.00 0.00
#&gt; TCGA.DY.A1H8.01     3  0.6670     0.1368 0.02 0.16 0.50 0.04 0.04 0.22 0.02 0.00
#&gt; TCGA.CL.5917.01     6  0.7382     0.2534 0.14 0.02 0.32 0.08 0.06 0.36 0.02 0.00
#&gt; TCGA.EI.6511.01     2  0.5892     0.3726 0.00 0.58 0.02 0.14 0.18 0.06 0.00 0.02
#&gt; TCGA.CI.6619.01     8  0.2862     0.6017 0.08 0.00 0.00 0.10 0.00 0.00 0.00 0.82
#&gt; TCGA.AF.6136.01     3  0.4137     0.2804 0.00 0.46 0.50 0.00 0.02 0.02 0.00 0.00
#&gt; TCGA.EI.7004.01     2  0.2856     0.6275 0.00 0.78 0.20 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.F5.6702.01     8  0.3601     0.5667 0.06 0.00 0.00 0.16 0.02 0.00 0.00 0.76
#&gt; TCGA.EI.6512.01     2  0.3198     0.4897 0.00 0.72 0.26 0.02 0.00 0.00 0.00 0.00
#&gt; TCGA.DY.A0XA.01     1  0.4190     0.4609 0.72 0.00 0.00 0.02 0.02 0.20 0.02 0.02
#&gt; TCGA.F5.6863.01     3  0.6059    -0.2207 0.04 0.02 0.44 0.06 0.02 0.40 0.02 0.00
#&gt; TCGA.AF.6655.01     4  0.4077     0.2012 0.02 0.00 0.00 0.76 0.04 0.08 0.10 0.00
#&gt; TCGA.CI.6624.01     1  0.7839     0.0536 0.32 0.00 0.16 0.08 0.02 0.30 0.04 0.08
#&gt; TCGA.EI.6883.01     2  0.0808     0.7661 0.00 0.96 0.00 0.00 0.04 0.00 0.00 0.00
#&gt; TCGA.AG.A036.01     2  0.3847     0.6922 0.00 0.78 0.02 0.10 0.06 0.04 0.00 0.00
#&gt; TCGA.CI.6623.01     4  0.4567     0.3240 0.06 0.00 0.06 0.76 0.02 0.02 0.02 0.06
#&gt; TCGA.DC.6156.01     2  0.3904     0.6978 0.04 0.80 0.00 0.04 0.06 0.04 0.00 0.02
#&gt; TCGA.F5.6864.01     1  0.5949     0.2786 0.50 0.00 0.00 0.06 0.02 0.16 0.00 0.26
#&gt; TCGA.DC.6160.01     4  0.8729     0.1474 0.04 0.08 0.08 0.34 0.06 0.08 0.08 0.24
#&gt; TCGA.F5.6814.01     2  0.1408     0.7656 0.00 0.94 0.02 0.00 0.02 0.00 0.02 0.00
#&gt; TCGA.F5.6464.01     3  0.3758     0.3303 0.00 0.14 0.76 0.00 0.04 0.06 0.00 0.00
#&gt; TCGA.AF.A56N.01     3  0.5342     0.2755 0.02 0.34 0.46 0.00 0.00 0.18 0.00 0.00
#&gt; TCGA.EF.5831.01     2  0.1275     0.7615 0.00 0.94 0.00 0.02 0.04 0.00 0.00 0.00
#&gt; TCGA.AG.3732.01     3  0.3395     0.1385 0.00 0.02 0.82 0.02 0.02 0.10 0.02 0.00
#&gt; TCGA.DY.A1DC.01     6  0.8950     0.1690 0.08 0.24 0.14 0.06 0.14 0.26 0.06 0.02
#&gt; TCGA.EI.6885.01     1  0.3941     0.4434 0.76 0.00 0.04 0.00 0.00 0.04 0.02 0.14
#&gt; TCGA.AF.A56L.01     6  0.6882     0.0993 0.20 0.30 0.18 0.00 0.00 0.30 0.00 0.02
#&gt; TCGA.AF.A56K.01     8  0.5960     0.3499 0.18 0.00 0.00 0.14 0.08 0.04 0.00 0.56
#&gt; TCGA.AG.A01Y.01     1  0.5352     0.3628 0.64 0.00 0.04 0.00 0.12 0.06 0.00 0.14
#&gt; TCGA.AF.2687.01     8  0.3385     0.5147 0.16 0.00 0.00 0.00 0.08 0.00 0.00 0.76
#&gt; TCGA.AH.6643.01     2  0.4401     0.6891 0.00 0.76 0.04 0.04 0.08 0.02 0.06 0.00
#&gt; TCGA.DC.6155.01     3  0.5859     0.1660 0.02 0.14 0.56 0.02 0.04 0.22 0.00 0.00
#&gt; TCGA.CL.4957.01     6  0.6059     0.2212 0.06 0.02 0.40 0.02 0.04 0.44 0.02 0.00
#&gt; TCGA.F5.6571.01     3  0.3862     0.3537 0.00 0.36 0.60 0.00 0.00 0.04 0.00 0.00
#&gt; TCGA.DC.6682.01     2  0.1275     0.7597 0.00 0.94 0.04 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.EI.6509.01     7  0.1607     0.0000 0.00 0.00 0.00 0.04 0.00 0.00 0.92 0.04
#&gt; TCGA.CI.6622.01     2  0.1741     0.7574 0.00 0.92 0.00 0.02 0.04 0.00 0.02 0.00
#&gt; TCGA.EI.7002.01     2  0.8943    -0.2526 0.08 0.30 0.02 0.18 0.14 0.10 0.04 0.14
#&gt; TCGA.DC.4749.01     5  0.8198     0.0313 0.02 0.02 0.04 0.28 0.32 0.14 0.06 0.12
</code></pre>

<script>
$('#tab-node-03-get-classes-7-a').parent().next().next().hide();
$('#tab-node-03-get-classes-7-a').click(function(){
  $('#tab-node-03-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-03-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-03-consensus-heatmap'>
<ul>
<li><a href='#tab-node-03-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-03-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-03-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-03-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-03-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-03-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-03-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-03-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-03-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-03-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-03-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-03-membership-heatmap'>
<ul>
<li><a href='#tab-node-03-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-03-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-03-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-03-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-03-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-03-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-03-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-1-1.png" alt="plot of chunk tab-node-03-membership-heatmap-1"/></p>

</div>
<div id='tab-node-03-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-2-1.png" alt="plot of chunk tab-node-03-membership-heatmap-2"/></p>

</div>
<div id='tab-node-03-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-3-1.png" alt="plot of chunk tab-node-03-membership-heatmap-3"/></p>

</div>
<div id='tab-node-03-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-4-1.png" alt="plot of chunk tab-node-03-membership-heatmap-4"/></p>

</div>
<div id='tab-node-03-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-5-1.png" alt="plot of chunk tab-node-03-membership-heatmap-5"/></p>

</div>
<div id='tab-node-03-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-6-1.png" alt="plot of chunk tab-node-03-membership-heatmap-6"/></p>

</div>
<div id='tab-node-03-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-03-membership-heatmap-7-1.png" alt="plot of chunk tab-node-03-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-03-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-03-get-signatures'>
<ul>
<li><a href='#tab-node-03-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-03-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-03-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-03-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-03-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-03-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-03-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-1-1.png" alt="plot of chunk tab-node-03-get-signatures-1"/></p>

</div>
<div id='tab-node-03-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-2-1.png" alt="plot of chunk tab-node-03-get-signatures-2"/></p>

</div>
<div id='tab-node-03-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-3-1.png" alt="plot of chunk tab-node-03-get-signatures-3"/></p>

</div>
<div id='tab-node-03-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-4-1.png" alt="plot of chunk tab-node-03-get-signatures-4"/></p>

</div>
<div id='tab-node-03-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-5-1.png" alt="plot of chunk tab-node-03-get-signatures-5"/></p>

</div>
<div id='tab-node-03-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-6-1.png" alt="plot of chunk tab-node-03-get-signatures-6"/></p>

</div>
<div id='tab-node-03-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-03-get-signatures-7-1.png" alt="plot of chunk tab-node-03-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-03-signature_compare](figure_cola/node-03-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-03-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-03-dimension-reduction'>
<ul>
<li><a href='#tab-node-03-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-03-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-03-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-03-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-03-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-03-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-03-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-03-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-1-1.png" alt="plot of chunk tab-node-03-dimension-reduction-1"/></p>

</div>
<div id='tab-node-03-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-2-1.png" alt="plot of chunk tab-node-03-dimension-reduction-2"/></p>

</div>
<div id='tab-node-03-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-3-1.png" alt="plot of chunk tab-node-03-dimension-reduction-3"/></p>

</div>
<div id='tab-node-03-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-4-1.png" alt="plot of chunk tab-node-03-dimension-reduction-4"/></p>

</div>
<div id='tab-node-03-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-5-1.png" alt="plot of chunk tab-node-03-dimension-reduction-5"/></p>

</div>
<div id='tab-node-03-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-6-1.png" alt="plot of chunk tab-node-03-dimension-reduction-6"/></p>

</div>
<div id='tab-node-03-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-03-dimension-reduction-7-1.png" alt="plot of chunk tab-node-03-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-03-collect-classes](figure_cola/node-03-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node031


Parent node: [Node03](#Node03).
Child nodes: 
                Node0111-leaf
        ,
                Node0112-leaf
        ,
                Node0113-leaf
        ,
                Node0311-leaf
        ,
                Node0312-leaf
        ,
                Node0321-leaf
        ,
                [Node0322](#Node0322)
        ,
                Node0323-leaf
        ,
                Node0324-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["031"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 15 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'kmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 2.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-031-collect-plots](figure_cola/node-031-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-031-select-partition-number](figure_cola/node-031-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.5148 0.486   0.486
#> 3 3 0.686           0.825       0.903         0.3139 0.752   0.519
#> 4 4 0.790           0.936       0.949         0.1249 0.895   0.667
#> 5 5 0.819           0.790       0.875         0.0759 1.000   1.000
#> 6 6 0.771           0.622       0.807         0.0449 0.886   0.538
#> 7 7 0.771           0.723       0.887         0.0281 0.962   0.750
#> 8 8 0.838           0.632       0.860         0.0280 1.000   1.000
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 2
```


Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-031-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-031-get-classes'>
<ul>
<li><a href='#tab-node-031-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-031-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-031-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-031-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-031-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-031-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-031-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-031-get-classes-1'>
<p><a id='tab-node-031-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.DC.6157.01     1       0          1  1  0
#&gt; TCGA.CI.6619.01     2       0          1  0  1
#&gt; TCGA.F5.6702.01     2       0          1  0  1
#&gt; TCGA.DY.A0XA.01     1       0          1  1  0
#&gt; TCGA.AF.6655.01     1       0          1  1  0
#&gt; TCGA.CI.6624.01     2       0          1  0  1
#&gt; TCGA.CI.6623.01     1       0          1  1  0
#&gt; TCGA.F5.6864.01     1       0          1  1  0
#&gt; TCGA.DC.6160.01     1       0          1  1  0
#&gt; TCGA.EI.6885.01     2       0          1  0  1
#&gt; TCGA.AF.A56K.01     1       0          1  1  0
#&gt; TCGA.AG.A01Y.01     2       0          1  0  1
#&gt; TCGA.AF.2687.01     2       0          1  0  1
#&gt; TCGA.EI.6509.01     1       0          1  1  0
#&gt; TCGA.DC.4749.01     1       0          1  1  0
</code></pre>

<script>
$('#tab-node-031-get-classes-1-a').parent().next().next().hide();
$('#tab-node-031-get-classes-1-a').click(function(){
  $('#tab-node-031-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-031-get-classes-2'>
<p><a id='tab-node-031-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.DC.6157.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.CI.6619.01     2   0.296      0.848 0.00 0.90 0.10
#&gt; TCGA.F5.6702.01     3   0.000      0.560 0.00 0.00 1.00
#&gt; TCGA.DY.A0XA.01     3   0.619      0.562 0.42 0.00 0.58
#&gt; TCGA.AF.6655.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.CI.6624.01     2   0.619      0.537 0.00 0.58 0.42
#&gt; TCGA.CI.6623.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.F5.6864.01     3   0.296      0.661 0.10 0.00 0.90
#&gt; TCGA.DC.6160.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.EI.6885.01     2   0.000      0.882 0.00 1.00 0.00
#&gt; TCGA.AF.A56K.01     3   0.619      0.562 0.42 0.00 0.58
#&gt; TCGA.AG.A01Y.01     2   0.000      0.882 0.00 1.00 0.00
#&gt; TCGA.AF.2687.01     2   0.000      0.882 0.00 1.00 0.00
#&gt; TCGA.EI.6509.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.DC.4749.01     1   0.000      1.000 1.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-031-get-classes-2-a').parent().next().next().hide();
$('#tab-node-031-get-classes-2-a').click(function(){
  $('#tab-node-031-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-031-get-classes-3'>
<p><a id='tab-node-031-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.DC.6157.01     1  0.0000      0.993 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6619.01     4  0.3172      0.851 0.00 0.16 0.00 0.84
#&gt; TCGA.F5.6702.01     4  0.0707      0.874 0.00 0.00 0.02 0.98
#&gt; TCGA.DY.A0XA.01     3  0.2345      0.902 0.10 0.00 0.90 0.00
#&gt; TCGA.AF.6655.01     1  0.0000      0.993 1.00 0.00 0.00 0.00
#&gt; TCGA.CI.6624.01     4  0.1637      0.905 0.00 0.06 0.00 0.94
#&gt; TCGA.CI.6623.01     1  0.0000      0.993 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6864.01     3  0.2921      0.836 0.00 0.00 0.86 0.14
#&gt; TCGA.DC.6160.01     1  0.0000      0.993 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6885.01     2  0.0000      0.954 0.00 1.00 0.00 0.00
#&gt; TCGA.AF.A56K.01     3  0.3525      0.909 0.10 0.00 0.86 0.04
#&gt; TCGA.AG.A01Y.01     2  0.2345      0.908 0.00 0.90 0.10 0.00
#&gt; TCGA.AF.2687.01     2  0.0000      0.954 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6509.01     1  0.0707      0.986 0.98 0.00 0.00 0.02
#&gt; TCGA.DC.4749.01     1  0.0707      0.986 0.98 0.00 0.00 0.02
</code></pre>

<script>
$('#tab-node-031-get-classes-3-a').parent().next().next().hide();
$('#tab-node-031-get-classes-3-a').click(function(){
  $('#tab-node-031-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-031-get-classes-4'>
<p><a id='tab-node-031-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.DC.6157.01     1   0.430      0.611 0.52 0.00 0.48 0.00 0.00
#&gt; TCGA.CI.6619.01     4   0.327      0.717 0.00 0.22 0.00 0.78 0.00
#&gt; TCGA.F5.6702.01     4   0.202      0.809 0.00 0.00 0.10 0.90 0.00
#&gt; TCGA.DY.A0XA.01     5   0.000      0.767 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.AF.6655.01     1   0.104      0.816 0.96 0.00 0.04 0.00 0.00
#&gt; TCGA.CI.6624.01     4   0.000      0.835 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.CI.6623.01     1   0.104      0.816 0.96 0.00 0.04 0.00 0.00
#&gt; TCGA.F5.6864.01     5   0.446      0.806 0.00 0.00 0.32 0.02 0.66
#&gt; TCGA.DC.6160.01     1   0.430      0.611 0.52 0.00 0.48 0.00 0.00
#&gt; TCGA.EI.6885.01     2   0.000      0.903 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AF.A56K.01     5   0.368      0.829 0.00 0.00 0.28 0.00 0.72
#&gt; TCGA.AG.A01Y.01     2   0.311      0.807 0.00 0.80 0.20 0.00 0.00
#&gt; TCGA.AF.2687.01     2   0.000      0.903 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.EI.6509.01     1   0.000      0.809 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.4749.01     1   0.000      0.809 1.00 0.00 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-031-get-classes-4-a').parent().next().next().hide();
$('#tab-node-031-get-classes-4-a').click(function(){
  $('#tab-node-031-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-031-get-classes-5'>
<p><a id='tab-node-031-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.DC.6157.01     3  0.5888      0.438 0.22 0.00 0.46 0.00 0.32 0.00
#&gt; TCGA.CI.6619.01     6  0.3076      0.565 0.00 0.24 0.00 0.00 0.00 0.76
#&gt; TCGA.F5.6702.01     6  0.3647      0.461 0.00 0.00 0.00 0.36 0.00 0.64
#&gt; TCGA.DY.A0XA.01     3  0.5876     -0.338 0.00 0.00 0.48 0.26 0.26 0.00
#&gt; TCGA.AF.6655.01     1  0.0547      0.942 0.98 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.CI.6624.01     6  0.0000      0.664 0.00 0.00 0.00 0.00 0.00 1.00
#&gt; TCGA.CI.6623.01     1  0.0547      0.942 0.98 0.00 0.02 0.00 0.00 0.00
#&gt; TCGA.F5.6864.01     5  0.3647      0.545 0.00 0.00 0.00 0.36 0.64 0.00
#&gt; TCGA.DC.6160.01     3  0.5921      0.441 0.24 0.00 0.46 0.00 0.30 0.00
#&gt; TCGA.EI.6885.01     2  0.0000      0.851 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.A56K.01     5  0.0000      0.456 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.A01Y.01     2  0.4067      0.698 0.00 0.70 0.04 0.26 0.00 0.00
#&gt; TCGA.AF.2687.01     2  0.0000      0.851 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.EI.6509.01     1  0.2350      0.875 0.88 0.00 0.02 0.10 0.00 0.00
#&gt; TCGA.DC.4749.01     1  0.0547      0.937 0.98 0.00 0.00 0.02 0.00 0.00
</code></pre>

<script>
$('#tab-node-031-get-classes-5-a').parent().next().next().hide();
$('#tab-node-031-get-classes-5-a').click(function(){
  $('#tab-node-031-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-031-get-classes-6'>
<p><a id='tab-node-031-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6 p7
#&gt; TCGA.DC.6157.01     3   0.189      0.962 0.12 0.00 0.88 0.00 0.00 0.00  0
#&gt; TCGA.CI.6619.01     6   0.435      0.817 0.00 0.10 0.00 0.24 0.00 0.66  0
#&gt; TCGA.F5.6702.01     4   0.167      0.000 0.00 0.00 0.00 0.90 0.10 0.00  0
#&gt; TCGA.DY.A0XA.01     7   0.000      0.000 0.00 0.00 0.00 0.00 0.00 0.00  1
#&gt; TCGA.AF.6655.01     1   0.167      0.864 0.90 0.00 0.10 0.00 0.00 0.00  0
#&gt; TCGA.CI.6624.01     6   0.329      0.805 0.00 0.00 0.00 0.34 0.00 0.66  0
#&gt; TCGA.CI.6623.01     1   0.167      0.864 0.90 0.00 0.10 0.00 0.00 0.00  0
#&gt; TCGA.F5.6864.01     5   0.000      0.758 0.00 0.00 0.00 0.00 1.00 0.00  0
#&gt; TCGA.DC.6160.01     3   0.257      0.962 0.14 0.00 0.84 0.00 0.00 0.02  0
#&gt; TCGA.EI.6885.01     2   0.000      0.868 0.00 1.00 0.00 0.00 0.00 0.00  0
#&gt; TCGA.AF.A56K.01     5   0.337      0.769 0.00 0.00 0.16 0.00 0.78 0.06  0
#&gt; TCGA.AG.A01Y.01     2   0.462      0.716 0.00 0.72 0.10 0.08 0.00 0.10  0
#&gt; TCGA.AF.2687.01     2   0.000      0.868 0.00 1.00 0.00 0.00 0.00 0.00  0
#&gt; TCGA.EI.6509.01     1   0.275      0.743 0.82 0.00 0.00 0.02 0.00 0.16  0
#&gt; TCGA.DC.4749.01     1   0.000      0.854 1.00 0.00 0.00 0.00 0.00 0.00  0
</code></pre>

<script>
$('#tab-node-031-get-classes-6-a').parent().next().next().hide();
$('#tab-node-031-get-classes-6-a').click(function(){
  $('#tab-node-031-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-031-get-classes-7'>
<p><a id='tab-node-031-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6 p7   p8
#&gt; TCGA.DC.6157.01     3  0.2025      0.882 0.10 0.00 0.88 0.00 0.00 0.00  0 0.02
#&gt; TCGA.CI.6619.01     6  0.1947      0.782 0.00 0.14 0.00 0.00 0.00 0.86  0 0.00
#&gt; TCGA.F5.6702.01     4  0.0808      0.000 0.00 0.00 0.00 0.96 0.00 0.04  0 0.00
#&gt; TCGA.DY.A0XA.01     7  0.0000      0.000 0.00 0.00 0.00 0.00 0.00 0.00  1 0.00
#&gt; TCGA.AF.6655.01     8  0.4302      0.765 0.36 0.00 0.08 0.00 0.00 0.00  0 0.56
#&gt; TCGA.CI.6624.01     6  0.2404      0.765 0.02 0.00 0.00 0.14 0.00 0.84  0 0.00
#&gt; TCGA.CI.6623.01     8  0.4302      0.765 0.36 0.00 0.08 0.00 0.00 0.00  0 0.56
#&gt; TCGA.F5.6864.01     5  0.3675      0.634 0.30 0.00 0.00 0.04 0.66 0.00  0 0.00
#&gt; TCGA.DC.6160.01     3  0.0471      0.881 0.00 0.00 0.98 0.00 0.00 0.00  0 0.02
#&gt; TCGA.EI.6885.01     2  0.0941      0.765 0.00 0.96 0.02 0.00 0.02 0.00  0 0.00
#&gt; TCGA.AF.A56K.01     5  0.1341      0.643 0.00 0.00 0.08 0.00 0.92 0.00  0 0.00
#&gt; TCGA.AG.A01Y.01     2  0.4677      0.510 0.32 0.54 0.00 0.00 0.00 0.14  0 0.00
#&gt; TCGA.AF.2687.01     2  0.0000      0.765 0.00 1.00 0.00 0.00 0.00 0.00  0 0.00
#&gt; TCGA.EI.6509.01     8  0.0941      0.571 0.00 0.00 0.00 0.02 0.02 0.00  0 0.96
#&gt; TCGA.DC.4749.01     8  0.2981      0.744 0.22 0.00 0.00 0.02 0.00 0.00  0 0.76
</code></pre>

<script>
$('#tab-node-031-get-classes-7-a').parent().next().next().hide();
$('#tab-node-031-get-classes-7-a').click(function(){
  $('#tab-node-031-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-031-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-031-consensus-heatmap'>
<ul>
<li><a href='#tab-node-031-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-031-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-031-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-031-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-031-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-031-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-031-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-031-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-031-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-031-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-031-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-031-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-031-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-031-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-031-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-031-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-031-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-031-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-031-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-031-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-031-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-031-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-031-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-031-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-031-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-031-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-031-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-031-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-031-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-031-membership-heatmap'>
<ul>
<li><a href='#tab-node-031-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-031-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-031-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-031-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-031-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-031-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-031-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-031-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-031-membership-heatmap-1-1.png" alt="plot of chunk tab-node-031-membership-heatmap-1"/></p>

</div>
<div id='tab-node-031-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-031-membership-heatmap-2-1.png" alt="plot of chunk tab-node-031-membership-heatmap-2"/></p>

</div>
<div id='tab-node-031-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-031-membership-heatmap-3-1.png" alt="plot of chunk tab-node-031-membership-heatmap-3"/></p>

</div>
<div id='tab-node-031-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-031-membership-heatmap-4-1.png" alt="plot of chunk tab-node-031-membership-heatmap-4"/></p>

</div>
<div id='tab-node-031-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-031-membership-heatmap-5-1.png" alt="plot of chunk tab-node-031-membership-heatmap-5"/></p>

</div>
<div id='tab-node-031-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-031-membership-heatmap-6-1.png" alt="plot of chunk tab-node-031-membership-heatmap-6"/></p>

</div>
<div id='tab-node-031-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-031-membership-heatmap-7-1.png" alt="plot of chunk tab-node-031-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-031-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-031-get-signatures'>
<ul>
<li><a href='#tab-node-031-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-031-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-031-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-031-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-031-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-031-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-031-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-031-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-031-get-signatures-1-1.png" alt="plot of chunk tab-node-031-get-signatures-1"/></p>

</div>
<div id='tab-node-031-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-031-get-signatures-2-1.png" alt="plot of chunk tab-node-031-get-signatures-2"/></p>

</div>
<div id='tab-node-031-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-031-get-signatures-3-1.png" alt="plot of chunk tab-node-031-get-signatures-3"/></p>

</div>
<div id='tab-node-031-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-031-get-signatures-4-1.png" alt="plot of chunk tab-node-031-get-signatures-4"/></p>

</div>
<div id='tab-node-031-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-031-get-signatures-5-1.png" alt="plot of chunk tab-node-031-get-signatures-5"/></p>

</div>
<div id='tab-node-031-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-031-get-signatures-6-1.png" alt="plot of chunk tab-node-031-get-signatures-6"/></p>

</div>
<div id='tab-node-031-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-031-get-signatures-7-1.png" alt="plot of chunk tab-node-031-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-031-signature_compare](figure_cola/node-031-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-031-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-031-dimension-reduction'>
<ul>
<li><a href='#tab-node-031-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-031-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-031-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-031-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-031-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-031-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-031-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-031-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-031-dimension-reduction-1-1.png" alt="plot of chunk tab-node-031-dimension-reduction-1"/></p>

</div>
<div id='tab-node-031-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-031-dimension-reduction-2-1.png" alt="plot of chunk tab-node-031-dimension-reduction-2"/></p>

</div>
<div id='tab-node-031-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-031-dimension-reduction-3-1.png" alt="plot of chunk tab-node-031-dimension-reduction-3"/></p>

</div>
<div id='tab-node-031-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-031-dimension-reduction-4-1.png" alt="plot of chunk tab-node-031-dimension-reduction-4"/></p>

</div>
<div id='tab-node-031-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-031-dimension-reduction-5-1.png" alt="plot of chunk tab-node-031-dimension-reduction-5"/></p>

</div>
<div id='tab-node-031-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-031-dimension-reduction-6-1.png" alt="plot of chunk tab-node-031-dimension-reduction-6"/></p>

</div>
<div id='tab-node-031-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-031-dimension-reduction-7-1.png" alt="plot of chunk tab-node-031-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-031-collect-classes](figure_cola/node-031-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node032


Parent node: [Node03](#Node03).
Child nodes: 
                Node0111-leaf
        ,
                Node0112-leaf
        ,
                Node0113-leaf
        ,
                Node0311-leaf
        ,
                Node0312-leaf
        ,
                Node0321-leaf
        ,
                [Node0322](#Node0322)
        ,
                Node0323-leaf
        ,
                Node0324-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["032"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 32 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 4.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-032-collect-plots](figure_cola/node-032-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-032-select-partition-number](figure_cola/node-032-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.5166 0.484   0.484
#> 3 3 1.000           0.999       0.999         0.2494 0.871   0.733
#> 4 4 0.936           0.978       0.966         0.0656 0.944   0.841
#> 5 5 1.000           0.958       0.993         0.0424 0.986   0.953
#> 6 6 0.989           0.922       0.983         0.0272 0.980   0.929
#> 7 7 0.968           0.866       0.950         0.0111 1.000   1.000
#> 8 8 0.931           0.782       0.946         0.0143 0.990   0.962
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 4
#> attr(,"optional")
#> [1] 2 3
```

There is also optional best $k$ = 2 3 that is worth to check.

Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-032-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-032-get-classes'>
<ul>
<li><a href='#tab-node-032-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-032-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-032-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-032-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-032-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-032-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-032-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-032-get-classes-1'>
<p><a id='tab-node-032-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.AH.6644.01     1       0          1  1  0
#&gt; TCGA.AH.6903.01     1       0          1  1  0
#&gt; TCGA.AG.3592.01     1       0          1  1  0
#&gt; TCGA.DT.5265.01     1       0          1  1  0
#&gt; TCGA.CI.6620.01     2       0          1  0  1
#&gt; TCGA.AG.3731.01     1       0          1  1  0
#&gt; TCGA.G5.6233.01     1       0          1  1  0
#&gt; TCGA.F5.6465.01     2       0          1  0  1
#&gt; TCGA.DY.A1H8.01     2       0          1  0  1
#&gt; TCGA.CL.5917.01     2       0          1  0  1
#&gt; TCGA.EI.6511.01     1       0          1  1  0
#&gt; TCGA.AF.6136.01     2       0          1  0  1
#&gt; TCGA.EI.7004.01     2       0          1  0  1
#&gt; TCGA.EI.6512.01     2       0          1  0  1
#&gt; TCGA.F5.6863.01     2       0          1  0  1
#&gt; TCGA.EI.6883.01     1       0          1  1  0
#&gt; TCGA.AG.A036.01     1       0          1  1  0
#&gt; TCGA.DC.6156.01     1       0          1  1  0
#&gt; TCGA.F5.6814.01     1       0          1  1  0
#&gt; TCGA.F5.6464.01     2       0          1  0  1
#&gt; TCGA.AF.A56N.01     2       0          1  0  1
#&gt; TCGA.EF.5831.01     1       0          1  1  0
#&gt; TCGA.AG.3732.01     2       0          1  0  1
#&gt; TCGA.DY.A1DC.01     2       0          1  0  1
#&gt; TCGA.AF.A56L.01     2       0          1  0  1
#&gt; TCGA.AH.6643.01     1       0          1  1  0
#&gt; TCGA.DC.6155.01     2       0          1  0  1
#&gt; TCGA.CL.4957.01     2       0          1  0  1
#&gt; TCGA.F5.6571.01     2       0          1  0  1
#&gt; TCGA.DC.6682.01     1       0          1  1  0
#&gt; TCGA.CI.6622.01     1       0          1  1  0
#&gt; TCGA.EI.7002.01     1       0          1  1  0
</code></pre>

<script>
$('#tab-node-032-get-classes-1-a').parent().next().next().hide();
$('#tab-node-032-get-classes-1-a').click(function(){
  $('#tab-node-032-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-032-get-classes-2'>
<p><a id='tab-node-032-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2   p3
#&gt; TCGA.AH.6644.01     1  0.0892      0.980 0.98  0 0.02
#&gt; TCGA.AH.6903.01     1  0.0000      0.997 1.00  0 0.00
#&gt; TCGA.AG.3592.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.DT.5265.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.CI.6620.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.AG.3731.01     1  0.0000      0.997 1.00  0 0.00
#&gt; TCGA.G5.6233.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.F5.6465.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.DY.A1H8.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.CL.5917.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.EI.6511.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.AF.6136.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.EI.7004.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.EI.6512.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.F5.6863.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.EI.6883.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.AG.A036.01     1  0.0000      0.997 1.00  0 0.00
#&gt; TCGA.DC.6156.01     1  0.0000      0.997 1.00  0 0.00
#&gt; TCGA.F5.6814.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.F5.6464.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.AF.A56N.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.EF.5831.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.AG.3732.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.DY.A1DC.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.AF.A56L.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.AH.6643.01     1  0.0000      0.997 1.00  0 0.00
#&gt; TCGA.DC.6155.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.CL.4957.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.F5.6571.01     2  0.0000      1.000 0.00  1 0.00
#&gt; TCGA.DC.6682.01     3  0.0000      1.000 0.00  0 1.00
#&gt; TCGA.CI.6622.01     1  0.0000      0.997 1.00  0 0.00
#&gt; TCGA.EI.7002.01     1  0.0000      0.997 1.00  0 0.00
</code></pre>

<script>
$('#tab-node-032-get-classes-2-a').parent().next().next().hide();
$('#tab-node-032-get-classes-2-a').click(function(){
  $('#tab-node-032-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-032-get-classes-3'>
<p><a id='tab-node-032-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.AH.6644.01     1  0.0707      0.936 0.98 0.00 0.02 0.00
#&gt; TCGA.AH.6903.01     1  0.0707      0.949 0.98 0.00 0.00 0.02
#&gt; TCGA.AG.3592.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.DT.5265.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.CI.6620.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.AG.3731.01     1  0.0000      0.949 1.00 0.00 0.00 0.00
#&gt; TCGA.G5.6233.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.F5.6465.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.DY.A1H8.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.CL.5917.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6511.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.AF.6136.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.7004.01     4  0.4624      1.000 0.00 0.34 0.00 0.66
#&gt; TCGA.EI.6512.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6863.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.EI.6883.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.A036.01     1  0.4624      0.672 0.66 0.00 0.00 0.34
#&gt; TCGA.DC.6156.01     1  0.0000      0.949 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6814.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.F5.6464.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.AF.A56N.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.EF.5831.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.3732.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.DY.A1DC.01     4  0.4624      1.000 0.00 0.34 0.00 0.66
#&gt; TCGA.AF.A56L.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.AH.6643.01     1  0.0000      0.949 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.CL.4957.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6571.01     2  0.0000      1.000 0.00 1.00 0.00 0.00
#&gt; TCGA.DC.6682.01     3  0.0000      1.000 0.00 0.00 1.00 0.00
#&gt; TCGA.CI.6622.01     1  0.0707      0.949 0.98 0.00 0.00 0.02
#&gt; TCGA.EI.7002.01     1  0.0707      0.949 0.98 0.00 0.00 0.02
</code></pre>

<script>
$('#tab-node-032-get-classes-3-a').parent().next().next().hide();
$('#tab-node-032-get-classes-3-a').click(function(){
  $('#tab-node-032-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-032-get-classes-4'>
<p><a id='tab-node-032-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1 p2   p3 p4   p5
#&gt; TCGA.AH.6644.01     1  0.0609      0.956 0.98  0 0.02  0 0.00
#&gt; TCGA.AH.6903.01     1  0.1410      0.951 0.94  0 0.00  0 0.06
#&gt; TCGA.AG.3592.01     3  0.0000      0.996 0.00  0 1.00  0 0.00
#&gt; TCGA.DT.5265.01     3  0.0000      0.996 0.00  0 1.00  0 0.00
#&gt; TCGA.CI.6620.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.AG.3731.01     1  0.0000      0.970 1.00  0 0.00  0 0.00
#&gt; TCGA.G5.6233.01     3  0.0000      0.996 0.00  0 1.00  0 0.00
#&gt; TCGA.F5.6465.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.DY.A1H8.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.CL.5917.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.EI.6511.01     3  0.0609      0.974 0.02  0 0.98  0 0.00
#&gt; TCGA.AF.6136.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.EI.7004.01     4  0.0000      1.000 0.00  0 0.00  1 0.00
#&gt; TCGA.EI.6512.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.F5.6863.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.EI.6883.01     3  0.0000      0.996 0.00  0 1.00  0 0.00
#&gt; TCGA.AG.A036.01     5  0.0609      0.000 0.02  0 0.00  0 0.98
#&gt; TCGA.DC.6156.01     1  0.0000      0.970 1.00  0 0.00  0 0.00
#&gt; TCGA.F5.6814.01     3  0.0000      0.996 0.00  0 1.00  0 0.00
#&gt; TCGA.F5.6464.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.AF.A56N.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.EF.5831.01     3  0.0000      0.996 0.00  0 1.00  0 0.00
#&gt; TCGA.AG.3732.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.DY.A1DC.01     4  0.0000      1.000 0.00  0 0.00  1 0.00
#&gt; TCGA.AF.A56L.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.AH.6643.01     1  0.0000      0.970 1.00  0 0.00  0 0.00
#&gt; TCGA.DC.6155.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.CL.4957.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.F5.6571.01     2  0.0000      1.000 0.00  1 0.00  0 0.00
#&gt; TCGA.DC.6682.01     3  0.0000      0.996 0.00  0 1.00  0 0.00
#&gt; TCGA.CI.6622.01     1  0.0609      0.967 0.98  0 0.00  0 0.02
#&gt; TCGA.EI.7002.01     1  0.1732      0.937 0.92  0 0.00  0 0.08
</code></pre>

<script>
$('#tab-node-032-get-classes-4-a').parent().next().next().hide();
$('#tab-node-032-get-classes-4-a').click(function(){
  $('#tab-node-032-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-032-get-classes-5'>
<p><a id='tab-node-032-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4 p5   p6
#&gt; TCGA.AH.6644.01     1  0.0000      0.902 1.00 0.00 0.00 0.00  0 0.00
#&gt; TCGA.AH.6903.01     6  0.2631      0.758 0.18 0.00 0.00 0.00  0 0.82
#&gt; TCGA.AG.3592.01     3  0.0000      0.997 0.00 0.00 1.00 0.00  0 0.00
#&gt; TCGA.DT.5265.01     3  0.0000      0.997 0.00 0.00 1.00 0.00  0 0.00
#&gt; TCGA.CI.6620.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.AG.3731.01     1  0.0547      0.889 0.98 0.00 0.00 0.00  0 0.02
#&gt; TCGA.G5.6233.01     3  0.0000      0.997 0.00 0.00 1.00 0.00  0 0.00
#&gt; TCGA.F5.6465.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.DY.A1H8.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.CL.5917.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.EI.6511.01     3  0.0547      0.978 0.00 0.00 0.98 0.00  0 0.02
#&gt; TCGA.AF.6136.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.EI.7004.01     4  0.0000      1.000 0.00 0.00 0.00 1.00  0 0.00
#&gt; TCGA.EI.6512.01     2  0.0547      0.979 0.00 0.98 0.00 0.02  0 0.00
#&gt; TCGA.F5.6863.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.EI.6883.01     3  0.0000      0.997 0.00 0.00 1.00 0.00  0 0.00
#&gt; TCGA.AG.A036.01     5  0.0000      0.000 0.00 0.00 0.00 0.00  1 0.00
#&gt; TCGA.DC.6156.01     1  0.0000      0.902 1.00 0.00 0.00 0.00  0 0.00
#&gt; TCGA.F5.6814.01     3  0.0000      0.997 0.00 0.00 1.00 0.00  0 0.00
#&gt; TCGA.F5.6464.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.AF.A56N.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.EF.5831.01     3  0.0000      0.997 0.00 0.00 1.00 0.00  0 0.00
#&gt; TCGA.AG.3732.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.DY.A1DC.01     4  0.0000      1.000 0.00 0.00 0.00 1.00  0 0.00
#&gt; TCGA.AF.A56L.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.AH.6643.01     1  0.0000      0.902 1.00 0.00 0.00 0.00  0 0.00
#&gt; TCGA.DC.6155.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.CL.4957.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.F5.6571.01     2  0.0000      0.998 0.00 1.00 0.00 0.00  0 0.00
#&gt; TCGA.DC.6682.01     3  0.0000      0.997 0.00 0.00 1.00 0.00  0 0.00
#&gt; TCGA.CI.6622.01     1  0.3409      0.483 0.70 0.00 0.00 0.00  0 0.30
#&gt; TCGA.EI.7002.01     6  0.0547      0.747 0.02 0.00 0.00 0.00  0 0.98
</code></pre>

<script>
$('#tab-node-032-get-classes-5-a').parent().next().next().hide();
$('#tab-node-032-get-classes-5-a').click(function(){
  $('#tab-node-032-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-032-get-classes-6'>
<p><a id='tab-node-032-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3 p4   p5   p6   p7
#&gt; TCGA.AH.6644.01     1  0.0504      0.759 0.98 0.02 0.00  0 0.00 0.00 0.00
#&gt; TCGA.AH.6903.01     6  0.4978      0.524 0.12 0.00 0.00  0 0.38 0.50 0.00
#&gt; TCGA.AG.3592.01     3  0.0000      0.981 0.00 0.00 1.00  0 0.00 0.00 0.00
#&gt; TCGA.DT.5265.01     3  0.0000      0.981 0.00 0.00 1.00  0 0.00 0.00 0.00
#&gt; TCGA.CI.6620.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.AG.3731.01     1  0.3546      0.464 0.54 0.46 0.00  0 0.00 0.00 0.00
#&gt; TCGA.G5.6233.01     3  0.0000      0.981 0.00 0.00 1.00  0 0.00 0.00 0.00
#&gt; TCGA.F5.6465.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.DY.A1H8.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.CL.5917.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.EI.6511.01     3  0.2163      0.882 0.00 0.10 0.88  0 0.00 0.02 0.00
#&gt; TCGA.AF.6136.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.EI.7004.01     4  0.0000      1.000 0.00 0.00 0.00  1 0.00 0.00 0.00
#&gt; TCGA.EI.6512.01     7  0.1166      0.939 0.00 0.06 0.00  0 0.00 0.00 0.94
#&gt; TCGA.F5.6863.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.EI.6883.01     3  0.0000      0.981 0.00 0.00 1.00  0 0.00 0.00 0.00
#&gt; TCGA.AG.A036.01     5  0.3413      0.000 0.00 0.38 0.00  0 0.62 0.00 0.00
#&gt; TCGA.DC.6156.01     1  0.0000      0.759 1.00 0.00 0.00  0 0.00 0.00 0.00
#&gt; TCGA.F5.6814.01     3  0.0000      0.981 0.00 0.00 1.00  0 0.00 0.00 0.00
#&gt; TCGA.F5.6464.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.AF.A56N.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.EF.5831.01     3  0.0504      0.970 0.00 0.02 0.98  0 0.00 0.00 0.00
#&gt; TCGA.AG.3732.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.DY.A1DC.01     4  0.0000      1.000 0.00 0.00 0.00  1 0.00 0.00 0.00
#&gt; TCGA.AF.A56L.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.AH.6643.01     1  0.0504      0.755 0.98 0.00 0.00  0 0.02 0.00 0.00
#&gt; TCGA.DC.6155.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.CL.4957.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.F5.6571.01     7  0.0000      0.996 0.00 0.00 0.00  0 0.00 0.00 1.00
#&gt; TCGA.DC.6682.01     3  0.0000      0.981 0.00 0.00 1.00  0 0.00 0.00 0.00
#&gt; TCGA.CI.6622.01     1  0.5215      0.335 0.58 0.06 0.00  0 0.06 0.30 0.00
#&gt; TCGA.EI.7002.01     6  0.0000      0.509 0.00 0.00 0.00  0 0.00 1.00 0.00
</code></pre>

<script>
$('#tab-node-032-get-classes-6-a').parent().next().next().hide();
$('#tab-node-032-get-classes-6-a').click(function(){
  $('#tab-node-032-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-032-get-classes-7'>
<p><a id='tab-node-032-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4 p5   p6  p7   p8
#&gt; TCGA.AH.6644.01     1   0.240      0.601 0.84 0.14 0.00 0.00  0 0.02 0.0 0.00
#&gt; TCGA.AH.6903.01     6   0.343      0.000 0.06 0.00 0.00 0.00  0 0.74 0.0 0.20
#&gt; TCGA.AG.3592.01     3   0.000      0.961 0.00 0.00 1.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.DT.5265.01     3   0.000      0.961 0.00 0.00 1.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.CI.6620.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.AG.3731.01     2   0.241      0.000 0.20 0.80 0.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.G5.6233.01     3   0.000      0.961 0.00 0.00 1.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.F5.6465.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.DY.A1H8.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.CL.5917.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.EI.6511.01     3   0.355      0.661 0.00 0.06 0.72 0.00  0 0.22 0.0 0.00
#&gt; TCGA.AF.6136.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.EI.7004.01     4   0.000      1.000 0.00 0.00 0.00 1.00  0 0.00 0.0 0.00
#&gt; TCGA.EI.6512.01     7   0.302      0.767 0.00 0.16 0.00 0.02  0 0.02 0.8 0.00
#&gt; TCGA.F5.6863.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.EI.6883.01     3   0.000      0.961 0.00 0.00 1.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.AG.A036.01     5   0.000      0.000 0.00 0.00 0.00 0.00  1 0.00 0.0 0.00
#&gt; TCGA.DC.6156.01     1   0.000      0.661 1.00 0.00 0.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.F5.6814.01     3   0.000      0.961 0.00 0.00 1.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.F5.6464.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.AF.A56N.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.EF.5831.01     3   0.000      0.961 0.00 0.00 1.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.AG.3732.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.DY.A1DC.01     4   0.000      1.000 0.00 0.00 0.00 1.00  0 0.00 0.0 0.00
#&gt; TCGA.AF.A56L.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.AH.6643.01     1   0.156      0.646 0.90 0.00 0.00 0.00  0 0.10 0.0 0.00
#&gt; TCGA.DC.6155.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.CL.4957.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.F5.6571.01     7   0.000      0.985 0.00 0.00 0.00 0.00  0 0.00 1.0 0.00
#&gt; TCGA.DC.6682.01     3   0.000      0.961 0.00 0.00 1.00 0.00  0 0.00 0.0 0.00
#&gt; TCGA.CI.6622.01     1   0.616      0.150 0.46 0.20 0.00 0.00  0 0.18 0.0 0.16
#&gt; TCGA.EI.7002.01     8   0.000      0.000 0.00 0.00 0.00 0.00  0 0.00 0.0 1.00
</code></pre>

<script>
$('#tab-node-032-get-classes-7-a').parent().next().next().hide();
$('#tab-node-032-get-classes-7-a').click(function(){
  $('#tab-node-032-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-032-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-032-consensus-heatmap'>
<ul>
<li><a href='#tab-node-032-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-032-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-032-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-032-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-032-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-032-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-032-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-032-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-032-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-032-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-032-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-032-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-032-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-032-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-032-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-032-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-032-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-032-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-032-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-032-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-032-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-032-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-032-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-032-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-032-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-032-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-032-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-032-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-032-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-032-membership-heatmap'>
<ul>
<li><a href='#tab-node-032-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-032-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-032-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-032-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-032-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-032-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-032-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-032-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-032-membership-heatmap-1-1.png" alt="plot of chunk tab-node-032-membership-heatmap-1"/></p>

</div>
<div id='tab-node-032-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-032-membership-heatmap-2-1.png" alt="plot of chunk tab-node-032-membership-heatmap-2"/></p>

</div>
<div id='tab-node-032-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-032-membership-heatmap-3-1.png" alt="plot of chunk tab-node-032-membership-heatmap-3"/></p>

</div>
<div id='tab-node-032-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-032-membership-heatmap-4-1.png" alt="plot of chunk tab-node-032-membership-heatmap-4"/></p>

</div>
<div id='tab-node-032-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-032-membership-heatmap-5-1.png" alt="plot of chunk tab-node-032-membership-heatmap-5"/></p>

</div>
<div id='tab-node-032-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-032-membership-heatmap-6-1.png" alt="plot of chunk tab-node-032-membership-heatmap-6"/></p>

</div>
<div id='tab-node-032-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-032-membership-heatmap-7-1.png" alt="plot of chunk tab-node-032-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-032-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-032-get-signatures'>
<ul>
<li><a href='#tab-node-032-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-032-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-032-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-032-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-032-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-032-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-032-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-032-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-032-get-signatures-1-1.png" alt="plot of chunk tab-node-032-get-signatures-1"/></p>

</div>
<div id='tab-node-032-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-032-get-signatures-2-1.png" alt="plot of chunk tab-node-032-get-signatures-2"/></p>

</div>
<div id='tab-node-032-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-032-get-signatures-3-1.png" alt="plot of chunk tab-node-032-get-signatures-3"/></p>

</div>
<div id='tab-node-032-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-032-get-signatures-4-1.png" alt="plot of chunk tab-node-032-get-signatures-4"/></p>

</div>
<div id='tab-node-032-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-032-get-signatures-5-1.png" alt="plot of chunk tab-node-032-get-signatures-5"/></p>

</div>
<div id='tab-node-032-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-032-get-signatures-6-1.png" alt="plot of chunk tab-node-032-get-signatures-6"/></p>

</div>
<div id='tab-node-032-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-032-get-signatures-7-1.png" alt="plot of chunk tab-node-032-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-032-signature_compare](figure_cola/node-032-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-032-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-032-dimension-reduction'>
<ul>
<li><a href='#tab-node-032-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-032-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-032-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-032-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-032-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-032-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-032-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-032-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-032-dimension-reduction-1-1.png" alt="plot of chunk tab-node-032-dimension-reduction-1"/></p>

</div>
<div id='tab-node-032-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-032-dimension-reduction-2-1.png" alt="plot of chunk tab-node-032-dimension-reduction-2"/></p>

</div>
<div id='tab-node-032-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-032-dimension-reduction-3-1.png" alt="plot of chunk tab-node-032-dimension-reduction-3"/></p>

</div>
<div id='tab-node-032-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-032-dimension-reduction-4-1.png" alt="plot of chunk tab-node-032-dimension-reduction-4"/></p>

</div>
<div id='tab-node-032-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-032-dimension-reduction-5-1.png" alt="plot of chunk tab-node-032-dimension-reduction-5"/></p>

</div>
<div id='tab-node-032-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-032-dimension-reduction-6-1.png" alt="plot of chunk tab-node-032-dimension-reduction-6"/></p>

</div>
<div id='tab-node-032-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-032-dimension-reduction-7-1.png" alt="plot of chunk tab-node-032-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-032-collect-classes](figure_cola/node-032-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

---------------------------------------------------




### Node0322


Parent node: [Node032](#Node032).
Child nodes: 
                Node03221-leaf
        ,
                Node03222-leaf
        .







The object with results only for a single top-value method and a single partitioning method 
can be extracted as:

```r
res = res_rh["0322"]
```

A summary of `res` and all the functions that can be applied to it:

```r
res
```

```
#> A 'ConsensusPartition' object with k = 2, 3, 4, 5, 6, 7, 8.
#>   On a matrix with 30000 rows and 14 columns.
#>   Top rows (1000) are extracted by 'ATC' method.
#>   Subgroups are detected by 'skmeans' method.
#>   Performed in total 350 partitions by row resampling.
#>   Best k for subgroups seems to be 2.
#> 
#> Following methods can be applied to this 'ConsensusPartition' object:
#>  [1] "cola_report"             "collect_classes"         "collect_plots"          
#>  [4] "collect_stats"           "colnames"                "compare_partitions"     
#>  [7] "compare_signatures"      "consensus_heatmap"       "dimension_reduction"    
#> [10] "functional_enrichment"   "get_anno_col"            "get_anno"               
#> [13] "get_classes"             "get_consensus"           "get_matrix"             
#> [16] "get_membership"          "get_param"               "get_signatures"         
#> [19] "get_stats"               "is_best_k"               "is_stable_k"            
#> [22] "membership_heatmap"      "ncol"                    "nrow"                   
#> [25] "plot_ecdf"               "predict_classes"         "rownames"               
#> [28] "select_partition_number" "show"                    "suggest_best_k"         
#> [31] "test_to_known_factors"   "top_rows_heatmap"
```

`collect_plots()` function collects all the plots made from `res` for all `k` (number of subgroups)
into one single page to provide an easy and fast comparison between different `k`.

```r
collect_plots(res)
```

![plot of chunk node-0322-collect-plots](figure_cola/node-0322-collect-plots-1.png)

The plots are:

- The first row: a plot of the eCDF (empirical cumulative distribution
  function) curves of the consensus matrix for each `k` and the heatmap of
  predicted classes for each `k`.
- The second row: heatmaps of the consensus matrix for each `k`.
- The third row: heatmaps of the membership matrix for each `k`.
- The fouth row: heatmaps of the signatures for each `k`.

All the plots in panels can be made by individual functions and they are
plotted later in this section.

`select_partition_number()` produces several plots showing different
statistics for choosing "optimized" `k`. There are following statistics:

- eCDF curves of the consensus matrix for each `k`;
- 1-PAC. [The PAC score](https://en.wikipedia.org/wiki/Consensus_clustering#Over-interpretation_potential_of_consensus_clustering)
  measures the proportion of the ambiguous subgrouping.
- Mean silhouette score.
- Concordance. The mean probability of fiting the consensus subgroup labels in all
  partitions.
- Area increased. Denote $A_k$ as the area under the eCDF curve for current
  `k`, the area increased is defined as $A_k - A_{k-1}$.
- Rand index. The percent of pairs of samples that are both in a same cluster
  or both are not in a same cluster in the partition of k and k-1.
- Jaccard index. The ratio of pairs of samples are both in a same cluster in
  the partition of k and k-1 and the pairs of samples are both in a same
  cluster in the partition k or k-1.

The detailed explanations of these statistics can be found in [the _cola_
vignette](https://jokergoo.github.io/cola_vignettes/cola.html#toc_13).

Generally speaking, higher 1-PAC score, higher mean silhouette score or higher
concordance corresponds to better partition. Rand index and Jaccard index
measure how similar the current partition is compared to partition with `k-1`.
If they are too similar, we won't accept `k` is better than `k-1`.

```r
select_partition_number(res)
```

![plot of chunk node-0322-select-partition-number](figure_cola/node-0322-select-partition-number-1.png)

The numeric values for all these statistics can be obtained by `get_stats()`.

```r
get_stats(res)
```

```
#>   k 1-PAC mean_silhouette concordance area_increased  Rand Jaccard
#> 2 2 1.000           1.000       1.000         0.4401 0.560   0.560
#> 3 3 0.791           0.953       0.979         0.4400 0.659   0.466
#> 4 4 0.725           0.793       0.906         0.1922 0.868   0.647
#> 5 5 0.648           0.730       0.897         0.0287 0.978   0.909
#> 6 6 0.791           0.581       0.879         0.0518 0.989   0.950
#> 7 7 0.824           0.549       0.913         0.0241 0.978   0.895
#> 8 8 0.857           0.401       0.889         0.0330 0.989   0.941
```

`suggest_best_k()` suggests the best $k$ based on these statistics. The rules are as follows:

- All $k$ with Jaccard index larger than 0.95 are removed because increasing
  $k$ does not provide enough extra information. If all $k$ are removed, it is
  marked as no subgroup is detected.
- For all $k$ with 1-PAC score larger than 0.9, the maximal $k$ is taken as
  the best $k$, and other $k$ are marked as optional $k$.
- If it does not fit the second rule. The $k$ with the maximal vote of the
  highest 1-PAC score, highest mean silhouette, and highest concordance is
  taken as the best $k$.

```r
suggest_best_k(res)
```

```
#> [1] 2
```


Following is the table of the partitions (You need to click the **show/hide
code output** link to see it). The membership matrix (columns with name `p*`)
is inferred by
[`clue::cl_consensus()`](https://www.rdocumentation.org/link/cl_consensus?package=clue)
function with the `SE` method. Basically the value in the membership matrix
represents the probability to belong to a certain group. The finall subgroup
label for an item is determined with the group with highest probability it
belongs to.

In `get_classes()` function, the entropy is calculated from the membership
matrix and the silhouette score is calculated from the consensus matrix.



<script>
$( function() {
	$( '#tabs-node-0322-get-classes' ).tabs();
} );
</script>
<div id='tabs-node-0322-get-classes'>
<ul>
<li><a href='#tab-node-0322-get-classes-1'>k = 2</a></li>
<li><a href='#tab-node-0322-get-classes-2'>k = 3</a></li>
<li><a href='#tab-node-0322-get-classes-3'>k = 4</a></li>
<li><a href='#tab-node-0322-get-classes-4'>k = 5</a></li>
<li><a href='#tab-node-0322-get-classes-5'>k = 6</a></li>
<li><a href='#tab-node-0322-get-classes-6'>k = 7</a></li>
<li><a href='#tab-node-0322-get-classes-7'>k = 8</a></li>
</ul>

<div id='tab-node-0322-get-classes-1'>
<p><a id='tab-node-0322-get-classes-1-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 2), get_membership(res, k = 2))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette p1 p2
#&gt; TCGA.CI.6620.01     1       0          1  1  0
#&gt; TCGA.F5.6465.01     1       0          1  1  0
#&gt; TCGA.DY.A1H8.01     2       0          1  0  1
#&gt; TCGA.CL.5917.01     2       0          1  0  1
#&gt; TCGA.AF.6136.01     2       0          1  0  1
#&gt; TCGA.EI.6512.01     2       0          1  0  1
#&gt; TCGA.F5.6863.01     2       0          1  0  1
#&gt; TCGA.F5.6464.01     1       0          1  1  0
#&gt; TCGA.AF.A56N.01     2       0          1  0  1
#&gt; TCGA.AG.3732.01     1       0          1  1  0
#&gt; TCGA.AF.A56L.01     2       0          1  0  1
#&gt; TCGA.DC.6155.01     2       0          1  0  1
#&gt; TCGA.CL.4957.01     2       0          1  0  1
#&gt; TCGA.F5.6571.01     2       0          1  0  1
</code></pre>

<script>
$('#tab-node-0322-get-classes-1-a').parent().next().next().hide();
$('#tab-node-0322-get-classes-1-a').click(function(){
  $('#tab-node-0322-get-classes-1-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0322-get-classes-2'>
<p><a id='tab-node-0322-get-classes-2-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 3), get_membership(res, k = 3))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3
#&gt; TCGA.CI.6620.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.F5.6465.01     2   0.334      0.858 0.12 0.88 0.00
#&gt; TCGA.DY.A1H8.01     2   0.334      0.855 0.00 0.88 0.12
#&gt; TCGA.CL.5917.01     2   0.000      0.964 0.00 1.00 0.00
#&gt; TCGA.AF.6136.01     3   0.000      0.961 0.00 0.00 1.00
#&gt; TCGA.EI.6512.01     3   0.000      0.961 0.00 0.00 1.00
#&gt; TCGA.F5.6863.01     2   0.000      0.964 0.00 1.00 0.00
#&gt; TCGA.F5.6464.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AF.A56N.01     2   0.000      0.964 0.00 1.00 0.00
#&gt; TCGA.AG.3732.01     1   0.000      1.000 1.00 0.00 0.00
#&gt; TCGA.AF.A56L.01     2   0.000      0.964 0.00 1.00 0.00
#&gt; TCGA.DC.6155.01     2   0.000      0.964 0.00 1.00 0.00
#&gt; TCGA.CL.4957.01     2   0.000      0.964 0.00 1.00 0.00
#&gt; TCGA.F5.6571.01     3   0.207      0.921 0.00 0.06 0.94
</code></pre>

<script>
$('#tab-node-0322-get-classes-2-a').parent().next().next().hide();
$('#tab-node-0322-get-classes-2-a').click(function(){
  $('#tab-node-0322-get-classes-2-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0322-get-classes-3'>
<p><a id='tab-node-0322-get-classes-3-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 4), get_membership(res, k = 4))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4
#&gt; TCGA.CI.6620.01     1  0.3801      0.848 0.78 0.00 0.00 0.22
#&gt; TCGA.F5.6465.01     4  0.1411      0.598 0.02 0.02 0.00 0.96
#&gt; TCGA.DY.A1H8.01     2  0.3037      0.776 0.00 0.88 0.10 0.02
#&gt; TCGA.CL.5917.01     2  0.0000      0.879 0.00 1.00 0.00 0.00
#&gt; TCGA.AF.6136.01     3  0.0707      0.956 0.00 0.00 0.98 0.02
#&gt; TCGA.EI.6512.01     3  0.0000      0.961 0.00 0.00 1.00 0.00
#&gt; TCGA.F5.6863.01     2  0.0000      0.879 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6464.01     1  0.4134      0.827 0.74 0.00 0.00 0.26
#&gt; TCGA.AF.A56N.01     4  0.5147      0.639 0.00 0.20 0.06 0.74
#&gt; TCGA.AG.3732.01     1  0.0000      0.745 1.00 0.00 0.00 0.00
#&gt; TCGA.AF.A56L.01     2  0.0000      0.879 0.00 1.00 0.00 0.00
#&gt; TCGA.DC.6155.01     2  0.4713      0.291 0.00 0.64 0.00 0.36
#&gt; TCGA.CL.4957.01     2  0.0000      0.879 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6571.01     3  0.1211      0.936 0.00 0.04 0.96 0.00
</code></pre>

<script>
$('#tab-node-0322-get-classes-3-a').parent().next().next().hide();
$('#tab-node-0322-get-classes-3-a').click(function(){
  $('#tab-node-0322-get-classes-3-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0322-get-classes-4'>
<p><a id='tab-node-0322-get-classes-4-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 5), get_membership(res, k = 5))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5
#&gt; TCGA.CI.6620.01     1   0.173      0.823 0.92 0.00 0.00 0.00 0.08
#&gt; TCGA.F5.6465.01     4   0.311      0.534 0.20 0.00 0.00 0.80 0.00
#&gt; TCGA.DY.A1H8.01     2   0.351      0.739 0.00 0.80 0.18 0.02 0.00
#&gt; TCGA.CL.5917.01     2   0.000      0.914 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.AF.6136.01     3   0.329      0.759 0.00 0.00 0.84 0.04 0.12
#&gt; TCGA.EI.6512.01     3   0.000      0.811 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.F5.6863.01     2   0.000      0.914 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6464.01     1   0.104      0.834 0.96 0.00 0.00 0.04 0.00
#&gt; TCGA.AF.A56N.01     4   0.503      0.575 0.00 0.10 0.06 0.76 0.08
#&gt; TCGA.AG.3732.01     5   0.311      0.000 0.20 0.00 0.00 0.00 0.80
#&gt; TCGA.AF.A56L.01     2   0.000      0.914 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     2   0.332      0.752 0.02 0.82 0.00 0.16 0.00
#&gt; TCGA.CL.4957.01     2   0.000      0.914 0.00 1.00 0.00 0.00 0.00
#&gt; TCGA.F5.6571.01     3   0.252      0.734 0.00 0.14 0.86 0.00 0.00
</code></pre>

<script>
$('#tab-node-0322-get-classes-4-a').parent().next().next().hide();
$('#tab-node-0322-get-classes-4-a').click(function(){
  $('#tab-node-0322-get-classes-4-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0322-get-classes-5'>
<p><a id='tab-node-0322-get-classes-5-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 6), get_membership(res, k = 6))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6
#&gt; TCGA.CI.6620.01     1  0.3045      0.790 0.84 0.00 0.00 0.06 0.10 0.00
#&gt; TCGA.F5.6465.01     4  0.3706      0.000 0.00 0.00 0.00 0.62 0.00 0.38
#&gt; TCGA.DY.A1H8.01     2  0.4495      0.610 0.00 0.72 0.20 0.06 0.00 0.02
#&gt; TCGA.CL.5917.01     2  0.0000      0.849 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.6136.01     3  0.4222      0.645 0.02 0.00 0.70 0.26 0.02 0.00
#&gt; TCGA.EI.6512.01     3  0.0547      0.789 0.00 0.00 0.98 0.02 0.00 0.00
#&gt; TCGA.F5.6863.01     2  0.0000      0.849 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6464.01     1  0.0937      0.801 0.96 0.00 0.00 0.04 0.00 0.00
#&gt; TCGA.AF.A56N.01     6  0.0937      0.000 0.00 0.00 0.04 0.00 0.00 0.96
#&gt; TCGA.AG.3732.01     5  0.0547      0.000 0.02 0.00 0.00 0.00 0.98 0.00
#&gt; TCGA.AF.A56L.01     2  0.0000      0.849 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     2  0.6037      0.336 0.06 0.58 0.00 0.12 0.00 0.24
#&gt; TCGA.CL.4957.01     2  0.0000      0.849 0.00 1.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6571.01     3  0.1865      0.769 0.04 0.04 0.92 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0322-get-classes-5-a').parent().next().next().hide();
$('#tab-node-0322-get-classes-5-a').click(function(){
  $('#tab-node-0322-get-classes-5-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0322-get-classes-6'>
<p><a id='tab-node-0322-get-classes-6-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 7), get_membership(res, k = 7))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4   p5   p6   p7
#&gt; TCGA.CI.6620.01     1  0.3927      0.769 0.76 0.00 0.00 0.02 0.08 0.00 0.14
#&gt; TCGA.F5.6465.01     4  0.0504      0.000 0.00 0.00 0.00 0.98 0.00 0.02 0.00
#&gt; TCGA.DY.A1H8.01     2  0.4108      0.509 0.00 0.66 0.28 0.00 0.00 0.06 0.00
#&gt; TCGA.CL.5917.01     2  0.0000      0.844 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.6136.01     7  0.2081      0.000 0.00 0.00 0.14 0.00 0.00 0.00 0.86
#&gt; TCGA.EI.6512.01     3  0.0504      0.896 0.00 0.00 0.98 0.00 0.00 0.00 0.02
#&gt; TCGA.F5.6863.01     2  0.0000      0.844 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.F5.6464.01     1  0.0000      0.778 1.00 0.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.AF.A56N.01     6  0.0000      0.000 0.00 0.00 0.00 0.00 0.00 1.00 0.00
#&gt; TCGA.AG.3732.01     5  0.0000      0.000 0.00 0.00 0.00 0.00 1.00 0.00 0.00
#&gt; TCGA.AF.A56L.01     2  0.0000      0.844 0.00 1.00 0.00 0.00 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     2  0.4908      0.459 0.02 0.62 0.00 0.26 0.00 0.10 0.00
#&gt; TCGA.CL.4957.01     2  0.0504      0.838 0.00 0.98 0.00 0.00 0.00 0.02 0.00
#&gt; TCGA.F5.6571.01     3  0.1363      0.898 0.00 0.04 0.94 0.00 0.00 0.02 0.00
</code></pre>

<script>
$('#tab-node-0322-get-classes-6-a').parent().next().next().hide();
$('#tab-node-0322-get-classes-6-a').click(function(){
  $('#tab-node-0322-get-classes-6-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>

<div id='tab-node-0322-get-classes-7'>
<p><a id='tab-node-0322-get-classes-7-a' style='color:#0366d6' href='#'>show/hide code output</a></p>
<pre><code class="r">cbind(get_classes(res, k = 8), get_membership(res, k = 8))
</code></pre>

<pre><code>#&gt;                 class entropy silhouette   p1   p2   p3   p4 p5   p6   p7   p8
#&gt; TCGA.CI.6620.01     1  0.0000      0.000 1.00 0.00 0.00 0.00  0 0.00 0.00 0.00
#&gt; TCGA.F5.6465.01     4  0.0000      0.000 0.00 0.00 0.00 1.00  0 0.00 0.00 0.00
#&gt; TCGA.DY.A1H8.01     2  0.5936      0.139 0.00 0.40 0.16 0.00  0 0.04 0.02 0.38
#&gt; TCGA.CL.5917.01     2  0.0000      0.793 0.00 1.00 0.00 0.00  0 0.00 0.00 0.00
#&gt; TCGA.AF.6136.01     7  0.0471      0.000 0.00 0.00 0.02 0.00  0 0.00 0.98 0.00
#&gt; TCGA.EI.6512.01     3  0.0941      0.960 0.00 0.00 0.96 0.00  0 0.00 0.02 0.02
#&gt; TCGA.F5.6863.01     2  0.0000      0.793 0.00 1.00 0.00 0.00  0 0.00 0.00 0.00
#&gt; TCGA.F5.6464.01     8  0.3329      0.000 0.48 0.00 0.00 0.00  0 0.00 0.00 0.52
#&gt; TCGA.AF.A56N.01     6  0.0000      0.000 0.00 0.00 0.00 0.00  0 1.00 0.00 0.00
#&gt; TCGA.AG.3732.01     5  0.0000      0.000 0.00 0.00 0.00 0.00  1 0.00 0.00 0.00
#&gt; TCGA.AF.A56L.01     2  0.0000      0.793 0.00 1.00 0.00 0.00  0 0.00 0.00 0.00
#&gt; TCGA.DC.6155.01     2  0.5687      0.387 0.00 0.58 0.02 0.16  0 0.08 0.00 0.16
#&gt; TCGA.CL.4957.01     2  0.0000      0.793 0.00 1.00 0.00 0.00  0 0.00 0.00 0.00
#&gt; TCGA.F5.6571.01     3  0.0000      0.960 0.00 0.00 1.00 0.00  0 0.00 0.00 0.00
</code></pre>

<script>
$('#tab-node-0322-get-classes-7-a').parent().next().next().hide();
$('#tab-node-0322-get-classes-7-a').click(function(){
  $('#tab-node-0322-get-classes-7-a').parent().next().next().toggle();
  return(false);
});
</script>
</div>
</div>

Heatmaps for the consensus matrix. It visualizes the probability of two
samples to be in a same group.




<script>
$( function() {
	$( '#tabs-node-0322-consensus-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-0322-consensus-heatmap'>
<ul>
<li><a href='#tab-node-0322-consensus-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-0322-consensus-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-0322-consensus-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-0322-consensus-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-0322-consensus-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-0322-consensus-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-0322-consensus-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-0322-consensus-heatmap-1'>
<pre><code class="r">consensus_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0322-consensus-heatmap-1-1.png" alt="plot of chunk tab-node-0322-consensus-heatmap-1"/></p>

</div>
<div id='tab-node-0322-consensus-heatmap-2'>
<pre><code class="r">consensus_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0322-consensus-heatmap-2-1.png" alt="plot of chunk tab-node-0322-consensus-heatmap-2"/></p>

</div>
<div id='tab-node-0322-consensus-heatmap-3'>
<pre><code class="r">consensus_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0322-consensus-heatmap-3-1.png" alt="plot of chunk tab-node-0322-consensus-heatmap-3"/></p>

</div>
<div id='tab-node-0322-consensus-heatmap-4'>
<pre><code class="r">consensus_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0322-consensus-heatmap-4-1.png" alt="plot of chunk tab-node-0322-consensus-heatmap-4"/></p>

</div>
<div id='tab-node-0322-consensus-heatmap-5'>
<pre><code class="r">consensus_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0322-consensus-heatmap-5-1.png" alt="plot of chunk tab-node-0322-consensus-heatmap-5"/></p>

</div>
<div id='tab-node-0322-consensus-heatmap-6'>
<pre><code class="r">consensus_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0322-consensus-heatmap-6-1.png" alt="plot of chunk tab-node-0322-consensus-heatmap-6"/></p>

</div>
<div id='tab-node-0322-consensus-heatmap-7'>
<pre><code class="r">consensus_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0322-consensus-heatmap-7-1.png" alt="plot of chunk tab-node-0322-consensus-heatmap-7"/></p>

</div>
</div>

Heatmaps for the membership of samples in all partitions to see how consistent they are:





<script>
$( function() {
	$( '#tabs-node-0322-membership-heatmap' ).tabs();
} );
</script>
<div id='tabs-node-0322-membership-heatmap'>
<ul>
<li><a href='#tab-node-0322-membership-heatmap-1'>k = 2</a></li>
<li><a href='#tab-node-0322-membership-heatmap-2'>k = 3</a></li>
<li><a href='#tab-node-0322-membership-heatmap-3'>k = 4</a></li>
<li><a href='#tab-node-0322-membership-heatmap-4'>k = 5</a></li>
<li><a href='#tab-node-0322-membership-heatmap-5'>k = 6</a></li>
<li><a href='#tab-node-0322-membership-heatmap-6'>k = 7</a></li>
<li><a href='#tab-node-0322-membership-heatmap-7'>k = 8</a></li>
</ul>
<div id='tab-node-0322-membership-heatmap-1'>
<pre><code class="r">membership_heatmap(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0322-membership-heatmap-1-1.png" alt="plot of chunk tab-node-0322-membership-heatmap-1"/></p>

</div>
<div id='tab-node-0322-membership-heatmap-2'>
<pre><code class="r">membership_heatmap(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0322-membership-heatmap-2-1.png" alt="plot of chunk tab-node-0322-membership-heatmap-2"/></p>

</div>
<div id='tab-node-0322-membership-heatmap-3'>
<pre><code class="r">membership_heatmap(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0322-membership-heatmap-3-1.png" alt="plot of chunk tab-node-0322-membership-heatmap-3"/></p>

</div>
<div id='tab-node-0322-membership-heatmap-4'>
<pre><code class="r">membership_heatmap(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0322-membership-heatmap-4-1.png" alt="plot of chunk tab-node-0322-membership-heatmap-4"/></p>

</div>
<div id='tab-node-0322-membership-heatmap-5'>
<pre><code class="r">membership_heatmap(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0322-membership-heatmap-5-1.png" alt="plot of chunk tab-node-0322-membership-heatmap-5"/></p>

</div>
<div id='tab-node-0322-membership-heatmap-6'>
<pre><code class="r">membership_heatmap(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0322-membership-heatmap-6-1.png" alt="plot of chunk tab-node-0322-membership-heatmap-6"/></p>

</div>
<div id='tab-node-0322-membership-heatmap-7'>
<pre><code class="r">membership_heatmap(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0322-membership-heatmap-7-1.png" alt="plot of chunk tab-node-0322-membership-heatmap-7"/></p>

</div>
</div>

As soon as the classes for columns are determined, the signatures
that are significantly different between subgroups can be looked for. 
Following are the heatmaps for signatures.






<script>
$( function() {
	$( '#tabs-node-0322-get-signatures' ).tabs();
} );
</script>
<div id='tabs-node-0322-get-signatures'>
<ul>
<li><a href='#tab-node-0322-get-signatures-1'>k = 2</a></li>
<li><a href='#tab-node-0322-get-signatures-2'>k = 3</a></li>
<li><a href='#tab-node-0322-get-signatures-3'>k = 4</a></li>
<li><a href='#tab-node-0322-get-signatures-4'>k = 5</a></li>
<li><a href='#tab-node-0322-get-signatures-5'>k = 6</a></li>
<li><a href='#tab-node-0322-get-signatures-6'>k = 7</a></li>
<li><a href='#tab-node-0322-get-signatures-7'>k = 8</a></li>
</ul>
<div id='tab-node-0322-get-signatures-1'>
<pre><code class="r">get_signatures(res, k = 2)
</code></pre>

<p><img src="figure_cola/tab-node-0322-get-signatures-1-1.png" alt="plot of chunk tab-node-0322-get-signatures-1"/></p>

</div>
<div id='tab-node-0322-get-signatures-2'>
<pre><code class="r">get_signatures(res, k = 3)
</code></pre>

<p><img src="figure_cola/tab-node-0322-get-signatures-2-1.png" alt="plot of chunk tab-node-0322-get-signatures-2"/></p>

</div>
<div id='tab-node-0322-get-signatures-3'>
<pre><code class="r">get_signatures(res, k = 4)
</code></pre>

<p><img src="figure_cola/tab-node-0322-get-signatures-3-1.png" alt="plot of chunk tab-node-0322-get-signatures-3"/></p>

</div>
<div id='tab-node-0322-get-signatures-4'>
<pre><code class="r">get_signatures(res, k = 5)
</code></pre>

<p><img src="figure_cola/tab-node-0322-get-signatures-4-1.png" alt="plot of chunk tab-node-0322-get-signatures-4"/></p>

</div>
<div id='tab-node-0322-get-signatures-5'>
<pre><code class="r">get_signatures(res, k = 6)
</code></pre>

<p><img src="figure_cola/tab-node-0322-get-signatures-5-1.png" alt="plot of chunk tab-node-0322-get-signatures-5"/></p>

</div>
<div id='tab-node-0322-get-signatures-6'>
<pre><code class="r">get_signatures(res, k = 7)
</code></pre>

<p><img src="figure_cola/tab-node-0322-get-signatures-6-1.png" alt="plot of chunk tab-node-0322-get-signatures-6"/></p>

</div>
<div id='tab-node-0322-get-signatures-7'>
<pre><code class="r">get_signatures(res, k = 8)
</code></pre>

<p><img src="figure_cola/tab-node-0322-get-signatures-7-1.png" alt="plot of chunk tab-node-0322-get-signatures-7"/></p>

</div>
</div>



Compare the overlap of signatures from different k:

```r
compare_signatures(res)
```

![plot of chunk node-0322-signature_compare](figure_cola/node-0322-signature_compare-1.png)

`get_signature()` returns a data frame invisibly. To get the list of signatures, the function
call should be assigned to a variable explicitly. In following code, if `plot` argument is set
to `FALSE`, no heatmap is plotted while only the differential analysis is performed.

```r
# code only for demonstration
tb = get_signature(res, k = ..., plot = FALSE)
```

An example of the output of `tb` is:

```
#>   which_row         fdr    mean_1    mean_2 scaled_mean_1 scaled_mean_2 km
#> 1        38 0.042760348  8.373488  9.131774    -0.5533452     0.5164555  1
#> 2        40 0.018707592  7.106213  8.469186    -0.6173731     0.5762149  1
#> 3        55 0.019134737 10.221463 11.207825    -0.6159697     0.5749050  1
#> 4        59 0.006059896  5.921854  7.869574    -0.6899429     0.6439467  1
#> 5        60 0.018055526  8.928898 10.211722    -0.6204761     0.5791110  1
#> 6        98 0.009384629 15.714769 14.887706     0.6635654    -0.6193277  2
...
```

The columns in `tb` are:

1. `which_row`: row indices corresponding to the input matrix.
2. `fdr`: FDR for the differential test. 
3. `mean_x`: The mean value in group x.
4. `scaled_mean_x`: The mean value in group x after rows are scaled.
5. `km`: Row groups if k-means clustering is applied to rows (which is done by automatically selecting number of clusters).

If there are too many signatures, `top_signatures = ...` can be set to only show the 
signatures with the highest FDRs:

```r
# code only for demonstration
# e.g. to show the top 500 most significant rows
tb = get_signature(res, k = ..., top_signatures = 500)
```

If the signatures are defined as these which are uniquely high in current group, `diff_method` argument
can be set to `"uniquely_high_in_one_group"`:

```r
# code only for demonstration
tb = get_signature(res, k = ..., diff_method = "uniquely_high_in_one_group")
```




UMAP plot which shows how samples are separated.


<script>
$( function() {
	$( '#tabs-node-0322-dimension-reduction' ).tabs();
} );
</script>
<div id='tabs-node-0322-dimension-reduction'>
<ul>
<li><a href='#tab-node-0322-dimension-reduction-1'>k = 2</a></li>
<li><a href='#tab-node-0322-dimension-reduction-2'>k = 3</a></li>
<li><a href='#tab-node-0322-dimension-reduction-3'>k = 4</a></li>
<li><a href='#tab-node-0322-dimension-reduction-4'>k = 5</a></li>
<li><a href='#tab-node-0322-dimension-reduction-5'>k = 6</a></li>
<li><a href='#tab-node-0322-dimension-reduction-6'>k = 7</a></li>
<li><a href='#tab-node-0322-dimension-reduction-7'>k = 8</a></li>
</ul>
<div id='tab-node-0322-dimension-reduction-1'>
<pre><code class="r">dimension_reduction(res, k = 2, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0322-dimension-reduction-1-1.png" alt="plot of chunk tab-node-0322-dimension-reduction-1"/></p>

</div>
<div id='tab-node-0322-dimension-reduction-2'>
<pre><code class="r">dimension_reduction(res, k = 3, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0322-dimension-reduction-2-1.png" alt="plot of chunk tab-node-0322-dimension-reduction-2"/></p>

</div>
<div id='tab-node-0322-dimension-reduction-3'>
<pre><code class="r">dimension_reduction(res, k = 4, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0322-dimension-reduction-3-1.png" alt="plot of chunk tab-node-0322-dimension-reduction-3"/></p>

</div>
<div id='tab-node-0322-dimension-reduction-4'>
<pre><code class="r">dimension_reduction(res, k = 5, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0322-dimension-reduction-4-1.png" alt="plot of chunk tab-node-0322-dimension-reduction-4"/></p>

</div>
<div id='tab-node-0322-dimension-reduction-5'>
<pre><code class="r">dimension_reduction(res, k = 6, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0322-dimension-reduction-5-1.png" alt="plot of chunk tab-node-0322-dimension-reduction-5"/></p>

</div>
<div id='tab-node-0322-dimension-reduction-6'>
<pre><code class="r">dimension_reduction(res, k = 7, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0322-dimension-reduction-6-1.png" alt="plot of chunk tab-node-0322-dimension-reduction-6"/></p>

</div>
<div id='tab-node-0322-dimension-reduction-7'>
<pre><code class="r">dimension_reduction(res, k = 8, method = &quot;UMAP&quot;)
</code></pre>

<p><img src="figure_cola/tab-node-0322-dimension-reduction-7-1.png" alt="plot of chunk tab-node-0322-dimension-reduction-7"/></p>

</div>
</div>



Following heatmap shows how subgroups are split when increasing `k`:

```r
collect_classes(res)
```

![plot of chunk node-0322-collect-classes](figure_cola/node-0322-collect-classes-1.png)



If matrix rows can be associated to genes, consider to use `functional_enrichment(res,
...)` to perform function enrichment for the signature genes. See [this vignette](https://jokergoo.github.io/cola_vignettes/functional_enrichment.html) for more detailed explanations.


 

## Session info


```r
sessionInfo()
```

```
#> R version 4.1.0 (2021-05-18)
#> Platform: x86_64-pc-linux-gnu (64-bit)
#> Running under: CentOS Linux 7 (Core)
#> 
#> Matrix products: default
#> BLAS/LAPACK: /usr/lib64/libopenblas-r0.3.3.so
#> 
#> locale:
#>  [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C               LC_TIME=en_US.UTF-8       
#>  [4] LC_COLLATE=en_US.UTF-8     LC_MONETARY=en_US.UTF-8    LC_MESSAGES=en_US.UTF-8   
#>  [7] LC_PAPER=en_US.UTF-8       LC_NAME=C                  LC_ADDRESS=C              
#> [10] LC_TELEPHONE=C             LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C       
#> 
#> attached base packages:
#> [1] grid      stats     graphics  grDevices utils     datasets  methods   base     
#> 
#> other attached packages:
#> [1] genefilter_1.74.0    ComplexHeatmap_2.8.0 markdown_1.1         knitr_1.33          
#> [5] matrixStats_0.59.0   cola_1.9.4          
#> 
#> loaded via a namespace (and not attached):
#>   [1] bitops_1.0-7           bit64_4.0.5            doParallel_1.0.16      RColorBrewer_1.1-2    
#>   [5] httr_1.4.2             GenomeInfoDb_1.28.1    data.tree_1.0.0        tools_4.1.0           
#>   [9] utf8_1.2.1             R6_2.5.0               irlba_2.3.3            DBI_1.1.1             
#>  [13] BiocGenerics_0.38.0    colorspace_2.0-2       GetoptLong_1.0.5       gridExtra_2.3         
#>  [17] tidyselect_1.1.1       bit_4.0.4              compiler_4.1.0         Biobase_2.52.0        
#>  [21] Cairo_1.5-12.2         xml2_1.3.2             microbenchmark_1.4-7   slam_0.1-48           
#>  [25] scales_1.1.1           askpass_1.1            stringr_1.4.0          digest_0.6.27         
#>  [29] XVector_0.32.0         pkgconfig_2.0.3        umap_0.2.7.0           fastmap_1.1.0         
#>  [33] highr_0.9              rlang_0.4.11           GlobalOptions_0.1.2    rstudioapi_0.13       
#>  [37] RSQLite_2.2.7          impute_1.66.0          generics_0.1.0         shape_1.4.6           
#>  [41] jsonlite_1.7.2         mclust_5.4.7           dplyr_1.0.7            dendextend_1.15.1     
#>  [45] RCurl_1.98-1.3         magrittr_2.0.1         GenomeInfoDbData_1.2.6 Matrix_1.3-4          
#>  [49] fansi_0.5.0            Rcpp_1.0.7             munsell_0.5.0          S4Vectors_0.30.0      
#>  [53] viridis_0.6.1          reticulate_1.20        lifecycle_1.0.0        scatterplot3d_0.3-41  
#>  [57] stringi_1.7.3          zlibbioc_1.38.0        blob_1.2.1             parallel_4.1.0        
#>  [61] crayon_1.4.1           lattice_0.20-44        Biostrings_2.60.1      splines_4.1.0         
#>  [65] annotate_1.70.0        circlize_0.4.13        KEGGREST_1.32.0        polylabelr_0.2.0      
#>  [69] pillar_1.6.1           rjson_0.2.20           codetools_0.2-18       stats4_4.1.0          
#>  [73] XML_3.99-0.6           glue_1.4.2             evaluate_0.14          png_0.1-7             
#>  [77] vctrs_0.3.8            foreach_1.5.1          polyclip_1.10-0        purrr_0.3.4           
#>  [81] gtable_0.3.0           openssl_1.4.4          assertthat_0.2.1       clue_0.3-59           
#>  [85] cachem_1.0.5           ggplot2_3.3.5          xfun_0.24              eulerr_6.1.0          
#>  [89] xtable_1.8-4           skmeans_0.2-13         RSpectra_0.16-0        viridisLite_0.4.0     
#>  [93] survival_3.2-11        tibble_3.1.2           Polychrome_1.3.1       iterators_1.0.13      
#>  [97] AnnotationDbi_1.54.1   memoise_2.0.0          IRanges_2.26.0         cluster_2.1.2         
#> [101] ellipsis_0.3.2         brew_1.0-6
```




