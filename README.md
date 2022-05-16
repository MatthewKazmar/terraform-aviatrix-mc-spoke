# terraform-aviatrix-mc-spoke

### Description
Deploys a VPC/VNET/VCN and Aviatrix Spoke gateways. It is also possible to use an existing VPC/VNET/VCN.
China and government regions are supported in both AWS and Azure and auto detected based on region name.

### Compatibility
Module version | Terraform version | Controller version | Terraform provider version
:--- | :--- | :--- | :---
v1.2.0 | >= 1.x | >= 6.7.1186 | ~> 2.22.0

Check [release notes](https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/RELEASE_NOTES.md) for more details.
Check [Compatibility list](https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/COMPATIBILITY.md) for older versions.

### Usage Examples
See [examples](https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/examples/)

### Variables
The following variables are required:

key | value
:--- | :---
cloud | Cloud where this is deployed. Valid values: "AWS", "Azure", "ALI", "OCI", "GCP"
name | Name for this spoke VPC/VNET/VCN and it's gateways
region | Cloud region to deploy this VPC/VNET/VCN in
cidr | What ip CIDR to use for this VPC/VNET/VCN (Not required when use_existing_vpc is true)
account | The account name as known by the Aviatrix controller
transit_gw | The name of the transit gateway we want to attach this spoke to. Not required when attached is set to false.

The following variables are optional:

<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> = AWS, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> = Azure, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> = GCP, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> = OCI, <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> = Alibaba


