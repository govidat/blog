+++
date = "2017-06-30T12:32:48+05:30"
draft = true
title = "bitcoin basics"

+++

![Bitcoin](/blog/img/image4.png)
Source: https://bitcoin.org/bitcoin.pdf

Bitcoin is a leading crypto currency and the origin is in the paper of Satoshi Nakamoto. 

The real identity of Satoshi Nakamoto is still not known. There are many valid reasons that it will never be known. Bitcoin is built on blockchain technology and has helped in generating world wide interest in this emerging technology. This article attempts to simplify some parts or terms used in the bitcoin paper.
The content within quotes is a reproduction from the Paper referred above.

## Abstract:

Bitcoin is an electronic cash sent directly from peer to peer in a network of participants. Thus it is a permission less blockchain and anyone can be part of this network. The transactions are trusted and there is no need of an intermediary institution to bring about this trust. (No need of any intermediary like Bank to transfer this cash). In electronic cash, there is a possibility of double spend. Bitcoin provides a solution by hashing them into a chain of transactions which are time stamped and have a proof-of-work. Miners perform the proof-of-work and add blocks to the chain. The longest chain of blocks is accepted by the network as final. Such a network is explained in byzantine general problem. Simply put, a few participants can be rogues who can gain by corrupting the chain. As long as the majority of the CPU power of the network is non-corrupt, they can outpace attackers. 

## SHA-256

SHA-2 (Secure Hash Algorithm) is a set of cryptographic hash functions designed by USA NSA. 

Hashing is a one way function. For any input it mathematically converts to a standard sized output. It is one way, meaning, from the output value one cannot get the input value. At the same time it is easy to verify as, for a given input the output will be the same all the time. 

For e.g. 
The hex value using SHA-256 using an online convertor http://hash.online-convert.com/sha256-generator:

“Hello” = 185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969

For a small change in inout the hash value changes a lot:
“Hello.”= 2d8bd7d9bb5f85ba643f0110d50cb506a1fe439e769a22503193ea6046bb87f7

Once an output hash is given, we can easily verify if the input value has gone for any change. 
In a more practical scenario, it is like participating in a tender and all bidders provide a sealed cover of their financial bid. Instead they can as well give the hash value of the soft copy of their bid. Later, like opening the tender, they can provide the full soft copy to the purchaser. Purchaser can easily verify if the soft copy is the same without any alteration, by just checking if the hash of this soft copy matchesches the previous hash value. 

Irrespective of the input size of the file, the hash will produce a fixed length output hash. 


  

 



