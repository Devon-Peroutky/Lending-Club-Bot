# Lending-Club-Bot

To accomplish the goal of finding the portfolio of loans on LendingClub with highest possible return::risk (set?), we will a
strategy involving a Genetic Algorithm and Linear Regression. For review, The basic process for a genetic algorithm is:

##Initialization
Create an initial population. This population is usually randomly generated and can be any desired size, from only a few individuals to thousands.

##Evaluation
Each member of the population is then evaluated and we calculate a 'fitness' for that individual. The fitness value is calculated by how well it fits with our desired requirements. These requirements could be simple, 'faster algorithms are better', or more complex, 'stronger materials are better but they shouldn't be too heavy'.

##Selection
We want to be constantly improving our populations overall fitness. Selection helps us to do this by discarding the bad designs and only keeping the best individuals in the population.  There are a few different selection methods but the basic idea is the same, make it more likely that fitter individuals will be selected for our next generation.

##Crossover
During crossover we create new individuals by combining aspects of our selected individuals. We can think of this as mimicking how sex works in nature. The hope is that by combining certain traits from two or more individuals we will create an even 'fitter' offspring which will inherit the best traits from each of it's parents.

##Mutation
We need to add a little bit randomness into our populations' genetics otherwise every combination of solutions we can create would be in our initial population. Mutation typically works by making very small changes at random to an individuals genome.

And repeat! - Now we have our next generation we can start again from step two until we reach a termination condition

##GA for Lending Club Approach
##Representation
To represent a Loan, we will use a Key->Value dictionary (probably doing this in Python). This makes the *Crossover* and *Mutation* simply - just swap the values of certain key between two loans. 

##Selection
For selection we will use the roulette wheel approach.

##Evaluation
The trickiest part is the *evaluation* step. We want to find which loans have the best risk::return ratios. To do so we must first project the risk of the loan (random forests, logistic regression, etc.). Once we have the probability of the loan defaulting, we can project the expected return (interest rate) from historial LendingClub data. Once we have a model of what sort of interest rate to expect, given projected risk, we have our evaluation function. 

```Fitness = (Expected Return - Actual Return)```
