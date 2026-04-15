# Step 3: Visualize lineage abundances with freyja plot

Now, we're ready to plot the relative lineage abundances of our samples over time. First, we'll need some information about how the samples were collected so that we can view them properly.

Take a look at `sample_metadata.csv`. This file contains useful sample information, including collection date, and viral load.

Let's try plotting the aggregated data using `freyja plot`:

`freyja plot aggregate_data.tsv --lineages --mincov 2 --times sample_metadata.csv --output mpx_plot.png`

- `aggregate_data.tsv ` contains the lineage abundance info for our samples.
- `--lineages` tells the plotting function to show individual lineages instead of WHO categories
- `--mincov 2` filters out samples with less than 2% coverage
- `--times` specifies the sample metadata file
- `--output` saves plot to a specific filename + format

Go ahead and open `mpx_plot.png` using your file browser. What do you see?