# Copy Fail Ansible collection

<!-- markdownlint-disable-next-line MD001 -->
#### Table of Contents

1. [Description](#description)
2. [Usage](#usage)
3. [Development](#development)
4. [Contributors](#contributors)

## Description

[Ansible](https://www.ansible.com/) collection that mitigate [Copy Fail](https://copy.fail/)
on [Debian](https://www.debian.org/)-based Linux distributions.

## Usage

```sh
    ansible-galaxy collection install soli.copy-fail
```

You can also include it in a `requirements.yml` file and install it via
`ansible-galaxy collection install -r requirements.yml` using the format:

```yaml
collections:
  - name: soli.copy-fail
```

To upgrade the collection to the latest available version, run the following command:

```sh
ansible-galaxy collection install soli.copy-fail --upgrade
```

You can also install a specific version of the collection, for example, if you need to downgrade when something is
broken in the latest version (please report an issue in this repository).
Use the following syntax where `X.Y.Z` can be any [available version](https://galaxy.ansible.com/soli/copy-fail):

```sh
ansible-galaxy collection install soli.copy-fail:==X.Y.Z
```

See [Ansible Using collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html) for more
details.

## Development

[Solution Libre](https://www.solution-libre.fr)'s repositories are open projects,
and community contributions are essential for keeping them great.

[Fork this repo on our GitLab](https://usine.solution-libre.fr/ansible/copy-fail/-/forks/new).

## Contributors

The list of contributors can be found at: <https://usine.solution-libre.fr/ansible/copy-fail/-/graphs/main>.
