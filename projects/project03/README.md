# Introduction
This project implements a Gibbs Sampling algorithm to identify DNA sequence motifs. The script uses a probabilistic Markov Chain Monte Carlo (MCMC) approach to iteratively find candidate motifs and converge on an enriched sequence pattern represented as a Position Frequency Matrix (PFM).
# Pseudocode
```
Import  libraries

Load BAM file
For each read in BAM file:
    Extract the read sequence
    Store the sequence in list "seqs"

Load genome FASTA file
Load GFF annotation file

Initialize an empty list "seqss"

For each sequence in FASTA:
    For each annotation entry in GFF:
        If annotation type is "CDS":
            Extract promoter sequence (50 bp upstream)
            If promoter contains "AGGAGG":
                Add promoter sequence to "seqss"

Print number of sequences in seqs and seqss

initialize_random_motif(seqs, k):

    Create an empty list motif_sequence_list

    For each sequence in seqs:
        Randomly choose start index between 0 and (length of sequence − k)
        Extract substring of length k starting at random index
        Add substring to motif_sequence_list

    Return motif_sequence_list

Function initialize_random_motif(seqs, k):

    Create empty list motif_sequence_list

    For each sequence in seqs:
        Randomly choose start index between 0 and (length of sequence − k)
        Extract substring of length k starting at random index
        Add substring to motif_sequence_list

    Return motif_sequence_list

select_new_motif(motif_list, seqs, k):

    Randomly choose one sequence index to omit
    Remove its motif from motif_list temporarily

    Build new PFM from remaining motifs
    Build new PWM from new PFM

    Initialize empty list scores

    For each possible k-mer position in omitted sequence:
        Extract forward k-mer
        Compute reverse complement k-mer

        Calculate PWM score for forward k-mer
        Calculate PWM score for reverse complement

        Add both scores to scores list

    Apply softmaxxing:
        For each score:
            Compute 2^score
        Divide each by total sum

    Randomly select new motif index using normalized probabilities

    If selected index corresponds to forward strand:
        Extract k-mer from original sequence
    Else:
        Extract reverse complement k-mer
        Update sequence to reverse complement

    Return omitted sequence index and new motif

GibbsMotifFinder(seqs, k, seed, max_iterations, ic_threshold, convergence_iterations):

    Set random seed

    Initialize motif_list using initialize_random_motif

    Build initial PFM from motif_list
    Build initial PWM
    Compute initial information content (IC)

    Set iteration counter i = 1
    Set convergence_counter = 0

    While i <= max_iterations:

        Call select_new_motif
        Update motif_list with returned motif

        Build new PFM
        Compute new IC

        Calculate absolute difference between new IC and current IC

        If difference < ic_threshold:
            Increment convergence_counter
        Else:
            Reset convergence_counter to 0

        If convergence_counter == convergence_iterations:
            Return new PFM

        Update current IC
        Increment iteration counter

    If max_iterations reached:
        Print "failed to converge"
        Return latest PFM
```

# Successes
Description of the team's learning points

# Struggles
Description of the stumbling blocks the team experienced

# Personal Reflections
## Group Leader
Group leader's reflection on the project

## Other member
Sneha- Spencer and Marcos were both great to work with. We were able to meet a handful of times throughout the two weeks to plan and implement our code rather than using a divide and conquer strategy. The planning phase was especially helpful to make sure we were all on the same page about what we had learned in class and what needed to be done for our project and specific functions.  

# Generative AI Appendix
As per the syllabus
