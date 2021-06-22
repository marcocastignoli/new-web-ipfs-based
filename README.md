# New web IPFS based
## Imagining a new web based on IPFS

### Introduction

A while ago I proposed Nile, a decentralised and commission-free shopping platform to empower local economies. I imagined an architecture of the system that combines centralized, decentralized and federated parts. https://nile.shopping

I would love to share this architecture with you to receive feedback and, if feasibile, build a framework to help other people building another app based on the same idea.

### Objective

The final goal is to make the internet a better place, these are the main topics:
1) Privacy: storing private informations only on the owner device
2) Low costs: allow low cost internet infrastructures.
3) Local: take advantage of the pros of a metropolitan area network, content near to you is delivered faster
4) Robust and easy: use just web technologies and IPFS, no blockchain involved means no new things to learn to the final user and no speculation on cryptos

### Architecture

The classic architecture CLIENT-SERVER becomes CLIENT-NODE-INSTANCE-REPOSITORY. An application based on this architecture has several client, nodes, instances but has only one repository.
* Repository: is the IPFS endpoint of the application where all the static contents are stored.
  * The repository is a key-value file published on IPFS that lists all the instances in the system and their IPFS hash.
  * Each instance IPFS hash points to a key-value file published on IPFS that lists all the nodes in the instance and their IPFS hash
  * Each node IPFS hash points to a file published on IPFS that contains the node content
* Instances are webservices distributed around the world that create a federation and act as a relay when direct p2p communication between nodes and clients is impossible. Each instance is connected to a set of local nodes.
* Nodes are the content creators of the application (e.g. in the case of Nile, nodes are the shops). Nodes can be browser based (they are active only when the webpage in which are loaded is open) or server based (they are always running). Nodes publish their static content on IPFS and accept p2p communications from the client
* The clients navigate the IPFS content starting from the repository, inside the repository are stored the p2p addresses of the nodes, so the client can contact them directly

### User Experience

The final user use the client as an app that browse the repository on IPFS and present the content as a normal centralized application. When the user talks to a node a direct p2p communication is created or the instance is used as a relay (communication is E2E-Encrypted).
