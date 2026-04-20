# Step 5: Freyja Aggregation

You'll see the results from the last steps in the `demix` directory here. Before we're ready to plot our data, we'll need to combine the `demixed` files into one aggregate file that the plotting command can accept.

To do this, we'll run the following command:
`freyja aggregate demix/ --output aggregated_results.tsv`

Let's break that down:
- `demix/` is a positional argument specifying the directory with all our demix results
- `--output aggregated_results.tsv` names the resulting output file

Go ahead and take a look at `aggregated_results.tsv` using your file browser. You'll notice that the relative abundances of each sample is listed on each row.

When you're ready, go ahead and `cd ../Step6`