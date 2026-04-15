# Step 4: Freyja Demixing
We're now ready to recover the individual mpox lineages that make up our sample. Freyja does this by using lineage-specific "barcodes" that match mutations to known to known mpox lineages based on the depth of coverage at each mutation site.

In your workspace, you'll see the variants (`.tsv`) and depth (`.depth`) files for 5 Mpox samples.

Your goal is to run `freyja demix` on all these samples. First however, we need to update the barcode set for the pathogen we're analyzing here. In this case, since we're looking at Mpox samples, we run the command:

`freyja update --pathogen MPX`

After a few seconds, you should have the latest barcode set for Mpox. Now, go ahead and run:

`freyja demix variants-output/reads0.tsv variants-output/reads0.depth --pathogen MPX --output demix/reads0.demixed`

Here, we specify the pathogen we're analyzing using the `--pathogen` flag. (See "https://github.com/bochen-lab/Freyja/blob/main/docs/pathogens.md" for a list of supported pathogens), and the input files for the variants and depths files as positional arguments.

This will create a `reads0.demixed` in `Step1/demix`. Go ahead and open the file using the file browser.

You should see: You'll see the rows `lineages` and `abundances`. These contain the lineages detected in the sample, along with their relative abundances. In addition, the `resid` row indicates the residual of the solving step (lower is better). Finally, `coverage` shows the percentage of the genome that is covered in the sample by 10 or more reads. In this case, our coverage is 3.1%, which is relatively low. This is due to the fact that the primer scheme we're using only targets selected informative regions of the genome, and since Mpox has such a large genome, we don't see coverage outside of these informative sites.

## Your goal

Run `freyja demix` on all the remaining samples in the same way, saving the outputs to `Step4/demix`
