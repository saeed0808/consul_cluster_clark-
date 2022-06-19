# Automate the creation of a Consul cluster using using terraform, packer and, scripting on AWS

This repo contains a set of modules in the modules folder for deploying a Consul cluster on AWS using Terraform. Consul is a distributed, highly-available tool that you can use for service discovery and key/value storage. A Consul cluster typically includes a small number of server nodes, which are responsible for being part of the consensus quorum, and a larger number of client nodes, which you typically run alongside your apps:


