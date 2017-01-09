Role: cns.dns
========

This role creates DNS entries for Route 53 using the ansible route53 module.

Requirements
------------

Nothing, it runs out of the box.

Role Variables
--------------

In the current version, you can specify the following variables:

| Name               | Default |                                           |
|--------------------|---------|-------------------------------------------|
| dns                |   ---   | Object variable containing site DNS zone. |

Dependencies
------------

This package has no dependencies.

License
-------

GPLv2

Author Information
------------------

Sam Morrison

Examples
--------
```yaml
# dns object variable
---
dns:
  - zone: some-fancy-site.com
    entries:
      - record: some-fancy-site.com
        type: A
        ttl: 500
        value: 12.34.56.78
      - record: some-fancy-site.com
        type: MX
        ttl: 500
        value: "5 mta.some-fancy-site.com"
      - record: blog.some-fancy-site.com
        type: CNAME
        ttl: 500
        value: server1.some-fancy-site.com
```

```yaml
---
- name: cns.dns role test
  hosts: all
  roles:
    - cns.dns
```
