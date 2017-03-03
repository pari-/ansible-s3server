# s3server

An Ansible role which installs and configures Scality's open-source Node.JS implementation of a server handling the S3 protocol

<!-- toc -->

- [Requirements](#requirements)
- [Example](#example)
- [Variables](#variables)
  * [Role Variables](#role-variables)
  * [Role Internals](#role-internals)
- [Dependencies](#dependencies)
- [License](#license)
- [Author Information](#author-information)

<!-- tocstop -->

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Ansible version in use for development: 2.2.1

## Example

```yaml
- hosts: s3-servers

  vars:
    nodejs_version: "node_7.x"
    nodejs_apt_key_id: "68576280"

  roles: 
    - "ansible-s3server"
```

## Variables

Available variables are listed below, along with default values (see defaults/main.yml). They're generally prefixed with `s3server_` (which I deliberately leave out here for better formatting).

### Role Variables

variable | default | notes
-------- | ------- | -----
`bucketd_list['bootstrap']` | `['localhost']` | `TBD`
`clusters` | `10` | `TBD`
`health_check_list['allowFrom']` | `['127.0.0.1/8','::1']` | `TBD`
`listen_on` | `[]` | `TBD`
`log_dump_level` | `error` | `TBD`
`log_level` | `info` | `TBD`
`port` | `8000` | `TBD`
`region_list['localregion']` | `['localhost']` | `TBD`
`sproxyd_list['bootstrap']` | `['localhost:8181']` | `TBD`
`us_east_behavior` | `false` | `TBD`
`vaultd_host` | `localhost` | `TBD`
`vaultd_port` | `8500` | `TBD`

### Role Internals

variable | default | notes
-------- | ------- | -----
`cache_valid_time` | `3600` | `Update the apt cache if its older than the set value (in seconds)`
`config_file` | `/opt/s3server/config.json` | `Absolute path to s3server's configuration file`
`default_release` | `jessie` | `The default release to install packages from.`
`git_accept_hostkey` | `yes` | `Adds the hostkey for the repo url if not already added`
`git_dest` | `/opt/s3server` | `Absolute path of where the repository should be checked out to`
`git_repo` | `https://github.com/scality/S3.git` | `git, SSH, or HTTP(S) protocol address of the git repository`
`git_update` | `no` | `If no, do not retrieve new revisions from the origin repository.`
`git_version` | `GA6.4.2` | `What version of the repository to check out`
`npm_global` | `yes` | `Install the node.js library globally`
`npm_production` | `yes` | `Install dependencies in production mode, excluding devDependencies`
`npm_state` | `present` | `The state of the node.js library`
`package_list` | `['git', 'g++']` | `The list of packages to be installed`
`packages_state` | `present` | `TBD`
`pm2_app_name` | `s3server` | `The name s3server becomes registered at pm2`
`pm2_binary` | `/usr/bin/pm2` | `Absolute path to the 'pm2'-binary`
`supported_distro_list` | `['jessie']` | `A list of distribution releases this role supports`
`update_cache` | `yes` | `Run the equivalent of apt-get update before the operation`

## Dependencies

- [ansible-pm2](https://github.com/pari-/ansible-pm2)
- [ansible-role-nginx](https://github.com/jdauphant/ansible-role-nginx)

## License

MIT

## Author Information

* Patrick Ringl
