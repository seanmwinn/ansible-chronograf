chronograf
=========

An Ansible role which installs and configures 'the C' (Chronograf) of the TICK stack from InfluxData.

Requirements
------------

Currently this role is developed for and tested on Debian GNU/Linux (release: jessie). It is assumed to work on other Debian distributions as well.

Example
----------------

    - hosts: chronograf-servers
      roles:
         - { role: chronograf }


Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):


- `chronograf_config_bind` 
> description: TCP address that Chronograf should bind to.
>
> default: "127.0.0.1:10000"

- `chronograf_config_local_database`
> description: Path to local database file to use or create for storing Chronograf application data.
>
> default: "/opt/chronograf/chronograf.db"

- `chronograf_config_query_response_bytes_limit`
> description: Maximum response size in bytes, for queries that pass through Chronograf.
>
> default: 2500000



Dependencies
------------

None.

License
-------

MIT

Author Information
------------------

* Patrick Ringl
