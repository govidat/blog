+++
date = "2017-07-17T17:18:50+05:30"
draft = false
title = "Blockchain basics - Byzantine fault tolerance"

+++


![BFT](/blog/img/image13.png)  
Source: [BFT paper](https://www.microsoft.com/en-us/research/publication/byzantine-generals-problem/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Flamport%2Fpubs%2Fbyz.pdf)

In a permission less blockchain, all the nodes have equal rights. There is a consensus process to make it a trusted network.  
- Does it mean that all participants are trust worthy?    
- What happens to the network, if a few participants are bad elements (either maliciously or due to connection issues)?

Answer lies in the well researched Byzantine fault tolerance and this article is to touch on few basics. 

## Byzantine fault tolerance 

As per [wiki:](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance#Byzantine_Generals.27_Problem)    
“A Byzantine fault is any fault presenting different symptoms to different observers. A Byzantine failure is the loss of a system service due to a Byzantine fault in systems that require consensus.”  

Byzantine fault tolerance is to be able to defend against such failures - say a few bad elements in a permission less blockchain like bitcoin.   
Byzantine refers to the Byzantines General’s problem as explained in this 1982 paper by [Leslie Lamport, Robert Shostak and Marshall Pease.](https://www.microsoft.com/en-us/research/publication/byzantine-generals-problem/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Flamport%2Fpubs%2Fbyz.pdf) 
 

## Byzantine Generals Problem 

As per [wiki:](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance#Byzantine_Generals.27_Problem):  
“The Byzantine Generals Problem is with a group of generals, each commanding a portion of the Byzantine army, encircle a city. These generals wish to formulate a plan for attacking the city. In its simplest form, the generals must only decide whether to attack or retreat. Some generals may prefer to attack, while others prefer to retreat. The important thing is that every general agrees on a common decision, for a halfhearted attack by a few generals would become a rout and be worse than a coordinated attack or a coordinated retreat.”

![BFT](/blog/img/image14.png)    
Source: [BFT paper](https://www.microsoft.com/en-us/research/publication/byzantine-generals-problem/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Flamport%2Fpubs%2Fbyz.pdf)

“The problem is complicated by the presence of traitorous generals who may not only cast a vote for a suboptimal strategy, they may do so selectively. For instance, if nine generals are voting, four of whom support attacking while four others are in favor of retreat, the ninth general may send a vote of retreat to those generals in favor of retreat, and a vote of attack to the rest. Those who received a retreat vote from the ninth general will retreat, while the rest will attack (which may not go well for the attackers). The problem is complicated further by the generals being physically separated and having to send their votes via messengers who may fail to deliver votes or may forge false votes.”  

![BFT](/blog/img/image15.png)    
Source: [BFT paper](https://www.microsoft.com/en-us/research/publication/byzantine-generals-problem/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Flamport%2Fpubs%2Fbyz.pdf)



The typical mapping of this story onto blockchain is that the network nodes are the generals and their digital communication system links are the messengers.


In the paper referred above, several solutions have been proposed.  

## Permissionless blockchain - Bitcoin  
Bitcoin has successfully overcome the BFT problem by using “Proof-of-Work” or “mining”.  
Proof-of-Work involves scanning for a value (nonce) that when hashed, the (block) hash begins with a specific number of zero bits.  

![BFT](/blog/img/image16.png)  
Source: [Bitcoin paper](https://bitcoin.org/bitcoin.pdf)  

For example if we have a few transactions in a block, the hash value without the nonce is as below:
![Block hash](/blog/img/image17.png)  
Source: [anders](https://anders.com/blockchain/hash.html)  

Assuming Proof-of-work needs that the resultant hash must start with 0000. We now need to find a nonce value that would satisfy this condition. After trying many combinations, we find that a nonce value of “67068” makes the hash value of the block start with “0000”.   
![Block hash](/blog/img/image18.png)  
Source: [anders](https://anders.com/blockchain/hash.html)  

This process of finding the nonce value is “mining” and the first miner gets rewarded with bitcoins.  

However, this process consumes enormous power for just finding a random number!

## Permissioned blockchains 

Permission blockchains like Hyperledger fabric have different and more energy efficient algorithms for overcoming the Byzantine Generals Problem. 


### Related articles

[Blockchain basics](https://www.linkedin.com/pulse/blockchain-basics-business-govindarajan-r)  
[Blockchain basics - cryptography](https://www.linkedin.com/pulse/cryptography-basics-blockchain-govindarajan-r)  
[Blockchain basics - Merkle tree](https://www.linkedin.com/pulse/blockchain-basics-merkle-tree-govindarajan-r)  
