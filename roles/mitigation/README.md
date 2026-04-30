# Copy Fail mitigation Ansible role

An Ansible role to mitigate [CVE-2026-31431 (Copy Fail)](https://copy.fail)
— a Linux local privilege escalation exploiting `AF_ALG` (`algif_aead`) to write into the page cache of a setuid binary.

The role applies the three recommended mitigations in order:

1. Disables the `algif_aead` kernel module via `modprobe`.
2. Drops the page cache to clear any in-memory payload left by a prior exploit run.
3. Updates the distribution's kernel packages to include mainline commit `a664bf3d603d`.

## Requirements

The `community.general` collection is required for the `modprobe` module:

```bash
ansible-galaxy collection install community.general
```

## Role Variables

| Variable | Default | Description |
| --- | --- | --- |
| `mitigation_drop_page_cache` | `true` | Drop the page cache (`drop_caches=3`). The exploit modifies only the page cache, not the file on disk — dropping it removes any in-memory payload without a reboot. |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: mitigation
```

## License

[GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)

## Author Information

This role was created by [Solution Libre](https://www.solution-libre.fr).
