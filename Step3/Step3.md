# Step 3: Variant Calling

We're now ready to call variants in our sample! `ivar variants` calls SNPs, insertions, and deletions in our sample. It also saves coverage depth information which will be important later when we run freyja demix.

Run the following command to call variants:

`samtools mpileup -aa -A -d 600000 -Q 20 -q 0 -B -f NC_063383.1.fasta trimmed.sorted.bam | tee >(cut -f1-4 > depths.tsv) | ivar variants -p variants.tsv -q 20 -t 0.0 -r NC_063383.1.fasta`

There's a lot to unpack here, so let's break it down step by step. ivar variants requries that you pipe in (|) the output of samtools mpileup into ivar variants. The tee command saves the first four columns of the samtools mpileup output to the file depths.tsv. Finally, ivar variants calls variants from the piped input, using our reference genome. If you're curious about the other arguments, you can run ivar variants --help to see the full list of options.

You should see variants.tsv and depths.tsv in your Step3 directory. Let's take a look at the variants file first using the file explorer.

You'll see columns corresponding to REF, ALT, and POS.

- POS is the position of the mutation
- REF is the reference allele
- ALT is the alternate allele

You'll also notice that some entries in ALT contain + or - characters. These correspond to insertions and deletions, respectively.

Now, let's take a look at the depth file:
Here, the columns correspond to the position, reference base, and the depth of coverage at that position. However, it looks like the depth is 0 for these positions. This is because we're only looking at the first 10 positions in the genome, which aren't covered by our sample.

Let's use head and tail to see the depth of coverage for a region that's covered by our amplicon scheme.

`head -n 111040 depths.tsv | tail -n 20`

Now, on to de-mixing with Freyja!
