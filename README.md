# chronograf

An Ansible role which installs and configures 'the C' (Chronograf) of the TICK stack from InfluxData.

## Requirements

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Ansible version in use for development:  2.2.0.0

## Example

```yaml
- hosts: chronograf-servers
  roles:
     - { role: chronograf }
```


## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

### chronograf_config

The following shows the global configuration dict:

```yaml
chronograf_config:
  Bind: "127.0.0.1:10000"
  LocalDatabase: "/opt/chronograf/chronograf.db"
  QueryResponseBytesLimit: 2500000
```

- `chronograf_config['Bind']` 
> TCP address that Chronograf should bind to.
>
> `"127.0.0.1:10000"`

- `chronograf_config['LocalDatabase']`
> Path to local database file to use or create for storing Chronograf application data.
>
> `"/opt/chronograf/chronograf.db"`

- `chronograf_config['QueryResponseBytesLimit']`
> Maximum response size in bytes, for queries that pass through Chronograf.
>
> `2500000`

### Role Internals

- `chronograf_service_name`
> The name of the chronograf service.
>
> `"chronograf"`

- `chronograf_supported_distribution_releases`
> A list of distribution releases this role supports.
>
> `['wheezy', 'jessie', 'precise', 'trusty', 'utopic', 'vivid', 'wily', 'xenial', 'yakkety']`

- `chronograf_release_component`
> The release component which is used in `chronograf_install_apt_repository_repo` to retrieve packages from.
>
> `"stable"`

- `chronograf_install_apt_key_id`
> The identifier for the key of the chronograf repository.. Including this allows check mode to correctly report the changed state.
>
> `""`

- `chronograf_install_apt_key_url`
> The url to retrieve the apt-key for the chronograf repository from.
>
> `"https://repos.influxdata.com/influxdb.key"`

- `chronograf_install_apt_repository_repo`
> A source string for the chronograf repository.
>
> `"deb https://repos.influxdata.com/debian {{ ansible_distribution_release|lower }} {{ chronograf_release_component }}"`

- `chronograf_install_apt_repository_validate_certs`
> If no, SSL certificates for the chronograf repository will not be validated. 
>
> `"no"`

- `chronograf_install_apt_update_cache`
> Run the equivalent of apt-get update before the operation.
>
> `"yes"`

- `chronograf_install_apt_cache_valid_time`
> Update the apt cache if its older than the set value.
>
> `"3600"`

- `chronograf_install_package_list`
> The list of packages to be installed.
>
> `['chronograf']`

- `chronograf_bin`
> The default path to the chronograf binary.
>
> `"/opt/chronograf/chronograf"`

- `chronograf_config_file`
> The default path to the chronograf configuration file.
>
> `"/opt/chronograf/config.toml"`

## Dependencies

None.

## License

MIT

## Author Information

* Patrick Ringl
