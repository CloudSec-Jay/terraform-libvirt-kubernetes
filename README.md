# Terraform libvirt Kubernetes

Reusable Terraform configuration for creating a small Kubernetes lab on a
remote libvirt host. It provisions Rocky Linux virtual machines, configures a
private libvirt network, attaches optional data disks, applies cloud-init, and
generates an Ansible inventory.

This repository is a reusable extraction from a private orchestration platform.
It contains safe example values only; live environment configuration remains
private. See `PUBLICATION_CHECKLIST.md` for the remaining runtime validation.

## Prerequisites

- Terraform 1.5 or newer
- A libvirt host reachable through key-based SSH
- A checksum-pinned Rocky Linux GenericCloud image
- A dedicated Ed25519 public key for the virtual machines

Do not disable SSH host-key verification. The remote account should receive
only the libvirt permissions required to manage this environment.

## Usage

```bash
cp terraform.tfvars.example terraform.tfvars
terraform init
terraform fmt -check -recursive
terraform validate
terraform plan -out=tfplan
terraform apply tfplan
```

The generated Ansible inventory is written to `generated/k8s.ini`. Terraform
state, saved plans, generated inventory, credentials, and private keys are
ignored and must not be committed.

## Scope

This project owns the reusable virtual infrastructure only. Kubernetes
bootstrap and platform add-ons belong in an Ansible collection or the private
orchestration repository.

## License

Apache License 2.0. See [`LICENSE`](LICENSE).
