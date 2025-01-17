# spatialGE.STplot (v1)

The `spatialGE.STplot` module is part of the spatialGE package. It generates a plot of the location of spots/cells 
within a spatial sample, and colors them according to gene expression levels or spot/cell-level metadata.

## Module Details

- **Authors:** Thorin Tabor; UCSD - Mesirov Lab
- **Categories:** spatial transcriptomics
- **Source repository:** [spatialGE.Preprocessing on GitHub](https://github.com/genepattern/spatialGE.STplot)
- **Contact**: [GenePattern Help Forum](https://groups.google.com/forum/?utm_medium=email&utm_source=footer#!forum/genepattern-help)
- **Algorithm Version**: [spatialGE 1.2.0](https://fridleylab.github.io/spatialGE/)

## Summary

[STplot](https://fridleylab.github.io/spatialGE/) generates a plot of the location of spots/cells within a spatial 
sample, and colors them according to gene expression levels or spot/cell-level metadata.

This module accepts an RDS file containing a STlist object, such as output by [spatialGE.Preprocessing](https://github.com/genepattern/spatialGE.Preprocessing) 
and optionally clustering data, such as output by the [spatialGE.STclust](https://github.com/genepattern/spatialGE.STclust) module.

## References

Ospina, O. E., Wilson C. M., Soupir, A. C., Berglund, A. Smalley, I., Tsai, K. Y., Fridley, B. L. 2022. spatialGE: quantification and visualization of the tumor microenvironment heterogeneity using spatial transcriptomics. Bioinformatics, 38:2645-2647. https://doi.org/10.1093/bioinformatics/btac145

## Source Links
* [spatialGE.STplot source repository](https://github.com/genepattern/spatialGE.STplot/)

## Parameters

| Name              | Description                                                                                                                                                                                         | Default Value |
|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| input file *      | Spatial transcriptomics data coming from spatialGE.Preprocessing or another spatialGE module.                                                                                                       |               |
| genes             | Comma-separated list of gene names to plot. If left blank, all genes will be used.                                                                                                                  |               |
| samples           | Comma-separated list of sample names to include. If left blank, all samples will be used.                                                                                                           |               |
| color palette     | Alternative color palette to use when generating the plot.                                                                                                                                          |               |
| colors            | A comma separated list of specific colors to use when generating the plot.                                                                                                                          |               |
| point size        | Alternative size of points marked by the plot, provided as a floating point number.                                                                                                                 |               |
| spatial weights   | Plot tissue domains for clusters created using the following spatial weights. Provide as a comma separated list. Must match spatial weights previously used in spatialGE.STclust.                   |               |
| dynamic tree cut  | Whether the number of clusters was determined using Dynamic Tree Cut in the earlier spatialGE.STclust step. If you have not previously run spatialGE.STclust with this data, leave the value blank. |               |
| minimum clusters  | The minimum number of clusters (tissue domains) to plot. Must match one of of the clusterings previously run in spatialGE.STclust. Only used if Dynamic Tree Cut is false.                          |               |
| maximum clusters  | The maximum number of clusters (tissue domains) to plot. Must match one of of the clusterings previously run in spatialGE.STclust. Only used if Dynamic Tree Cut is false.                          |               |
| deep split        | Whether deepSplit was used in the earlier spatialGE.STclust step. If you have not previously run spatialGE.STclust with this data, leave the value blank.                                           |               |
 | display in grid * | Whether to display the results in a singular grid containing all plots. If set to false, each plot will be saved as its own image file.                                                             | FALSE         |
 | grid rows *       | The number of rows in the grid containing all plots. Ignored unless display in grid is set to true.                                                                                                 |               |
 | grid columns *    | The number of columns in the grid containing all plots. Ignored unless display in grid is set to true.                                                                                              |               |
 | common legend *   | Whether the grid of plots should share a common legend. If set to false, each grid will have its own accompanying legend. Ignored unless display in grid is set to true.                            | TRUE          |
 | legend location * | The location of the legend accompanying the plots.                                                                                                                                                  | bottom        |

\*  required

## Input Files
1. input.file  
   Accepts an RDS file containing a STlist object, such as output by [spatialGE.Preprocessing](https://github.com/genepattern/spatialGE.Preprocessing)
   and optionally clustering data, such as output by the [spatialGE.STclust](https://github.com/genepattern/spatialGE.STclust) module.

    
## Output Files
1. **\*.jpg**  
   Images containing one or more plots, as generated by the STplot method.

## Example Data

Input:  
[lung.rds](https://github.com/genepattern/spatialGE.STplot/blob/main/data/lung.rds)

## Requirements

Requires the [genepattern/spatialge-stplot:0.1 Docker image](https://hub.docker.com/layers/genepattern/spatialge-stplot/0.1/images/sha256-89506dbe3c0187ae8523dd1f677bc46990ce1fdb6e8d1f1ac929f999571d6196).

## License

`spatialGE.STplot` is distributed under a BSD-style license available at [https://github.com/genepattern/spatialGE.STplot/blob/main/LICENSE.](https://github.com/genepattern/spatialGE.STplot/blob/main/LICENSE)

## Version Comments

| Version | Release Date     | Description     |
|---------|------------------|-----------------|
| 1       | January 17, 2025 | Initial version |