Key | Supported_CSP's |  Default value | Description
:-- | --: | :-- | :--
approved_learned_cidrs | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | A list of approved learned CIDRs.
attached | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if you don't want to attach spoke to transit_gw.
attached_gw_egress | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if you don't want to attach spoke to transit_gw_egress.
auto_advertise_s2c_cidrs | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Auto Advertise Spoke Site2Cloud CIDRs.
az_support | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | true | Set to false if the region does not support Availability Zones.
az1 | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | a<br>az-1<br>b | Concatenates with region to form az names. e.g. eu-central-1a. Used for insane mode only.
az2 | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | b<br>az-2<br>c | Concatenates with region to form az names. e.g. eu-central-1b. Used for insane mode only.
bgp_ecmp | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Enable Equal Cost Multi Path (ECMP) routing
bgp_hold_time | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | BGP hold time. Unit is in seconds.
bgp_polling_time | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | BGP route polling time. Unit is in seconds.
customer_managed_keys | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> | | Customer managed key ID for EBS Volume encryption.
customized_spoke_vpc_routes | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | A list of comma separated CIDRs to be customized for the spoke VPC routes. When configured, it will replace all learned routes in VPC routing tables, including RFC1918 and non-RFC1918 CIDRs. Example: 10.0.0.0/116,10.2.0.0/16
enable_active_standby | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Enables Active-Standby Mode. Available only with HA enabled.
enable_bgp | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Enable BGP for this spoke gateway.
enable_encrypt_volume | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> | false | Set to true to enable EBS volume encryption for Gateway.
enable_learned_cidrs_approval | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Switch to enable/disable CIDR approval for BGP Spoke Gateway.
filtered_spoke_vpc_routes | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | |A list of comma separated CIDRs to be filtered from the spoke VPC route table. When configured, filtering CIDR(s) or it’s subnet will be deleted from VPC routing tables as well as from spoke gateway’s routing table. Example: 10.2.0.0/116,10.3.0.0/16
gw_subnet | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | |Subnet CIDR, for using an existing VPC. Required when use_existing_vpc is enabled. Make sure this is a public subnet.
ha_cidr | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | | The IP CIDR to be used to create ha_region spoke subnet. Only required when ha_region is set.
ha_gw |<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if you only want to deploy a single Aviatrix spoke gateway
ha_region | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> | | Region for multi region HA. HA is multi-az single region by default, but will become multi region when this is set.
hagw_subnet | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Subnet CIDR, for using an existing VPC. Required when use_existing_vpc is enabled and ha_gw is true. Make sure this is a public subnet.
included_advertised_spoke_routes | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | A list of comma separated CIDRs to be advertised to on-prem as Included CIDR List. When configured, it will replace all advertised routes from this VPC. Example: 10.4.0.0/116,10.5.0.0/16
insane_mode | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> | false | Set to true to enable insane mode encryption
inspection | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Set to true to enable east/west Firenet inspection. Only valid when transit_gw is East/West transit Firenet.
instance_size | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"><br><img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> |  t3.medium<br>Standard_B1ms<br>n1-standard-1<br>VM.Standard2.2<br>ecs.g5ne.large | The size of the Aviatrix spoke gateways
learned_cidrs_approval_mode | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Learned CIDRs approval mode. Either "gateway" (approval on a per-gateway basis) or "connection" (approval on a per-connection basis).
local_as_number | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Changes the Aviatrix Spoke Gateway ASN number before you setup Aviatrix Spoke Gateway connection configurations.
network_domain | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Provide network domain name to which spoke needs to be deployed. Transit gateway must be attached and have segmentation enabled.
prepend_as_path | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | List of AS numbers to populate BGP AS_PATH field when it advertises to VGW or peer devices.
private_vpc_default_route | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Program default route in VPC private route table.
rx_queue_size | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Gateway ethernet interface RX queue size. Once set, can't be deleted or disabled.
single_az_ha | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | true | Set to false if Controller managed Gateway HA is desired
single_ip_snat | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Specify whether to enable Source NAT feature in single_ip mode on the gateway or not. Please disable AWS NAT instance before enabling this feature. Currently only supports AWS(1) and AZURE(8)
skip_public_route_table_update | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Skip programming VPC public route table.
spoke_bgp_manual_advertise_cidrs | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | Intended CIDR list to be advertised to external BGP router.
subnet_groups | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | | Map of subnet groups to create for this spoke. Example: {"group1" = ["10.1.48.0/20\~\~subnet1", "10.1.64.0/20\~\~subnet2"], "group2" = ["10.2.48.0/20\~\~subnet3", "10.2.64.0/20\~\~subnet4"],}
subnet_pairs | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | 2 | Number of Public/Private subnet pairs created in the VPC.
subnet_size | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | 28 | Size of the Public/Private subnets in the VPC.
tags |<img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | | Map of tags to assign to the gateway.
transit_gw_egress | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> | | Add secondary transit to attach spoke to (e.g. for dual transit firenet). When segmentation is used, transit_gw MUST be used for east/west transit.
transit_gw_egress_route_tables | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | [] | A list of route tables to propagate routes to for transit_gw_egress attachment.
transit_gw_route_tables | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | [] | A list of route tables to propagate routes to for transit_gw attachment.
tunnel_detection_time | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | The IPsec tunnel down detection time for the Spoke Gateway in seconds. Must be a number in the range [20-600]. Default is 60.
use_existing_vpc | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | false | Set to true to use an existing VPC in stead of having this module create one.
vpc_id | <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/aws.png?raw=true" title="AWS"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/azure.png?raw=true" title="Azure"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/gcp.png?raw=true" title="GCP"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/oci.png?raw=true" title="OCI"> <img src="https://github.com/terraform-aviatrix-modules/terraform-aviatrix-mc-spoke/blob/master/img/alibaba.png?raw=true" title="Alibaba"> | | VPC ID, for using an existing VPC.

### Outputs
This module will return the following outputs:

key | description
:---|:---
[vpc](https://registry.terraform.io/providers/AviatrixSystems/aviatrix/latest/docs/resources/aviatrix_vpc) | The created VPC as an object with all of it's attributes (when use_existing_vpc is false). This was created using the aviatrix_vpc resource.
[spoke_gateway](https://registry.terraform.io/providers/AviatrixSystems/aviatrix/latest/docs/resources/aviatrix_spoke_gateway) | The created Aviatrix spoke gateway as an object with all of it's attributes.

