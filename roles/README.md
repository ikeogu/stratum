<h1 align="center">
  Stratum Roles
</h1>

# Introduction

Roles in Stratum are knowns as Job Declarators (JDs), JDs are roles which can be Pool-side and Miner-side, but they can also be run by any third parties. They are connected to a Template Provider, in this way they are able to receive and validate custom block templates. They are the roles needed to implement the so called Job Declaration Protocol. They can further distribute jobs to a Mining Proxy (or Proxies) via the Job Distribution Protocol.

# List of Roles

1 Mining Devices or Miners
2 Pools
3 Proxies
    - Mining Proxy
    - Translation Proxy
4 Job Declarators
    - Job Declarator Server (JDS)
    - Job Declarator Client (JDC)


## Mining Devices or Miners

The term "miners" refers to the machines responsible for computing hashes. They come in various sizes and types, from large-scale corporate farms to smaller, decentralized setups. When discussing miners in relation to a pool, they are typically grouped based on how they communicate with the pool. For example, a mining farm with a hashing power of 10PH that communicates as a single unit with the pool is considered a single 'miner'. This is different from an individual operating a single S19 miner in their garage. Miners direct their hashing power towards a pool, as explained below. In Stratum v2, miners are considered the most downstream participants.

## Pools

Pools serve as intermediaries for coordinating hashing power and distributing mining rewards. They create tasks, validate blocks, and share them with the Bitcoin Network. Pools don't control hashing power but compete for it based on factors like latency and reliability. With Stratum v2, these factors can be significantly improved. Pools establish communication channels with downstream roles like Proxies or Mining Devices.

## Proxies

  Proxies are intermediaries between Miners and Pools that aggregate connections and translate mining communications from Sv1->Sv2 or Sv2->Sv1. Proxies may optionally provide additional functionality including monitoring services or job declaration optimizations. Both Miners and Pools can run Proxies, and they will do so for various reasons depending on the use-case. i

  in addition, there are 2 proxies here on Stratum they include the following :

  a. Mining Proxy  

    The Sv2 Mining Proxy functions as a bridge connecting mining devices and the Sv2 Pool. It gathers mining requests from various devices, combines them, and sends them to the Sv2 Pool. It can establish group/extended channels with the upstream (Sv2 Pool) and standard channels with the downstream (Sv2 Mining Devices).

  b. Translation Proxy

    The Translator Proxy facilitates communication between Sv1 Mining Devices and an Sv2 Pool or Mining Proxy. It allows Sv1 devices to interface with Sv2-based mining infrastructure, bridging the protocol gap between Sv1 and Sv2. The Translator Proxy can establish extended channels with the upstream (Sv2 Pool or Mining Proxy). For instance, a Pool may employ a Translator Proxy as its initial connection service to accommodate both Sv1 and Sv2 connections. This involves establishing direct standard channels with Sv2 miners and using the proxy to translate messages with Sv1 miners.

## Job Declarators

  Job Declarators (JDs) are roles which can be Pool-side and Miner-side, but they can also be run by any third parties. They are connected to a Template Provider, in this way they are able to receive and validate custom block templates. They are the roles needed to implement the so called Job Declaration Protocol. They can further distribute jobs to a Mining Proxy (or Proxies) via the Job Distribution Protocol. The Job declaration role can be futherly seen in the phases below.

  a. Job Declarator Server (JDS):
    Job Declarator Server (JDS) are roles which can be Pool-side and Miner-side, but they can also be run by any third parties. They are connected to a Template Provider, in this way they are able to receive and validate custom block templates. They are the roles needed to implement the so called Job Declaration Protocol. They can further distribute jobs to a Mining Proxy (or Proxies) via the Job Distribution Protocol.

  b. Job Declarator Client (JDC):
    Job Declarator Client (or JDC) is the role which is Miner-side, in charge of creating new mining jobs from the templates received by the Template Provider to which it is connected. It declares custom jobs to the JDS, in order to start working on them. JDC is also responsible for putting in action the Pool-fallback mechanism, automatically switching to backup Pools in case of declared custom jobs refused by JDS (which is Pool side). As a solution of last-resort, it is able to switch to Solo Mining until new safe Pools appear in the market.


