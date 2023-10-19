# Introduction

Magma is an open-source software platform that gives network operators an open, flexible and extendable mobile core network solution. Magma enables better connectivity by:

- Unlocking operator freedom with an open-source core network for cellular service.
- Enhancing network management with automation, improved uptime, predictability, and agility.
- Facilitating collaboration between MNOs and new providers for rural expansion.
- Expanding capacity and reach for operators with Wi-Fi and CBRS, especially in licensed spectrum-constrained areas.

## Magma Architecture
The figure below shows the high-level Magma architecture. Magma is designed to be 3GPP generation and access network (cellular or WiFi) agnostic. It can flexibly support a radio access network with minimal development and deployment effort.

Magma has three major components:

- Access Gateway (AGW)
- Orchestrator
- Federation Gateway

**Access Gateway (AGW):** This component serves as the heart of the network, providing network services, policy enforcement, and implementing LTE's evolved packet core. It can work seamlessly with existing radio hardware.

**Orchestrator:** The Orchestrator is a cloud-based service that simplifies network configuration and monitoring. It ensures network security and allows for easy monitoring of wireless network analytics and traffic flows through the Magma web UI.

**Federation Gateway:** This component acts as a bridge between the MNO's core network and Magma. It utilizes standard 3GPP interfaces to integrate with existing MNO components, ensuring uniformity in functions like authentication, data plans, policy enforcement, and charging between the MNO network and the expanded network powered by Magma.

## Magma architecture diagram

![Text](docs/images/magma_overview.png)

