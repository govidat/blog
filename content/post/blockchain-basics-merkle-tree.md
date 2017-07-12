+++
date = "2017-07-12T15:04:19+05:30"
draft = false
title = "Blockchain basics - Merkle tree"

+++

![Merkle tree](/blog/img/image9.png)  


All the transactions that ever happened in a bitcoin are stored in the distributed database.   
- Does it mean that a participant has to manage a very large database? 
- Does it mean that to verify if a transaction is valid, one has to process all the data from the very beginning?

Answer lies in Merkle tree and this article is to touch on few basics. 

## Merkle tree

In cryptography and computer science, a hash tree or Merkle tree is a tree in which every non-leaf node is labelled with the hash of the labels or values (in case of leaves) of its child nodes. [wiki kink](https://en.wikipedia.org/wiki/Merkle_tree)  

In the above diagram, the transactions are at the leaf level. Hash of two transactions (Tx0 and Tx1) are again hashed and a non-leaf node of Hash01 is formed. Similarly Hash23, Hash45 etc are formed. A tree is formed and at the top of the tree is the Top Hash or the Root Hash. 

In bitcoin the Block header contains this Root as Merkle Root. 

![Merkle root](/blog/img/image10.png)  
Source: [Bitcoin paper](https://bitcoin.org/bitcoin.pdf)

With this design, they have greatly reduced the size of the blocks that are required for a transaction user. 

As mentioned in the paper - “A block header with no transactions would be about 80 bytes. If we suppose blocks are generated every 10 minutes, 80 bytes * 6 * 24 * 365 = 4.2MB per year. With computer systems typically selling with 2GB of RAM as of 2008, and Moore's Law predicting current growth of 1.2GB per year, storage should not be a problem even if the block headers must be kept in memory.”

## Verification simplicity

To verify that a transaction is part of a block )or a hash tree), one needs the specific transaction details and just the hash values of the higher level non branches.

![Verification](/blog/img/image11.png)

To verify that Tx0 is in the block, one needs the details of 
- Tx0   
- Hash1 and 
- Hash23  
With this one can quickly recalculate Root Hash and verify that Tx0 is part of this block.

Mathematical explanation as per Wiki:    
“Demonstrating that a leaf node is a part of the given hash tree requires processing an amount of data proportional to the logarithm of the number of nodes of the tree.”

## Reclaiming Disk Space

In the bitcoin world, the spent transactions can be discarded to save space. Merkle tree enables this without breaking the block’s hash. The image below shows the pruning after removing Tx0, Tx1 and Tx2. 

![Pruning](/blog/img/image12.png)  
Source: [Bitcoin paper](https://bitcoin.org/bitcoin.pdf)  

### Related article

Blockchain basics : [github](https://govidat.github.io/blog/post/blockchain-basics/) [Linkedin](https://www.linkedin.com/pulse/blockchain-basics-business-govindarajan-r)  
Blockchain basics - cryptography : [github](https://govidat.github.io/blog/post/blockchain-basics-cryptography/) [Linkedin](https://www.linkedin.com/pulse/cryptography-basics-blockchain-govindarajan-r)  

