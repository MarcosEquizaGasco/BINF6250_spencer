# Introduction
This project implements the viterbi algorithm given an HMM model. The viterbi algorithm finds the optimal path of hidden states given a sequence of observations. 

# Pseudocode
Put pseudocode in this box:

```

Class HMM(emission_prob, transition_prob, initial_prob):

    FUNCTION viterbi(self, observations):
    
    INITIALIZATION: start with initialization of probabilities for each state for each observation
    initialize two matrices, probability matrix and move matrix 
    first column of probability matrix:
        for each state: 
            initial probability of state k * emission probability for observation 0 in state k

    RECURSION: 
        For each remaining observation: 
            for each possible state:
                previous probability for preceding state  * transition probability * emission probability
                take max value after all states are iterated through
                store state that contributed to max value
                return score matrix, move matrix, max of last column (or Termination function)
                
    TERMINATION:
        after all observations are iterated through
        Take max from last column and begin traceback
    
    TRACEBACK:
        take state contributing to max of last column
        add to state path list 
        move one back in the matrix and look at cell in corresponding state row
        get state contributing to max in new cell
        add to state path list
        move one back in matrix and look at cell in corresponding state row
        repeat for all observations
        reverse list of state path
        return state path list (final output)

    return output from traceback
```

# Successes
There were a few key successes for this weeks project. We felt confident in our use of object oriented programming and we feel aptly set up to continue to build upon the objects we have created. Another highlight is the group work itself, we were able meet and discuss the algorithm conceptually, plan, and implement in an efficient manner. We ended up with a implementation we feel confident in moving forward with. 

# Struggles
We initially struggled with the structure, or lack thereof, for this project. Setting up a notebook, and tackling this algorithm starting with nothing but our conceptual understanding required some teamwork and open discussion. 

# Personal Reflections
## Group Leader
Spencer: I enjoyed this project, having no set structure and guidance as I think it emphasized the need for teamwork and made us leverage the skills we already have. I am looking forward to the following weeks working with Marcos and Sneha!

## Other member
Sneha: Spencer and Marcos are both great partners and it was easy to meet and plan our implementation. We spent a good amount of time on the planning stage to make sure we understood each step of the algorithm and the scope of each of our functions. I think the most difficult concept for me was the traceback, specifically keeping track of the indices and mentally tracking that i and the actual matrix column are always one apart. It was also a bit intimidating at first not having a structured notebook and making sure that our code was implemented in such a way that we could add on to it in the next few weeks, but I think our group handled that well in planning. 

# Generative AI Appendix
As per the syllabus
