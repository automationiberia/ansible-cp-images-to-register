# Copy images to a Container register Playbook

This Ansible playbook automates the process of managing container images. It performs various tasks such as pulling, tagging, pushing, and deleting images from container registries.

## Prerequisites

Before running this playbook, ensure you have the following prerequisites installed:

- Ansible
- Podman
- Docker registry credentials (for pulling/pushing images)

   ```bash
   $ ansible-galaxy collection install -r collections/requirements.yaml -p collections
   ```
## Variables

| Variable                  | Description                                                                     |
|---------------------------|---------------------------------------------------------------------------------|
| `images_copy_to_quay`     | List of Docker images to be managed, including their names and tags.            |
| `quay_dest_account`       | Destination account in the Quay.io registry.                                    |
| `vault_registry_username` | Username for authenticating with Docker registries.                             |
| `vault_registry_password` | Password for authenticating with Docker registries.                             |
|---------------------------|---------------------------------------------------------------------------------|

## Usage

1. Clone this repository to your local machine:

   ```bash
   git clone <repository_url>
   ```

2. Populate registry connection variables:
   ```bash
   $ vim vars.yaml
       vault_registry_username: quay.io-username-CHANGEME!
       vault_registry_password: quay.io-password-CHANGEME!
       images_copy_to_quay:
         - name: quay.io/silvinux/2048
           tag: v1
         - name: quay.io/silvinux/2048
           tag: v2
         - name: quay.io/silvinux/simple-http
           tag: v1
         - name: quay.io/silvinux/simple-http
           tag: v2
       quay_dest_account: "quay.io/automationiberia/ot2024
   ```

2. Execute playbook:
   ```bash
   $  ansible-playbook copy_images_to_your_quay.yaml -e @vars/vault.yaml
   ```
