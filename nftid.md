# IAMX X NFT MAKER X SELENE SYSTEMS IDENTIFICATION Specification Draft v0.1

# Abstract

This CIP proposes a solution to the issue of verifying Cardano NFT projects.


# Motivation

Bad actors are currently one of the biggest threats to the NFT space, with scams ranging from convincing victims to send ADA to a false address to stealing art for minting - this is something that we must work hard to stop. To do this, we plan to introduce a form of ‘trust score’ for every user on the platform. The initial metrics for which will be rated by two data points; their level of identification and their level of Stake.

For the most common NFT aftermarket scams, there are currently two main attack vectors:

**Fake** - List an NFT with an unverified POLICY ID and then use names and other metadata to make it appear like the real project with the hope that the lack of verification goes unnoticed.

**Man in middle** - Get a fake project verified (similar to getting an SSL Cert for a fake website), the idea being that people will then see the verification and not check that it is actually the correct project. Think of this like getting an SSL Cert for “G00GLE”, the padlock appears, as it really is G00GLE, but G00GLE is not GOOGLE.


The main protection against these attack vectors so far has been the verification process, the idea being that secondary markets can build up a database of POLICY ID’s (with corresponding projects) and then the default for the user is to only see verified projects. Verifying projects is on the surface, nothing more than matching up a unique POLICY ID with its respective creator, which, once complete, allows the aftermarket to show the potential buyers all of the related information and proof of that being the real project that the buyer is looking for.

Although the process for doing this so far has been accurate, it has relied on a handful of dedicated, centralised adjudicators which has resulted in delays and does not fully align with the decentralisation we all want to create.


# Specification and Rationale

Before we attempt to explain how this CIP will solve identity for the purpose of verifying NFTs, we need to first look at how it solves the identity problem for people and businesses.

# Key principles
* Public Key Encyption
* One-Way Processes
* Conceptually similar to SSL Certificate Authorities
* Layering

# Getting onboarded

The onboarding process is the initial step that people/businesses must take to create the first attributes in their **Master Record**
There are several methods by which a user can create thier initial verification

* Visiting an IAMX Kiosk
* Using the IAMX App
* Utilising the database of an exisiting company -> Physical letter with QR Code/2FA


# The Master Record

For every attribute that a user proves is true about themselves, this is signed by a trusted authority's private key and the resulting checksum is stored in the users Master Record.

The users Master Record is stored on the users device -> heavily encrypted.

The clear text mappings of these attributes are never stored anywhere.


# Standardisation based on use cases

Conceptually, having this master DID file stored on the users device allows us perform runtime based subset DID's, based on the specific use case.
These Subset DIDs are NFTs minted to the Cardano Blockchain.

These can range from the simple downloads (requiring only your age),to mortgage applications or crypto exchange KYC (which require far more attributes).


# From an end user point of view

Lets take an example, I want to purchase some alcohol online.
I already have verified my name and address (needed for shipping).
By verified, I mean the "Getting Onboarded" phase has been completed for these attributes.

But I have not yet verified my DOB, thus I cannot prove my age yet to buy the alchol.

I can then use the App to follow a process similar to KYC, whereby I would show my passport, my face and then app would confirm that the passport is real, the DOB I have entered matches the passport and thus would sign the attribute and add it to the Master Record.

I then return to the website where I want to make the purchase, enter my details as normal into the form.
In additional to this, I also use the Master Record, to generate a subset DID for the specific use case of an online age verified purchase, which will pull all of the relevant Checksums for these attributes and mint them as an NFT.

The online store can then run the one-way checksum process on each attribute, to verify that they do match.

So essentially, for each value the user submits both:
* The cleartext value
* The corresponding checksum result

Notice here how the process is more about confirming that the information the user has inputted is actually their information.
The user still needs to enter it in cleartext for the shopping website to process, but the DID generated from the Master Record is used to confirm the information is correct.

# Using this for NFT Verification

## There are 3 scenarios in which we would need to implement this

- Brand New Project, Yet to mint and with an Open Policy
- A project that has already minted, but does have an Open Policy
    - (Backwards compatibility)
- A project that has already minted and the Policy has closed
    - (Backwards compatibility)


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

