# Ansible-anysync

- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installing](#installing)
- [Usage](#usage)
- [Contribution](#contribution)

## Getting Started

Ansible role for any-sync daemons. Currently, this works on Debian and RHEL based linux systems. Tested platforms are:
* Ubuntu 22.04
* Amazon Linux 2

You can read the documentation on using any-sync [here](https://tech.anytype.io/).

### Prerequisites

* Minimum Ansible v2.11 recommended
* Minimum **x1** [Redis with Bloom module](https://github.com/RedisBloom/RedisBloom)
* Minimum **x3 MongoDB** (version ≥6 recommended) in Replica Set mode ([requirement for any-sync-consensusnode](https://github.com/anyproto/any-sync-consensusnode/blob/v0.1.1/README.md?plain=1#L19))
* S3 object storage: AWS S3 or self-hosted solution (for example [minio](https://github.com/minio/minio))

### Installing

Clone the current repository with roles

```
git clone https://github.com/anyproto/ansible-anysync.git
```

Use the playbook:

```
ansible-playbook any-sync.yml -i inventory.yml
```

## Usage

1. Define the structure of your any-sync cluster in the `inventory.yml` file. Minimum **x1 node of each type**, and also **x1 Redis** and **x3 MongoDB** in Replica Set mode. If not using AWS S3, specify **Minio server** address.
2. Generate using [any-sync-tools](https://github.com/anyproto/any-sync-tools/blob/main/any-sync-network/README.md) and then copy `networkId`(from heart.yml file) of your network and `peerId, peerKey, signingKey` for each any-sync-* account. Paste this data into the `group_vars/any_sync.yml` file on the appropriate lines, replacing example data.
3. You can then make configuration changes to each any-sync-* daemon by editing the corresponding `default/main.yml` within each role. Remember to change the MongoDB and Redis URLs if required.
4. Import into your client app `heart.yml` file that you should have created during generation in step 2.

## Contribution
Thank you for your desire to develop Anytype together!

❤️ This project and everyone involved in it is governed by the [Code of Conduct](https://github.com/anyproto/.github/blob/main/docs/CODE_OF_CONDUCT.md).

🧑‍💻 Check out our [contributing guide](https://github.com/anyproto/.github/blob/main/docs/CONTRIBUTING.md) to learn about asking questions, creating issues, or submitting pull requests.

🫢 For security findings, please email [security@anytype.io](mailto:security@anytype.io) and refer to our [security guide](https://github.com/anyproto/.github/blob/main/docs/SECURITY.md) for more information.

🤝 Follow us on [Github](https://github.com/anyproto) and join the [Contributors Community](https://github.com/orgs/anyproto/discussions).

---
Made by Any — a Swiss association 🇨🇭

Licensed under [MIT](./LICENSE.md).
