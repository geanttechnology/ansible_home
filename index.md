This is a collection of Ansible roles for free software self-hosting.

This collection mainly targets individuals or eventually small companies, but is
done with professional quality standards.

These roles are done with in mind:

* Up to date and fully featured software.
* Security.
* Minimal maintenance.

To achieve well the two first points, [Fedora](https://getfedora.org/) is used
as the base OS because it always provides up to date versions of software and
advanced security feature like SELinux by default.
To again improve the security, hardening roles are applied in addition of some
security configuration.
To achieve the minimal maintenance, auto-updates (with auto-reboot, if required)
are set for all packages every day.

Of course, there are always drawbacks with all choices. In that case, it is the
risk of an update that break something and makes the service unavailable.

If you absolutely require a perfectly stable service with a 99.99% availability,
use some other role based on stabler OS like CentOS or Debian and that install
LTS software versions.
No guarantee is provided with the use of these roles.

## Roles

### Main roles

* [**common**](docs/common.md): Perform common machine initialisation task like
  configuring: auto-updates, firewall, NTP server, SSH and OS security
  hardening,...
* [**nextcloud**](docs/nextcloud.md): Install a
  [Nextcloud](https://nextcloud.com) server.
* [**kodi**](docs/kodi.md): Install a [Kodi](https://kodi.tv) home theater
  personal computer.
* [**mail**](docs/mail.md): Install a mail server using
  [Postfix](http://www.postfix.org/) and [Dovecot](https://www.dovecot.org/).
  *[Work in progress]*
* [**mpd**](docs/mpd.md): Install a
  [Music Player Daemon](https://www.musicpd.org/) server.

The **common** role is intended to be used with all other roles and may be
required by some of them.

### Dependencies roles

These roles are used as main roles dependencies:

* [**clamav**](docs/clamav.md): Install [ClamAV](https://www.clamav.net)
  antivirus.
* [**mariadb**](docs/mariadb.md): Install a [MariaDB](https://mariadb.org)
  database.
* [**nginx**](docs/nginx.md): Install a [Nginx](https://nginx.org) web server.
* [**postgresql**](docs/postgresql.md): Install a
  [PostgreSQL](https://www.postgresql.org) database.
* [**php_fpm**](docs/php_fpm.md): Install a [PHP-FPM](https://php-fpm.org)
  server.
* [**redis**](docs/redis.md): Install [Redis](https://redis.io) in memory data
  store.
* [**rpmfusion**](docs/rpmfusion.md): Enable [RPMFusion](https://rpmfusion.org)
  repositories.

## Installation

This collection is available on
[Ansible Galaxy](https://galaxy.ansible.com/jgoutin/home).

```bash
ansible-galaxy collection install jgoutin.home

# Dependencies
ansible-galaxy role install dev-sec.mysql-hardening dev-sec.nginx-hardening dev-sec.os-hardening dev-sec.ssh-hardening
```

## Example Playbook

```yaml
---
- hosts: all
  become: true
  roles:
    -  jgoutin.home.kodi
```
