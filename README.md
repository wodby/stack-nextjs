# Next.js application stack for Kubernetes on Wodby

Deploy Next.js applications on Kubernetes with Wodby.

This repository defines the Wodby stack manifests and default service
composition for Next.js.

- [Browse Wodby application stacks](https://wodby.com/stacks)
- [Wodby stack documentation](https://wodby.com/docs/2.0/stacks/)
- [Stack manifest reference](https://wodby.com/docs/2.0/stacks/template/)

## Start from a template

Use one of the compatible source templates exposed by this stack's services to
start with Wodby CI build configuration:

- [Next.js Boilerplate](https://github.com/wodby/nextjs-boilerplate)

## Service definitions

- [Node.js (Next.js) service](https://github.com/wodby/service-nextjs)
- [PostgreSQL service](https://github.com/wodby/service-postgres)
- [Valkey service](https://github.com/wodby/service-valkey)
- [Mailpit service](https://github.com/wodby/service-mailpit)
- [OpenSMTPD service](https://github.com/wodby/service-opensmtpd)
- [Gotenberg service](https://github.com/wodby/service-gotenberg)

## What's included

| Component / service | Default configuration |
| --- | --- |
| Node.js (`nextjs`)<br>`nextjs` | required; enabled by default; links: `db` → `postgres`, `redis` → `valkey`, `sendmail` → `mailpit` |
| PostgreSQL (`postgres`)<br>`postgres` | optional; disabled by default; volumes: `data` 10 GB |
| Valkey<br>`valkey` | optional; disabled by default |
| Mailpit<br>`mailpit` | optional; disabled by default |
| OpenSMTPD<br>`opensmtpd` | optional; disabled by default |
| Gotenberg<br>`gotenberg` | optional; disabled by default |

Enabled optional services are selected by default but can be excluded when an
app is created. Disabled optional services are available but not selected by
default. Required services cannot be excluded.

## Deploy this stack

Start from [Next.js Boilerplate](https://github.com/wodby/nextjs-boilerplate), or connect your own compatible source
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
