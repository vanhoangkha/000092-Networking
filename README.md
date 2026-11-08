# AWS Networking and Content Delivery

> AWS networking fundamentals.

A hands-on workshop from the [AWS First Cloud Journey](https://github.com/vanhoangkha/aws-first-cloud-journey) series, available in English and Vietnamese.

**Read the workshop online:** https://vanhoangkha.github.io/000092-Networking/

## Overview

An Availability Zone (AZ) consists of one or more data centers, the (AZs) are designed so that no failure affects 2 AZs at the same time (fault isolation). Between the 2 AZs is a dedicated high-speed connection. AWS recommends deploying the application on at least 2 AZs.

An AWS Region consists of at least 3 Availability Zones. Currently, there are more than 25 Regions globally. Regions are connected by the AWS backbone network. By default, data and services in regions are independent of each other. (Except for some services at a global scale).

## Workshop contents

1. Introduction
2. Preparation
   - VPC Deployment
   - Cisco CSR Agreement
3. VPC Components Deep Dive
4. Transit Gateway and Site-to-Site VPNs
   - Datacenter Router and Transit Gateway Deployment
   - Access Cisco CSR Router with Cloud9
   - Site-to-site VPN setup
   - Additional ECMP Paths
   - Transit Gateway Routing
5. Route53 DNS Endpoints and Internal Hosted Zones
   - DNS Components Deployment
   - DNS Testing
6. VPC Endpoints for AWS Services
   - VPC Endpoints - Deployment
   - NP2 Endpoint Testing
7. VPC Endpoint Services
   - VPC Endpoint Services - Deployment
8. VPC Peering
   - VPC Peering Request
   - Routing Configuration
   - Final Testing
9. Transit Gateway Network Manager
   - Network Manager Setup
   - Site Configuration
   - Network Insights
10. Clean up resources

## Prerequisites

- An AWS account with permissions to create the resources used in the labs
- Basic familiarity with the AWS Management Console
- [Hugo](https://gohugo.io/installation/) (extended edition) if you want to run the site locally

## Run locally

```bash
git clone --recurse-submodules https://github.com/vanhoangkha/000092-Networking.git
cd 000092-Networking
hugo server
```

Then open http://localhost:1313 in your browser.

## Repository structure

| Path | Purpose |
| --- | --- |
| `content/` | Workshop pages (`*.md` English, `*.vi.md` Vietnamese) |
| `static/` | Images and other static assets |
| `layouts/` | Hugo layout overrides |
| `themes/` | Hugo theme |
| `config.toml` | Site configuration |

## Cost and cleanup

The labs create AWS resources that may incur charges. Complete the **Clean up** chapter when you finish to remove them.

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

To report a security issue, see [SECURITY.md](SECURITY.md).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
