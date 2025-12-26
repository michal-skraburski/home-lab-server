# Home Lab Server
![Case](./images/case.jpeg)
<sup>Not actual build inside because old picture, I'm reusing the case</sup>

## System Specifications
- X99 Fata1ity Killer AsRock LGA2011
  - 16 x 4 GB DDR4 2133MHz
  - Intel Xeon E5-2699 V4 22 Core 44 Threads @ 2.20GHz 
  - No dGPU
  - 512GB NVME OS SDD
- SATA
 - 4 x 1TB RAID SSD

## Architecture Overview
- OpenMediaVault OS (OMV) 
- Docker-Compose for daily services
  - Wireguard
  - Plex
  - Blog Site
  - GitLab
  - and other private web services I'm using 
- Kubernetes & Flux for experimentation


## System usage 
OMV is used because it's a pure linux system under the hood. Docker setup for software I'm writing or using for daily use, such as a blog webpage accessible from any local device.

Kubernetes is used for experiments since I want the experience, I'm using Flux to practice GitOps workflows, version controlling the environment, rollbacks, automatic updating etc

Wireguard is setup through the Docker and exposed to the router, then port forwarded. I use this for remote management for whenever I need to restart a service or use one of the services.
A good use case is also the NAS, enabling other people in my family to use the NAS is important to me, although quite tedious because it requires them to do technical vpn configuration.
```
Internet -> Router -> VPN -> OMV
                           | Docker Services
                           | Kubernetes Cluster with Flux
                           | NAS Storage
```
I’m considering buying a domain and exposing a secure login gateway so the NAS can be accessed without requiring a VPN. I haven’t done this yet because I want to ensure the security model is solid first.

## Things I've learned so far
- Keeping configs in Git helps keep my main system consistent and hard rollbacks easy
- VPN onboarding for non-technical people is a UX problem

## Further Goals
- Migrate to building reliable, Kubernetes ready projects
- Build a reliable anywhere-accessible private NAS
- Practice security and provide secure access
  - Add reverse-proxy and SSO
- Analyze the power draw I'm using, optimize services to keep low power usage
- Add system monitoring services for logs and alerts via email
  - Notes: Prometheus / Grafana
