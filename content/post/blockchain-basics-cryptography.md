+++
date = "2017-07-02T10:16:20+05:30"
draft = false
title = "Blockchain basics - cryptography"

+++

![Bitcoin](/blog/img/image4.png)
Source: [Bitcoin paper](https://bitcoin.org/bitcoin.pdf)

A blockchain database is immutable and is cryptographically protected. 

This article is on few very basic aspects of cryptography.

## SHA-256

SHA-2 (Secure Hash Algorithm) is a set of cryptographic hash functions designed by United States NSA. 

Key aspects of a hash function are :

- It is a one way function. From a known output value one cannot derive the input value.
	
- It mathematically converts the input to a standard sized output.
	
- It is easy to verify. For a given input the output will be the same, all the time.

- A small change to the input will change the output significantly.
				
For e.g. 
The hex value using SHA-256 using any [online convertor](http://hash.online-convert.com/sha256-generator) for 

### “Hello” 

185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969

For a small change in input the hash value changes a lot:

### “Hello.”

2d8bd7d9bb5f85ba643f0110d50cb506a1fe439e769a22503193ea6046bb87f7

In a related scenario like businesses tenders, all bidders provide a sealed cover of their financial bid. Instead, they can as well give the hash value of the soft copy of their bid. Like a sealed cover, nothing can be extracted from the hash value and the content remains undisclosed. Later, like opening the tender, the bidder can reveal the soft copy document. Others can easily verify that soft copy has not been altered, by just checking if the hash of this soft copy matches the previous hash value. 

A simple use case of this one way function is used in securing our passwords by better secured websites. They store the **hash of our password** in their system. When user signs in with password, the website hashes the input and compares with the password hash stored in their system. Thus, even if their systems are hacked, only our useless password hash leaks. This is the reason, *forgot password* option in these sites only allows us to reset the password and never provides our old password.

In another use case, hash is used to filter spams in our email. Our email header consists of a hash of some header contents of our email. At the senders end, this hash is calculated and included in the email header. Any calculation takes some effort and a spammer avoids this calculation. For a normal sender and receiver the hash calculation and verification effort is imperceptible. 

## Block hash

In blockchain the transactions are stored in a block. This block of transactions can be passed through a hashing algorithm like SHA-256 and we will get a hash. 
For e.g.: 
![Block hash](/blog/img/image5.png)  
[Source](https://anders.com/blockchain/hash.html)

Now this block includes the hash value in its header. 

![Block hash](/blog/img/image6.png)

In a blockchain, the database is distributed and every participant has a copy of this block. They can easily verify if the hash of the transactions in a block matches with the header.

## Linking the blocks

In blockchain, once a block is made, the hash header of this block is passed on to the next block as an input. 
![Linked blocks](/blog/img/image7.png)

With this link, in a blockchain, if any transaction is altered or corrupted, then the hash of that block will change. Since this hash is an input to the next block, the hash of the next block also changes and so on. Thus all the blocks, subsequent to the changed block will be corrupted and this is easily verifiable by others. 

There is still a possibility of all future block hashes also reconstructed by a bad element. That is a separate discussion topic. 


## Keys for digital signatures

![Keys](/blog/img/image8.png)  
Source: [Wiki](https://en.wikipedia.org/wiki/Public-key_cryptography)  

A digital signature is the equivalent of a physical signature and it needs to meet two important requirements.  
1. Authentication : Only the holder of the signature could sign that way and others can easily verify the signatory and  
2. The signature cannot be copied by others

In the public key cryptography, using mathematical functions, a program generates a Private/Secret Key and a corresponding pair of Public Key.  

Few of the properties of this cryptographic function are:  
1.  Sign/ Encrypt a document / message with this Secret Key ; Sign = (message + Secret Key)  
2.  Any one with the corresponding Public Key can verify/ decrypt ; Derive message with (Sign + public key)

The first requirement of authentication is immediately satisfied. Sign includes the message + Secret Key. Hence only the owner of the Secret Key alone can sign any message / documents. Even if the corresponding Public keys are shared, the same can only be used to verify/ decrypt and not to Sign. Thus this digital signature cannot be copied by others.  
[Source:](http://bitcoinbook.cs.princeton.edu) 

## Public Key as identity

In another way, a public key acts as ones identity. One can just provide their public key to others and they can easily verify the signed messages. One can remain anonymous by generating as many combinations of the private/secret key and their corresponding public key. 

In the bitcoin world, all the transactions are publicly available and one can see only the public keys.

Also this combination of private/secret key and their corresponding public key cannot be forged or hacked. Blockchain transactions have this signing process and thus they give a finality to the transactions. 

### Related articles

[Blockchain basics](https://www.linkedin.com/pulse/blockchain-basics-business-govindarajan-r)  
[Blockchain basics - Merkle tree](https://www.linkedin.com/pulse/blockchain-basics-merkle-tree-govindarajan-r)  


