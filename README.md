![Ansible Lint](https://github.com/johanneskastl/ansible-role-podman_bind9_resolver/workflows/Ansible%20Lint/badge.svg)

podman_bind9_resolver
=========

Install a Bind9 validating DNS resolver using podman

Requirements
------------

None.

Role Variables
--------------

**Role behaviour**

- `enable_podman_auto_updates_timer`: (Boolean) Whether the `podman-auto-update.timer` should be enabled or not (default: `false`)

**Bind9 configuration options**

- `podman_bind9_resolver_forwarders`: list of IPs that should be added as DNS forwarders. This needs to be specified as a list, not in bind9 configuration syntax.
- `podman_bind9_resolver_allow_query`: Value that should be set for the bind configuration option `allow-query`. Defaults to `any` (the trailing semicolon is added automatically)
- `podman_bind9_resolver_allow_query_cache`: Value that should be set for the bind configuration option `allow-query-cache`. Defaults to `any` (the trailing semicolon is added automatically)
- `podman_bind9_resolver_allow_recursion`: Value that should be set for the bind configuration option `allow-recursion`. Defaults to `any` (the trailing semicolon is added automatically)
- `podman_bind9_resolver_dnssec_validation`: Value that should be set for the bind configuration option `dnssec-validation`. Defaults to `auto` (the trailing semicolon is added automatically)
- `podman_bind9_resolver_ipv6_enabled`: (Boolean) The configuration option `listen-on-v6` will be set to `any`, if this variable is set to `true`, or `none` if this variable is set to `false`. Default value is `true`.

**Container image**

- `bind9_container_image`: full name of the container image including the tag (default: `docker.io/internetsystemsconsortium/bind9:9.18`)

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: 'johanneskastl.podman_bind9_resolver'
          podman_bind9_resolver_forwarders:
            # DNS servers taken from [Mike Kuketz' recommendations](https://www.kuketz-blog.de/empfehlungsecke/#dns)
            - 80.241.218.68
            - 159.69.114.157
            - 176.9.93.198

License
-------

BSD-3-Clause

Author Information
------------------

I am Johannes Kastl, reachable via kastl@b1-systems.de.
