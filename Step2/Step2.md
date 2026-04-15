# Step 2: Sorting and Indexing with samtools

You should now see trimmed.bam alongside your other files. Before we can proceed to the variant calling step, we'll need to sort and index the trimmed file. To do this, we'll have to run samtools sort on our newly created trimmed.bam. Name the output of this command trimmed.sorted.bam. (Note: if you see the output fill with random characters, try redirecting the output to a file using >)

`samtools sort trimmed.bam -o trimmed.sorted.bam`

Now, we'll need to index the sorted BAM file. To do this, we'll have to run samtools index on our newly created trimmed.sorted.bam.

`samtools index trimmed.sorted.bam`

Now, we're ready to proceed to the variant calling step.