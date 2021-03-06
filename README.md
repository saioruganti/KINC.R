![KINC logo](KINClogo.png)

# KINC.R

The KINC.R package provides supplementary R functions to assist with analysis of files used and generated by [KINC] (https://github.com/SystemsGenetics/KINC).  An important function is the RMT() function which perform Random Matrix Theory (RMT) analysis of a network.

## Installation

Clone this repository and start R in the cloned directory:
```
library('devtools')
install()
```

Now you can use KINC.R in R by importing the library:
```
library('KINC.R')
```

## Examples

While KINC has been written for gene co-expression networks, the RMT function can be used with any similarity matrix.  The matrix must be in a data frame with at least three columns named: Source, Target and Similarity.  The Source and Target columns indicate the edge in the network and the Similarity contains the similarity score.  The RMT() function will perform RMT analysis on a similarity matrix that it constructs from the network file.

### Example 1 -- RMT of Traditional KINC network

Below is an example from traditional KINC networks:

``` R
library('KINC.R')

# Import the network from a file.
colNames = c('Source', 'Target', 'Similarity', 'interaction')
colClasses = c('character', 'character', 'numeric', 'character')
net = read.table("KINC_traditional_net.txt",
  header=TRUE, sep="\t", colClasses=colClasses, col.names=colNames)

# Now perform RMT analysis on the loaded network
RMT(net)
```

In this example, the network file being read from a file was generated using the traditional KINC method and is named `KINC_traditional_net.txt`. It is tab-delimited and has four columns: source, target, similarity score and interaction type.

### Example 2 -- RMT of Clustered KINC Network

``` R
library('KINC.R')

# Import the network from a file.
net = loadNetwork('KINC_clustered_net.txt')

# Now perform RMT analysis on the loaded network
RMT(net)
```
