# PHP application stack for Kubernetes on Wodby

Deploy PHP applications on Kubernetes with Wodby.

This repository defines the Wodby stack manifests and default service
composition for PHP.

- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Start from a template

Use one of the compatible source templates exposed by this stack's services to
start with Wodby CI build configuration:

- [Composer boilerplate](https://github.com/wodby/php-package-boilerplate)

## Service definitions

- [PHP service](https://github.com/wodby/service-php)
- [Nginx (PHP) service](https://github.com/wodby/service-php-nginx)
- [MariaDB service](https://github.com/wodby/service-mariadb)
- [Apache HTTP server (PHP) service](https://github.com/wodby/service-php-httpd)
- [PostgreSQL service](https://github.com/wodby/service-postgres)
- [Valkey service](https://github.com/wodby/service-valkey)
- [Mailpit service](https://github.com/wodby/service-mailpit)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)
- [Gotenberg service](https://github.com/wodby/service-gotenberg)

## What's included

| Component / service | Default configuration |
| --- | --- |
| PHP<br>`php` | required; enabled by default; links: `db` → `mariadb`, `sendmail` → `mailpit` |
| Nginx<br>`php-nginx` | required; enabled by default; links: `backend` → `php` |
| MariaDB<br>`mariadb` | optional; enabled by default; volumes: `data` 20 GB |
| Apache HTTP server (`httpd`)<br>`php-httpd` | optional; disabled by default; links: `backend` → `php` |
| PostgreSQL (`postgres`)<br>`postgres` | optional; disabled by default; volumes: `data` 20 GB |
| Valkey<br>`valkey` | optional; disabled by default |
| Mailpit<br>`mailpit` | optional; enabled by default |
| OpenSMTPD<br>`opensmtpd` | optional; disabled by default |
| Gotenger (`gotenberg`)<br>`gotenberg` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Deploy this stack

Start from [Composer boilerplate](https://github.com/wodby/php-package-boilerplate), or connect your own compatible source
repository.

Review service versions, storage, links, and optional components when creating
the application. The same stack can be reused across development, staging, and
production environments.

## Maintain a custom version

1. Fork this repository.
2. Edit the stack manifest.
3. Import the repository as a [Git-backed stack](https://wodby.com/docs/2.0/stacks/create/#create-a-git-backed-stack).

When replacing or renaming a stack service, update every related link target
and derivative reference. Stack-local names and referenced service names are
distinct identifiers.

Validate the manifests with:

```bash
wodby stack validate-manifest stack.yml --org <org-id>
```

See the [stack manifest reference](https://wodby.com/docs/2.0/stacks/template/) and the [managed services index](https://github.com/wodby/services).
