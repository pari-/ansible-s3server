# ansible-s3server

An Ansible role which installs and configures Scality's open-source Node.JS implementation of a server handling the S3 protocol

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Ansible version in use for development: 2.2.0

## Example

```yaml
- hosts: s3-servers

  roles: 
    - { role: ansible-nodejs, nodejs_install_version: 'node_7.x', nodejs_install_apt_key_id: '68576280' }
    - { role: ansible-pm2 }
    - { role: ansible-s3server }
```

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

### Role Internals

- `s3server_prerequisites_supported_distribution_releases`

  > A list of distribution releases this role supports.
  >
  > `['wheezy', 'jessie', 'precise', 'trusty', 'utopic', 'vivid', 'wily', 'xenial', 'yakkety']`

- `s3server_prerequisites_apt_packages`

  > A list of apt package dependencyies.
  >
  > `['git', 'g++']

- `s3server_prerequisites_apt_state`

  > Indicates the desired package state.
  >
  > `"present"`

- `s3server_prerequisites_apt_update_cache`

  > Run the equivalent of apt-get update before the operation.
  >
  > `"yes"`

- `s3server_prerequisites_apt_cache_valid_time`

  > Update the apt cache if its older than the x seconds.
  >
  > `3600`

- `s3server_install_git_repo`

  > git, SSH, or HTTP(S) protocol address of the git repository.
  >
  > `"https://github.com/scality/S3.git"`

- `s3server_install_git_dest`

  > Absolute path of where the repository should be checked out to.
  >
  > `"/opt/s3server"`

- `s3server_install_git_update`

  > If no, do not retrieve new revisions from the origin repository.
  >
  > `"no"`

- `s3server_install_git_version`

  > What version of the repository to check out.
  >
  > `"GA6.3.3"`

- `s3server_install_git_accpet_hostkey`

  > If yes, adds the hostkey for the repo url if not already added. 
  >
  > `"yes"`

- `s3server_install_npm_production`

  > Install dependencies in production mode, excluding devDependencies
  >
  > `"yes" `

- `s3server_configure_bin`

  > The path of the 's3server'-entity
  >
  > `"/usr/bin/pm2"`

## Dependencies

- ansible-nodejs
- ansible-pm2

## License

MIT

## Author Information

* Patrick Ringl
