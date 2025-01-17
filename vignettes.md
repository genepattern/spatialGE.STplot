# Quilt plots -- downstream of Preprocessing

quilts1 <- STplot(tnbc, 
                  genes=c('NDRG1', 'IGKC'), 
                  samples='sample_094c', 
                  color_pal='BuRd', 
                  ptsize=0.8)

# Gene interpolation params -- downstream of ???

```{r genekrige_chunk}
tnbc <- gene_interpolation(tnbc, 
                           genes=c('NDRG1', 'IGKC'),
                           samples=c('sample_094c', 'sample_117e'))
```

Generating gene expression surfaces can be time consuming. The finer resolution to which the surface is to be predicted (`ngrid` argument), the longer the time it takes. The execution time also depends on the number of spots/cells. The surfaces can be visualized using the `STplot_interpolation()` function:

```{r plotkrige_chunk1, fig.align='center'}
kriges1 <- STplot_interpolation(tnbc,
                                genes=c('NDRG1', 'IGKC'),
                                samples='sample_094c')
ggpubr::ggarrange(plotlist=kriges1, nrow=1, ncol=2, common.legend=T, legend='bottom')
```

# Clustering weight comparison -- downstream of STclust

```{r plotclustspots_chunk, fig.align='center'}
cluster_p <- STplot(tnbc, 
                    samples='sample_094c', 
                    ws=c(0, 0.025, 0.05, 0.2),
                    color_pal='highcontrast')
ggpubr::ggarrange(plotlist=cluster_p, nrow=2, ncol=2, legend='right')
```

# Specific clustering -- downstream of STclust

```{r plotclustspots_chunk, fig.align='center', fig.height=4, fig.width=3}
cluster_p <- STplot(melanoma, 
                    samples='ST_mel1_rep1', 
                    ws=0.025, 
                    deepSplit=F,
                    ptsize=2, color=c('#00BA38', '#619CFF', '#F8766D'))

print(cluster_p[[1]])
```


# Gene set comparison -- downstream of STenrich

```{r notch_plots, fig.width=10}
qp <- STplot(lung, genes=gene_sets[names(gene_sets) == 'HALLMARK_NOTCH_SIGNALING'], 
             samples=c('Lung5_Rep1_fov_2', 'Lung5_Rep1_fov_6', 'Lung5_Rep1_fov_11', 'Lung6_fov_4', 'Lung6_fov_6', 'Lung6_fov_7'),
             color_pal='YlOrBr')

ggpubr::ggarrange(plotlist=qp, ncol=3, nrow=2, common.legend=T)
```

# Domain plotting -- downstream of STclust

```{r plot_domains, fig.width=12}
dom_p <- STplot(lung_subset, ks='dtc', ws=0.02, deepSplit=F,
                color_pal='discreterainbow')

ggpubr::ggarrange(dom_p$Lung5_Rep1_fov_2_stclust_spw0.02_dsplFalse,
                  ti$image_Lung5_Rep1_fov_2,
                  dom_p$Lung5_Rep1_fov_6_stclust_spw0.02_dsplFalse,
                  ti$image_Lung5_Rep1_fov_6,
                  dom_p$Lung5_Rep1_fov_11_stclust_spw0.02_dsplFalse,
                  ti$image_Lung5_Rep1_fov_11,
                  dom_p$Lung6_fov_4_stclust_spw0.02_dsplFalse,
                  ti$image_Lung6_fov_4,
                  dom_p$Lung6_fov_6_stclust_spw0.02_dsplFalse,
                  ti$image_Lung6_fov_6,
                  dom_p$Lung6_fov_7_stclust_spw0.02_dsplFalse,
                  ti$image_Lung6_fov_7,
                  ncol=4, nrow=3)

# If no tissue images are available:
# ggpubr::ggarrange(plotlist=dom_p, ncol=3, nrow=2)
```

# Genes showing spatial gradients - downstream of STgradient

```{r stg_plots}
qp2 <- STplot(lung_subset, genes=c('KRT6A', 'HLA-B'), samples='Lung6_fov_4', color_pal='YlOrBr')
ggpubr::ggarrange(plotlist=qp2, common.legend=T)
```


# Arrange Plots params -- Good for all

```{r genequilt_chunk2, fig.align='center'}
ggpubr::ggarrange(plotlist=quilts1, nrow=1, ncol=2, legend='bottom')
```

# Other plots

SThet_compare <- SThet
STdiff_volcano <- STdiff (TBD)
distribution_plots <- Preprocessing
barplot with spatial pattern <- STenrich
plot_image <- STclust