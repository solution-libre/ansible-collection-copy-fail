# Copy Fail detection Ansible role

An Ansible role to detect whether a system is vulnerable to
[CVE-2026-31431 (Copy Fail)](https://copy.fail) — a Linux local privilege
escalation exploiting `AF_ALG` (`algif_aead`) to write into the page cache
of a setuid binary.

The role checks two independent protection mechanisms and exposes the result
as Ansible facts for use by other roles or playbooks:

1. Verifies the installed kernel package version against the fixed version for
   the detected Debian release.
2. Checks whether the `modprobe` drop-in (`/etc/modprobe.d/disable-algif.conf`)
   applied by the `mitigation` role is present.

## Requirements

None.

## Role Variables

| Variable | Default | Description |
| --- | --- | --- |
| `detection_fail_if_unprotected` | `false` | When `true`, the role fails if the system is neither patched nor mitigated. When `false`, a warning is printed and execution continues. |

## Exposed Facts

| Fact | Description |
| --- | --- |
| `detection_copy_fail_patched` | `true` if the running kernel package version is ≥ the fixed version for the detected Debian release. |
| `detection_copy_fail_mitigated` | `true` if `/etc/modprobe.d/disable-algif.conf` is present (mitigation role applied). |
| `detection_copy_fail_vulnerable` | `true` if neither `detection_copy_fail_patched` nor `detection_copy_fail_mitigated` is `true`. |
| `detection_copy_fail_protected` | `true` if `detection_copy_fail_patched` or `detection_copy_fail_mitigated` is `true`. |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: detection
```

Fail the playbook if any host is unprotected:

```yaml
- hosts: all
  roles:
    - role: detection
      vars:
        detection_fail_if_unprotected: true
```

## License

[GPLv3](https://www.gnu.org/licenses/gpl-3.0.html)

## Author Information

This role was created by [Solution Libre](https://www.solution-libre.fr).
