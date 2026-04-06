# Proof of Concept Report — AWS Cloud Migration
**Course:** CMIT 326 — Class 7384  
**Institution:** University of Maryland Global Campus (UMGC)  
**Author:** Brandy Haynes  
**Date:** December 11, 2023  

---

## Abstract

This project establishes facts and key concepts related to the Don & Associates financial consulting firm, which is seeking to provide better and more accessible services to its clients. Currently the company relies on physical network infrastructure such as on-premises servers to maintain operations.

The addition of cloud computing will allow substantial growth by enabling the firm to expand without being tethered to a physical location. This report evaluates three major cloud providers and documents the hands-on implementation of an AWS Virtual Private Cloud (VPC) as a proof of concept for the company's migration.

---

## Introduction

The primary focus of this project is to identify a network solution appropriate to the firm's current workflow — one that can scale cost-effectively while delivering additional benefits such as new applications and automation capabilities. This project adopted **Amazon Web Services (AWS)** as the recommended infrastructure to guide Don & Associates in both its migration and future use.

---

## Statement of Need

Don & Associates aims to expand operations regionally across northeastern states with potential for global scaling. Key obstacles include:

- **Cost** — Physical servers, racks, and on-site technical support at multiple locations far exceeds the cost of a cloud solution
- **Data Security** — The firm needs to safeguard sensitive client information
- **Scalability** — The current infrastructure cannot support rapid expansion

This proof-of-concept covers how to identify technological needs, manage the AWS migration, implement automation, evaluate system security, and maintain the new infrastructure.

---

## Assumptions

- AWS management tools are efficient, user-friendly, and quick to deploy within a virtual network
- Network gateways, subnets, routing tables, and IP address ranges are congruent with the firm's needs

---

## Description of Current Infrastructure

Don & Associates currently maintains its own on-premises servers, physical networks, and equipment — a setup that sustainably supports a small to medium-sized business but cannot support rapid expansion. The strategic goal is to migrate this physical infrastructure to a cloud-based setup, streamlining and hardening services to create better operational efficiency.

---

## Cloud Service Provider Comparison

| Provider | Strengths | Limitations |
|----------|-----------|-------------|
| **AWS** | Largest global infrastructure, pay-as-you-go pricing, no upfront costs, AWS Cost Calculator | — |
| **Microsoft Azure** | Mobile/developer tools, databases, 60+ global data centers | More expensive, limited reach vs. AWS, complex support setup |
| **Google Cloud (GCP)** | Familiar brand, competitive pricing, 5 support tiers | Smaller infrastructure than AWS, limited mobile app compatibility |

**Recommendation:** AWS — most advanced provider, best scalability, most compatible with current and future needs.

---

## Project Details

### Building a VPC on AWS

**Step 1 — Create the VPC**
- Place every subnet into a single Availability Zone
- Create a NAT (Network Address Translation) Gateway to provide internet connectivity to EC2 instances in private subnets
- Provision the VPC with both a public and private subnet under the same Availability Zone, integrated with route tables

**Subnet Configuration:**
- Public Subnet CIDR: `10.0.0.0/24`
- Private Subnet CIDR: `10.0.1.0/24`

**Step 2 — Create Additional Subnets**
- Create subnets in a secondary Availability Zone for higher availability
- Configure the private subnet to route internet-bound traffic through the NAT Gateway
- Internet-bound traffic (`0.0.0.0/0`) is sent to the NAT Gateway, which forwards it from the private network to the internet

**Step 3 — Configure Route Tables**
- Route tables direct traffic from private subnets to the internet via the Internet Gateway

**Step 4 — Create a VPC Security Group**
- The security group serves as a virtual firewall for the network
- Applied to one or multiple instances within the network
- Configured with inbound and outbound traffic rules for all associated servers

### Launching a Web Server on AWS

- Launched a Web Server Instance onto an **Amazon EC2** instance within the new VPC
- Configured the instance to launch into the public subnet
- Loaded and configured a **PHP Web Application** script into the instance

---

## Challenges Encountered

The most notable issue was wait times during lab steps, likely due to internet connectivity rather than the AWS platform itself. The AWS Console is straightforward — the built-in search bar resolves most questions, and AWS customer support is available for escalation.

---

## Conclusion

AWS is the recommended cloud provider for Don & Associates due to its:

- **Scalability** — Compatible with both current and future growth needs
- **AWS Cloud Migration Service** — Seamless migration with minimal strain on company resources
- **Cost Efficiency** — "Economy of scale" pricing model with pay-as-you-go billing by the hour
- **Flexibility** — Ability to test new applications and instances before committing to full payment

The migration will eliminate large upfront capital expenditures while enabling the firm to expand its service area without physical infrastructure constraints.

---

## Appendix — Lab Screenshots

The following screenshots document each step of the hands-on AWS lab:

1. Start Lab
2. AWS Management Console
3. Task 1: Create Your VPC
4. View Your VPC
5. Task 2: Create Additional Subnets (Public & Private)
6. Task 3: Create a VPC Security Group
7. Task 4: Launch a Web Server Instance
8. Lab Complete

---

## References

1. Slingerland, C. AWS vs. Azure vs. Google Cloud: Which should you use? CloudZero. https://www.cloudzero.com/blog/aws-vs-azure-vs-google-cloud/
2. Hatton, M. What is Google Cloud? Nightingale HQ. https://nightingalehq.ai/knowledgebase/glossary/what-is-google-cloud/
3. Set up NAT gateway for private subnet in Amazon VPC. Amazon Web Services. https://repost.aws/knowledge-center/nat-gateway-vpc-private-subnet/
4. Höllwarth, T. Cloud migration. Amazon. https://aws.amazon.com/cloud-migration/
5. Tutorial: Create a VPC for use with a DB instance (IPv4 only). AWS. https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Tutorials.WebServerDB.CreateVPC.html
6. Types of cloud computing — SaaS vs PaaS vs IaaS. AWS. https://aws.amazon.com/types-of-cloud-computing/
