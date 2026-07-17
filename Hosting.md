List of ISPs: https://marinade.finance/app/network/isps/?countries=&direction=descending&sorting=stake

# Bare Metal

- [Interserver](https://www.interserver.net/dedicated/buy-now-servers.html)
  - [7443p 256GB 2TB SSD + 2x2TB HVMe](https://www.interserver.net/dedicated/v2-dedicated2.php?hd%5B%5D=44&hd%5B%5D=44&hd%5B%5D=23&cpu=135&memory=24&os=30&bandwidth=10&ips=9) for $600/month
- [Cherry services](https://www.cherryservers.com/pricing/dedicated-servers)
  - [7443p 256GM 3x1TB NVMe](https://portal.cherryservers.com/deployment?plan=739&cycle=3&components=39964,37891,39978,39989,40002&show_hardware=1&tags=up_to_32) $775 first month, $668 after.
- [Latitude](https://www.latitude.sh/metal/pricing)
  - Out of stock
- [Teraswitch](https://teraswitch.com/bare-metal)
  - Out of stock
- [Reliablesite](https://www.reliablesite.net/dedicated-servers)
  - Out of stock
- [Lumen](https://www.lumen.com/en-us/marketplace/edge-cloud/bare-metal.html)
- [WebNX](https://webnx.com/dedicated-servers/custom-dedicated-servers/)
  - They require to contact their sales department for customization.
- [Equinix](https://deploy.equinix.com/product/bare-metal/servers/)
  - Out of stock
- [Edgevana](https://srv.edgevana.com/solana-validator-servers)
  - I think it was founded by Solana.
  - Most suitable for [SFDP](https://github.com/andreimontchik/research/wiki/SFDP)
  - Out of stock for reasonable pricing.
- [OVHCloud](https://us.ovhcloud.com/bare-metal/prices/?display=list)
  - They are black-holing Solana Validators thinking that they are being DDOSes.

# Cloud

- [Google Cloud Pricing](https://cloud.google.com/pricing?hl=en)
  - [VM Instance Pricing](https://cloud.google.com/compute/vm-instance-pricing)
    - [Compute engine price calculator](https://cloud.google.com/products/calculator?hl=en): the `n2-highmem-16` Regular Compute Engine with 16 vCPU (2 threads per core), 128 GB memory and 500GB SSD is $850.12 / month.
  - [Network Pricing](https://cloud.google.com/vpc/network-pricing)
    - Google VM-to-VM in same zone, same region using internal IPv4: free
    - Google VM-to-VM in diff zone of the same region: $0.01 / GiB
    - Network data transfer from Google cloud to North America $0.11 / GiB.
  - [Cloud Storage Pricing](https://cloud.google.com/storage/pricing#cloud-storage-pricing)
    - 10 TB of Standard Storage in Iowa region is $186.6 / month

# Hardware

- [Optimal Solana HW from Zan](https://discord.com/channels/428295358100013066/560174212967432193/1221687113079197706)
  ```
  My thoughts:
  - TR 3960X has been working for me for three years without any issue, and appears to *still* have headroom.  THREE YEARS.
  - TR 7960X is the generational upgrade to 3960X and I would tentatively brand it "the best Solana CPU".
  - EDIT: Forgot to mention that TR PRO 7965WX is essentially the same processor with better memory support, so that would be great too
  - However TR is not as readily available as rented hardware.  Most use EPYC.
  - Given this, EPYC 9274F would likely be the best EPYC processor for Solana
  - However, it's not nearly as available and more expensive than the fleets of older/cheaper EPYC out there
  - For older/cheaper, EPYC 74F3 seems best, but I believe it's the choice with the far least headroom for the future
  ```
