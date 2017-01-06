packer Ansible role
===================

Installs and configures [Packer] for building VM images.

Unlike most community-maintained Packer installation roles, this role will
verify package integrity via a GPG-signed SHA256 checksum file prior to installing.

Role Variables
--------------

```yaml
# Hardcoded version string. Will be reused in multiple vars. Must be manually
# updated to install new versions. Checksums will be automatically verified.
packer_version: 0.12.1

# Directory to store downloaded files, including checksum info.
packer_download_dir: /usr/local/src

# Download URLs for fetching ZIP file of binaries and checksum verification info.
packer_zip_url: "https://releases.hashicorp.com/packer/{{ packer_version }}/packer_{{ packer_version }}_linux_amd64.zip"
packer_checksum_url: "https://releases.hashicorp.com/packer/{{ packer_version }}/packer_{{ packer_version }}_SHA256SUMS"
packer_signature_url: "{{ packer_checksum_url }}.sig"
```

Example Playbook
----------------

```yaml
- name: Install Packer.
  hosts: packer
  vars:
    packer_version: 0.12.1
  roles:
    - role: freedomofpress.packer
      become: yes
      tags: packer
```

License
-------

MIT

Author Information
------------------

[Freedom of the Press Foundation]

[Packer]: https://packer.io/
[Freedom of the Press Foundation]: https://freedom.press/
