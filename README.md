Ansible role "gentoo.package-meta"
=========

Role for adding meta info(env/use/keywords/mask/unmusk) for package.

Requirements
------------

Works only on gentoo distro.

Role Variables
--------------

```yaml
packages:
  - name: "sys-devel/gcc"
    keywords: [~amd64]
    use: [debug, doc]
    env:
      - 'MAKEOPTS="-j1"'
  - name: "<=sys-devel/gcc-4"
    mask:
  - name: ">=sys-devel/gcc-5"
    unmask:
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - gentoo.package-meta
  vars:
    packages:
      - name: "sys-devel/gcc"
        keywords: [~amd64]
        use: [debug, doc]
        env:
          - 'MAKEOPTS="-j1"'
      - name: "<=sys-devel/gcc-4"
        mask:
      - name: ">=sys-devel/gcc-5"
        unmask:
```

Test
-------
```bash
ansible-playbook tests/test.yml -i tests/inventory --connection=local
```

License
-------

BSD
