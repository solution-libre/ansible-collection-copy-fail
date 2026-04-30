# Copy Fail reactivation Ansible role

An Ansible role to reactivate the `algif_aead` kernel module after applying the
[CVE-2026-31431 (Copy Fail)](https://copy.fail) mitigation — for example once a
patched kernel is installed and a reboot has been performed.

The role reverses the two disabling steps applied by the `mitigation` role:

1. Removes the `modprobe` drop-in (`/etc/modprobe.d/disable-algif.conf`) that
   blocked `algif_aead` from loading.
2. Loads the `algif_aead` module back into the running kernel.

## Requirements

The `community.general` collection is required for the `modprobe` module:

```bash
ansible-galaxy collection install community.general
```

## Role Variables

None.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: reactivation
```

## License

[GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)

## Author Information

This role was created by [Solution Libre](https://www.solution-libre.fr).
