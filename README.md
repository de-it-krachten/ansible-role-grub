[![CI](https://github.com/de-it-krachten/ansible-role-grub/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-grub/actions?query=workflow%3ACI)


# ansible-role-grub

Configures grub password



## Dependencies

#### Roles
None

#### Collections
None

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- Red Hat Enterprise Linux 10<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- RockyLinux 10
- OracleLinux 8
- OracleLinux 9
- OracleLinux 10
- AlmaLinux 8
- AlmaLinux 9
- AlmaLinux 10
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Debian 13 (Trixie)
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Ubuntu 26.04 LTS
- Fedora 43
- Fedora 44<sup>1</sup>

Note:
<sup>1</sup> : no automated testing is performed on these platforms


## Role Variables
### defaults/main.yml
<pre><code>
# Grub user
# grub_user: boot

# Grub password
# grub_password: boot

# Grub password salt
# grub_salt: abcd1234
</pre></code>

### defaults/family-Debian.yml
<pre><code>
grub_packages:
  - grub-common
  - grub2-common
  - python3-pexpect

grub_password_tool: grub-mkpasswd-pbkdf2
</pre></code>

### defaults/family-RedHat.yml
<pre><code>
grub_packages:
  - grub2-tools
  - python3-pexpect

grub_password_tool: grub2-mkpasswd-pbkdf2
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'grub'
  hosts: all
  become: 'yes'
  vars:
    molecule_driver: '{{ lookup(''env'', ''MOLECULE_DRIVER_NAME'') }}'
    grub_user: boot
    grub_password: boot
    grub_salt: abcd1234
  tasks:
    - name: Include role 'grub'
      ansible.builtin.include_role:
        name: grub
</pre></code>
