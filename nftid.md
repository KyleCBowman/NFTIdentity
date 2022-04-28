# IAMX X NFT MAKER X SELENE SYSTEMS IDENTIFICATION Specification Draft v0.1

# Overview

This is a draft document

# Explanation

Before we attempt to explain how this will solve identity for the prupose of verifying NFTs, we need to first look at how it solves the identity problem for people businesses

# Key principles
* Public Key Encyption
* One-Way Processes
* Conceptually similar to SSL Certificate Authorities
* Layering

# Getting onboarded

There are several methods by which a user can create thier initial verification

* Kiosk
* App
* Database of exisiting company -> Physical letter with QR Code/2FA


# The Master Record

For every attribute that a user proves, this is signed by a trusted authority's private key and the resulting checksum is stored in the users Master Record.

The clear text mappings of these attributes are never stored anywhere.


# Standardisation based on use cases

Conceptually, having this master DID file stored on the users device allows us perform runtime based subset DID's, based on the specific use case.
These Subset DIDs are NFTs minted to the Cardano Blockchain.

These can range from the simple downloads (requiring only your age)

To mortgage applications (which require your Date of Birth,


# From an end user point of view

Lets take an example, I want to purchase some alcohol online.
I already have confirmed my name and address (needed for shipping).
By confirmed, I mean the "Getting Onboarded" phase has been completed for these attributes

But I have not yet confirmed my DOB, thus I cannot prove my age yet to buy the alchol.

I can then use the App to follow a process similar to KYC, whereby I would show my passport, my face and then app would confirm that the passport is real, the DOB I have entered matches the passport and thus would sign the attribute and add it to the Master Record.

I then return to the website where I want to make the purchase, enter my details as normal into the form.
In additional to this, I also use the Master Record, to generate a subset DID for the specific use case of an online age verified purchase, which will pull all of the relevant Checksums for these attributes and mint them as an NFT.

The online store can then run the one-way checksum process on each attribute, to verify that they do match.

So essentially, for each value the user submits both:
* The Cleartext value
* The corresponding checksum result

Notice here how the process is more about confirming that the information the user has inputted is actually their information.
This is confirmed because they have submitted


# Using this for NFT Verification

## There are 3 scenarios in which we would need to implement this

* Brand New Project, Yet to mint and with an Open Policy
* A project that has already minted, but does have an Open Policy
* A project that has already minted and the Policy has closed


## New Projects
As with all new standards, they tend to be easiest to implement on new instances.
In this case, all new projects have the option to set this up in the optimal format, whereby the DID is included inside of each NFT.
Crucially, this NFT will be signed by a trusted party such as NFT Maker or IAMX.

## Minted, with currently Open Policy
With the PolicyID still open, we are able to mint another NFT under that Policy and gain the inherint proof of authenticity through it.
We can therefore use this opportunity to mint a single new NFT containing the DID information for that collection.
Crucially, this NFT will be signed by a trusted party such as NFT Maker or IAMX.

## Minted, with a Closed Policy
In this case (as will be for many projects by now) the Policy is already closed.
This gives us more of a challenge as we can no longer point from inside the project, rather from the outside in.
To solve this, our solution wiuld be for the creator to maintain another Policy, specifically for the purpose of pointing



