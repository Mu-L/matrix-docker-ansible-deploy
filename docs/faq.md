<!--
SPDX-FileCopyrightText: 2021 - 2022 MDAD project contributors
SPDX-FileCopyrightText: 2021 - 2024 Slavi Pantaleev
SPDX-FileCopyrightText: 2022 Julian-Samuel Gebühr
SPDX-FileCopyrightText: 2022 László Várady
SPDX-FileCopyrightText: 2024 - 2025 Suguru Hirahara
SPDX-FileCopyrightText: 2024 Nikita Chernyi
SPDX-FileCopyrightText: 2024 Uğur İLTER

SPDX-License-Identifier: AGPL-3.0-or-later
-->

# Frequently Asked Questions

This documentation page tries to answer various Frequently Asked Questions about all things [Matrix](https://matrix.org/), with a focus on this [Ansible](https://www.ansible.com/) playbook ([What is Ansible? How does it work?](#what-is-ansible-how-does-it-work)).

This FAQ page does not intend to replace the [matrix.org FAQ](https://matrix.org/faq/) (please see that one too).

We've only started this FAQ recently, so it's still somewhat empty.

Also, we encourage you to not dig yourself into a hole by reading way too much. When you've heard enough, proceed to installation. To get started, see [below](#how-do-i-run-the-installation) about our installation guides.

## Introductory

### Where do I find more questions and answers about Matrix?

This is a Frequently Asked Questions page focused on this [Ansible](https://www.ansible.com/) playbook ([What is Ansible? How does it work?](#what-is-ansible-how-does-it-work)) for deploying a [Matrix](https://matrix.org/) server.

For a lot more generic questions and answers, see the [matrix.org FAQ](https://matrix.org/faq/).

### What is Matrix? What is Element? What is Synapse? Why are you confusing me with so many terms?

[Matrix](https://matrix.org/) is a new type of realtime communication (chat) network, the closest analogy to which is probably "email".

You don't just use the "email" protocols (SMTP, POP3, IMAP) directly though. There's a *server* somewhere which stores your data (`@gmail.com`, `@yahoo.com`, `@hotmail.com`, `@your-company.com`) and you access it by using these "email" protocols via some *client* program (Outlook, Thunderbird, some website, etc).

In the world of the Matrix chat protocol, there are various client programs. The first and currently most full-featured one is called [Element](https://element.io/) (used to be called Riot.im and Vector.im in the past). There are [many other clients](https://matrix.org/clients/). You can switch clients as much as you want until you find the one that is right for you on a given platform (you may use Element Desktop on your desktop, but Fluffychat on your phone, etc).

Matrix is also like email due to the fact that there are many servers around the world which can all talk to each other (you can send email from `@gmail.com` addresses to `@yahoo.com` and `@hotmail.com` addresses). It's the same with Matrix (`@bob:example.com` can talk to `@alice:example.org`).

If someone else is hosting your Matrix server (you being `@alice:matrix.org` or some other public server like this), all you need is a Matrix client program, like Element Web or Element X Android.

If you'd like to host your own server (you being `@alice:example.com`), you'd need to set up a Matrix server program, like Synapse.

In short:

- Matrix is the protocol — a set of rules about how the chat network operates
- Element is a client program you can use to participate on the Matrix chat network via some server (yours or someone else's). There are also [many other client programs](https://matrix.org/clients/).
- Synapse is a server program you can use to host your very own Matrix server.

This FAQ here mostly focuses on installing various Matrix services using the Ansible automation tool. You can learn much more about Matrix in the [matrix.org FAQ](https://matrix.org/faq/).

### People I wish to talk to are not on Matrix. Can I talk to them?

You most likely can. Besides Matrix-native chats, Matrix also supports the concept of "bridging", which allows you to plug other networks into it.

This Ansible playbook can help you install [tens of bridges for various networks](configuring-playbook.md#bridging-other-networks).

Besides setting up your own bridges (preferable), you can also use some [public bridges hosted by others](https://publiclist.anchel.nl/#bridges).

### How do I get started with Matrix?

One of [Matrix](https://matrix.org/)'s distinguishing strengths (compared to other chat networks) is its decentralized nature. There's not just one entity (company, organization) controlling the servers. Rather there's thousands of servers operated by different people — one server being insecure, slow or disrespective toward its users does not affect the rest of the network. To participate in that decentralization in its fullest, consider hosting your own server or using some public server other than the largest/default one (`matrix.org`).

There are 3 ways to get into Matrix, depending on your technical ability and needs:

- **using the existing default server** — the easiest way is to use an existing server. The largest public Matrix server is `matrix.org` and it's configured as a default server in clients such as [Element Web](https://app.element.io) and many others. Just use Element Web on the browser via that link (or [download client apps for your Desktop or smartphone](https://element.io/app-for-productivity)), create an account and start chatting.

- **using some other server** — instead of using the largest public server (`matrix.org`), you can use another public one. Here's a [list of public Matrix servers](https://joinmatrix.org/servers/) to choose from. Go to [Element Web](https://app.element.io) or download [some other client](https://matrix.org/clients/) of your choosing and adjust the homeserver URL during login.

- **using your own server** — running your own server puts you in ultimate control of your data. It also lets you have your own user IDs (e.g. `@bob:example.com`). See [How do I set up my own Matrix server](#how-do-i-set-up-my-own-matrix-server).

### How do I set up my own Matrix server?

Normally, you'd first choose the [Matrix](https://matrix.org/) server software you'd like to run. At the time of this writing (January/2021), there's only one fully-featured server program, so there's only one reasonable choice. That's [Synapse](https://github.com/element-hq/synapse).

There are [many guides about installing Synapse](https://matrix.org/docs/guides/#installing-synapse). Using this Ansible playbook is just one way of doing it.

Naturally, we're biased, so our usual recommendation is to go with this [Ansible](https://www.ansible.com/) playbook, instead of installing Synapse (and many many other things around it) manually.

To get started with the playbook, check out the [Quick start](quick-start.md) or full installation guide (starting at the [Prerequisites](prerequisites.md) page).

### What is Ansible? How does it work?

[Ansible](https://www.ansible.com/) is an automation program. This "playbook" is a collection of tasks/scripts that will set up a [Matrix](https://matrix.org/) server for you, so you don't have to perform these tasks manually.

We have written these automated tasks for you and all you need to do is execute them using the Ansible program.

You can install Ansible and this playbook code repository on your own computer and tell it to install Matrix services at the server living at `matrix.example.com`. We recommend installing Ansible on your own computer.

Alternatively, you can download Ansible and the playbook itself directly on the `matrix.example.com` server.

To learn more, see our [dedicated Ansible documentation page](ansible.md).

### What is `just`?

[`just`](https://github.com/casey/just) is a modern command-runner alternative to [make](https://www.gnu.org/software/make/). It can be used to invoke commands with less typing.

The `just` utility executes shortcut commands (called "recipes"), which invoke `ansible-playbook`, `ansible-galaxy` or [`agru`](https://github.com/etkecc/agru) (depending on what is available in your system). The targets of the recipes are defined in [`justfile`](../justfile).

For details about `just` commands, take a look at: [Running `just` commands](just.md).

The playbook also contains a `Makefile` for the `make` tool, but most of the just recipes are not available as targets in the `Makefile`.

### Why use this playbook and not install Synapse and other things manually?

There are various guides telling you how easy it is to install [Synapse](https://github.com/element-hq/synapse).

Reading the documentation of this Ansible playbook, you may also be thinking:

> I don't know what [Ansible](https://www.ansible.com/) is. I don't know what [Docker](https://www.docker.com/) is. This looks more complicated.

… so you may be leaning toward [installing Synapse manually](https://github.com/element-hq/synapse/blob/master/INSTALL.md).

The problem with a manual installation is:

- Synapse is written in Python. If not packaged for your distribution, you'd need to install various Python modules, etc., and keep them updated.
- Synapse requires a [Postgres](https://www.postgresql.org/) database (it can run on SQLite, but that's very much discouraged). So you'd need to install Postgres as well.
- you may also need a reverse-proxy server in front of it (nginx, Apache), so you'd need to be familiar with that
- SSL is required, so you'd need to obtain Let's Encrypt (or other free or non-free) certificates for one or more domain names. You'd need to be familiar with [certbot](https://certbot.eff.org/) (when using Let's Encrypt) or similar software.
- for each additional component you'd like to add (client like [Element](https://element.io), bridge to some other chat network, integration manager (stickers, other services, Identity Manager, etc.), you'll need to spend extra time installing and wiring it with the rest of the system in a way that works.
- you'll likely get slower updates for all of these components, depending on your distro packaging or your own time and ability

The playbook, on the other hand, installs a bunch of components for you by default, obtains SSL certificates for you, etc. If you'd like, you can enable various bridges and other services with very little effort. All the components are wired to work together.

All services run in Docker containers (most being officially provided by each component's developers), so we're not at the mercy of distro packaging.

### Why use this playbook and not just use the Docker image directly?

Reasons are similar to the reasons for not installing manually.

Besides Synapse, you'd need other things — a Postgres database, likely the [Element](https://element.io) client, etc., etc.

Using the playbook, you get all these components in a way that works well together out of the box.

### Occasionally I see some people are talking about "MDAD". What is it?

It is the acronym of us: **m**atrix-**d**ocker-**a**nsible-**d**eploy.

### What's different about this Ansible playbook compared to [EMnify/matrix-synapse-auto-deploy](https://github.com/EMnify/matrix-synapse-auto-deploy)?

This is similar to the [EMnify/matrix-synapse-auto-deploy](https://github.com/EMnify/matrix-synapse-auto-deploy) Ansible deployment, but:

- this one is a complete Ansible playbook (instead of just a role), so it's **easier to run** — especially for folks not familiar with Ansible

- this one installs and hooks together **a lot more Matrix-related services** for you (see above)

- this one **can be executed more than once** without causing trouble

- works on various distros: **CentOS** (7.0+), Debian-based distributions (**Debian** 10/Buster+, **Ubuntu** 18.04+), **Archlinux**

- this one installs everything in a single directory (`/matrix` by default) and **doesn't "contaminate" your server** with files all over the place

- this one **doesn't necessarily take over** ports 80 and 443. By default, it sets up [Traefik](https://doc.traefik.io/traefik/) for you there, but you can also [use your own webserver](configuring-playbook-own-webserver.md)

- this one **runs everything in Docker containers**, so it's likely more predictable and less fragile (see [Docker images used by this playbook](container-images.md))

- this one retrieves and automatically renews free [Let's Encrypt](https://letsencrypt.org/) **SSL certificates** for you

- this one optionally can store the `media_store` content repository files on [Amazon S3](https://aws.amazon.com/s3/) (but defaults to storing files on the server's filesystem)

- this one optionally **allows you to use an external PostgreSQL server** for Synapse's database (but defaults to running one in a container)

- helps you **import data from a previous installation** (so you can migrate your manual virtualenv/Docker setup to a more managed one)

- this one is actually **maintained**

## Server-related

### What kind of server do I need to install Matrix using this Ansible playbook?

We list our server requirements in [Prerequisites](prerequisites.md).

### Why not run Matrix on Kubernetes?

There's no reason not to run Matrix on [Kubernetes](https://kubernetes.io/).

However, that's overly complicated for thousands of us who just want to run a single small (and sometimes not so small) Matrix server, either using "cloud" servers or even a [Raspberry Pi](https://www.raspberrypi.org/) at home.

For us, a Kubernetes-based setup which requires a cluster of multiple computers and is more technically-involved is a no-go.

There are others working on automating a Matrix-on-Kubernetes setup, such as this [Helm](https://helm.sh/) chart: https://github.com/dacruz21/matrix-chart.

### Why don't you use Podman instead of Docker?

We like the philosophy of a daemonless container runtime, but [Podman](https://podman.io) is just not ready for our use case yet.

Learn more about our past experiences/attempts to give Podman a chance, by reading [this issue](https://github.com/spantaleev/matrix-docker-ansible-deploy/issues/520).

In short, `alias podman=docker` is a lie (for us).

### Why use Docker?

[Docker](https://www.docker.com/) is one of our 2 hard dependencies (the other one being [systemd](https://systemd.io/)).

It lets us run services in an isolated manner and independently of the (usually old) packages available for distributions.

It also lets us have a unified setup which runs the same across various supported distros (see them on [Prerequisites](prerequisites.md)).

### Is Docker a hard requirement?

Yes. See [Why don't you use Podman instead of Docker?](#why-dont-you-use-podman-instead-of-docker) for why we're not using another container runtime.

All of our services run in containers. It's how we achieve predictability and also how we support tens of different services across lots of distros.

The only thing we need on the distro is systemd and Python (we install Docker ourselves, unless you ask us not to).

### Why don't you use docker-compose?

Instead of using [docker-compose](https://docs.docker.com/compose/), we prefer installing systemd services and scheduling those independently.

There are people who have worked on turning this setup into a docker-compose-based one. See these experiments [here](https://github.com/spantaleev/matrix-docker-ansible-deploy/issues/64#issuecomment-603164625). There is also a demo project ([element-docker-demo](https://github.com/element-hq/element-docker-demo)) by Element.

### Can I run this on a distro without systemd?

No. [systemd](https://systemd.io/) is one of our 2 hard dependencies (the other one being [Docker](https://www.docker.com/)).

### Can I install this on a Raspberry Pi?

Yes, you can. See our [Alternative Architectures](alternative-architectures.md) documentation page.

Whether a Raspberry Pi has enough power to give you a good experience is another question. It depends on your use case.

Also see: [What kind of server specs do I need?](#what-kind-of-server-specs-do-i-need).

### What kind of server specs do I need?

This largely depends on your use case. It's not so much the number of users that you plan to host, but rather the number of large rooms they will join.

Federated rooms with lots of history and containing hundreds of other servers are very heavy CPU-wise and memory-wise.

You can probably use a 1 CPU + 1GB memory server to host hundreds of local users just fine, but as soon as one of them joins a federated room like `#matrix:matrix.org` (Matrix HQ) or some IRC-bridged room (say `##linux`), your server will get the need for a lot more power (at least 2GB RAM, etc).

Running Matrix on a server with 1GB of memory is possible (especially if you disable some not-so-important services). See [How do I optimize this setup for a low-power server?](#how-do-i-optimize-this-setup-for-a-low-power-server).

**We recommend starting with a server having at least 2GB of memory** and even then using it sparingly. If you know for sure you'll be joining various large rooms, etc., then going for 4GB of memory or more is a good idea.

Besides the regular Matrix stuff, we also support things like video-conferencing using [Jitsi](configuring-playbook-jitsi.md) and other additional services which (when installed) may use up a lot of memory. Things do add up. Besides the Synapse Matrix server, Jitsi is especially notorious for consuming a lot of resources. If you plan on running Jitsi, we recommend a server with at least 2GB of memory (preferably more). See our [Jitsi documentation page](configuring-playbook-jitsi.md) to learn how to optimize its memory/CPU usage.

### Can I run this in an LXC container?

If your distro runs within an [LXC container](https://linuxcontainers.org/), you may hit [this issue](https://github.com/spantaleev/matrix-docker-ansible-deploy/issues/703). It can be worked around, if absolutely necessary, but we suggest that you avoid running from within an LXC container.

## Configuration

### Why install my server at matrix.example.com and not at the base domain?

It's the same with email servers. Your email address is likely `name@company.com`, not `name@mail.company.com`, even though it's `mail.company.com` that is really handling your data for `@company.com` email to work.

Using a separate domain name is easier to manage (although it's a little hard to get right at first) and keeps your Matrix server isolated from your website (if you have one), from your email server (if you have one), etc. Therefore, this playbook sets up services on your Matrix server (`matrix.example.com`) by default.

### I don't control anything on the base domain and can't set up delegation to matrix.example.com. What do I do?

If you're not in control of your base domain (or the server handling it) at all, you can take a look at [How do I install on matrix.example.com without involving the base domain?](#how-do-i-install-on-matrixexamplecom-without-involving-the-base-domain)

### I can't set up HTTPS on the base domain. How will I get Matrix federating?

If you really can't obtain an HTTPS certificate for your base domain, you can take a look at [How do I install on matrix.example.com without involving the base domain?](#how-do-i-install-on-matrixexamplecom-without-involving-the-base-domain)

### How do I install on matrix.example.com without involving the base domain?

Add the following configuration to your `inventory/host_vars/matrix.example.com/vars.yml` file:

```yaml
# This is what your identifiers are like (e.g. `@bob:matrix.example.com`).
matrix_domain: "matrix.example.com"

# This is where Matrix services
matrix_server_fqn_matrix: "matrix.example.com"

# This is where you access the Element Web from (if enabled via `matrix_client_element_enabled: true`; enabled by default).
# This and the Matrix FQN (see above) are expected to be on the same server.
#
# Feel free to use `element.matrix.example.com`, if you'd prefer that.
matrix_server_fqn_element: "element.example.com"

# This is where you access Etherpad (if enabled via `etherpad_enabled: true`; NOT enabled by default).
#
# Feel free to use `etherpad.matrix.example.com`, if you'd prefer that.
matrix_server_fqn_etherpad: "etherpad.example.com"
```

After configuring the playbook, run it with [playbook tags](playbook-tags.md) as below:

<!-- NOTE: let this conservative command run (instead of install-all) to make it clear that failure of the command means something is clearly broken. -->
```sh
ansible-playbook -i inventory/hosts setup.yml --tags=setup-all,start
```

**Notes**:

- The shortcut commands with the [`just` program](just.md) are also available: `just install-all` or `just setup-all`

  `just install-all` is useful for maintaining your setup quickly ([2x-5x faster](../CHANGELOG.md#2x-5x-performance-improvements-in-playbook-runtime) than `just setup-all`) when its components remain unchanged. If you adjust your `vars.yml` to remove other components, you'd need to run `just setup-all`, or these components will still remain installed. Note these shortcuts run the `ensure-matrix-users-created` tag too.

- Without setting up [server delegation](howto-server-delegation.md) to `matrix.example.com`, your user IDs will be like `@alice:matrix.example.com`. This is equivalent to having an email address like `bob@mail.company.com`, instead of just `bob@company.com`.

### I don't use the base domain for anything. How am I supposed to set up Server Delegation for Matrix services?

If you don't use your base domain for anything, then it's hard for you to "serve files over HTTPS" on it — something we ask you to do for the [.well-known](configuring-well-known.md) setup (needed for [Server Delegation](howto-server-delegation.md)).

Luckily, the playbook can set up your Matrix server (at `matrix.example.com`) to also handle traffic for the base domain (`example.com`).

See [Serving the base domain](configuring-playbook-base-domain-serving.md).

### How do I optimize this setup for a low-power server?

You can disable some not-so-important services to save on memory.

```yaml
# Disabling this will prevent email-notifications and other such things from working.
exim_relay_enabled: false

# You can also disable this to save more RAM,
# at the expense of audio/video calls being unreliable.
matrix_coturn_enabled: false

# This makes Synapse not keep track of who is online/offline.
#
# Keeping track of this and announcing such online-status in federated rooms with
# hundreds of servers inside is insanely heavy (https://github.com/matrix-org/synapse/issues/3971).
#
# If your server does not federate with hundreds of others, enabling this doesn't hurt much.
matrix_synapse_presence_enabled: false
```

You can also consider implementing a restriction on room complexity, in order to prevent users from joining very heavy rooms:

```yaml
matrix_synapse_configuration_extension_yaml: |
  limit_remote_rooms:
    enabled: true
    complexity: 1.0 # this limits joining complex (~large) rooms, can be
					# increased, but larger values can require more RAM
```

If you've installed [Jitsi](configuring-playbook-jitsi.md) (not installed by default), there are additional optimizations listed on its documentation page that you can perform.

### I already have Docker on my server. Can you stop installing Docker via the playbook?

Yes, we can stop installing Docker ourselves. Just use this in your `vars.yml` file:

```yaml
matrix_playbook_docker_installation_enabled: false
```

### I run another webserver on the same server where I wish to install Matrix. What now?

By default, we install a webserver for you ([Traefik](https://doc.traefik.io/traefik/)), but you can also use [your own webserver](configuring-playbook-own-webserver.md).

### How is the effective configuration determined?

Configuration variables are defined in multiple places in this playbook and are considered in this order:

- there are defaults coming from each role's defaults file (`role/matrix*/defaults/main.yml`). These variable values aim to be good defaults for when the role is used standalone (outside of this collection of roles, also called playbook).

- then, there are overrides in `group_vars/matrix_servers`, which aim to adjust these "standalone role defaults" to something which better fits the playbook in its entirety.

- finally, there's your `inventory/host_vars/matrix.example.com/vars.yml` file, which is the ultimate override

### What configuration variables are available?

You can discover the variables you can override in each role (`roles/*/*/defaults/main.yml`).

As described in [How is the effective configuration determined?](#how-is-the-effective-configuration-determined), these role-defaults may be overridden by values defined in `group_vars/matrix_servers`.

Refer to both of these for inspiration. Still, as mentioned in [Configuring the playbook](configuring-playbook.md), you're only ever supposed to edit your own `inventory/host_vars/matrix.example.com/vars.yml` file and nothing else inside the playbook (unless you're meaning to contribute new features).

**Note**: some of the roles (`roles/galaxy/*`) live in separate repositories and are only installed after your run `just roles` (or `make roles`) or `just update` (which automatically does `git pull` and `just roles`).

### I'd like to adjust some configuration which doesn't have a corresponding variable. How do I do it?

The playbook doesn't aim to expose all configuration settings for all services using variables. Doing so would amount to hundreds of variables that we have to create and maintain.

Instead, we only try to make some important basics configurable using dedicated variables you can see in each role. See [What configuration variables are available?](#what-configuration-variables-are-available).

Besides that, each role (component) aims to provide a `matrix_SOME_COMPONENT_configuration_extension_yaml` (or `matrix_SOME_COMPONENT_configuration_extension_json`) variable, which can be used to override the configuration.

Check each role's `roles/*/*/defaults/main.yml` for the corresponding variable and an example for how use it.

**Note**: some of the roles (`roles/galaxy/*`) live in separate repositories and are only installed after your run `just roles` (or `make roles`) or `just update` (which automatically does `git pull` and `just roles`).

## Installation

### How do I run the installation?

See [Installing](installing.md) to learn how to use Ansible to install Matrix services.

However, we recommend you to follow our installation guide, instead of jumping straight to installing.

There are two guides available:

- ⚡ **[Quick start](quick-start.md)** (for beginners): this is recommended for those who do not have an existing Matrix server and want to start quickly with "opinionated defaults".

- **Full installation guide (for advanced users)**: if you need to import an existing Matrix server's data into the new server or want to learn more while setting up the server, follow this guide by starting with the **[Prerequisites](prerequisites.md)** documentation page.

### I installed Synapse some other way. Can I migrate such a setup to the playbook?

Yes, you can.

You generally need to do a playbook installation. It's recommended to follow the full installation guide (starting at the [Prerequisites](prerequisites.md) page), not the [Quick start](quick-start.md) guide. The full installation guide will tell you when it's time to import your existing data into the newly-prepared server.

This Ansible playbook guides you into installing a server for `example.com` (user IDs are like this: `@alice:example.com`), while the server is at `matrix.example.com`. If your existing setup has a server name (`server_name` configuration setting in Synapse's `homeserver.yaml` file) other than the base `example.com`, you may need to tweak some additional variables. This FAQ entry may be of use if you're dealing with a more complicated setup — [How do I install on matrix.example.com without involving the base domain?](#how-do-i-install-on-matrixexamplecom-without-involving-the-base-domain)

After configuring the playbook and installing and **before starting** services (done with `ansible-playbook … --tags=start`) you'd import [your SQLite](importing-synapse-sqlite.md) (or [Postgres](importing-postgres.md)) database and also [import your media store](importing-synapse-media-store.md).

### I've downloaded Ansible and the playbook on the server. It can't connect using SSH.

If you're using the playbook directly on the server, then Ansible doesn't need to connect using SSH.

It can perform a local connection instead. Just set `ansible_connection=local` at the end of the server line in `inventory/hosts` and re-run the playbook.

If you're running Ansible from within a container (one of the possibilities we list on our [dedicated Ansible documentation page](ansible.md)), then using `ansible_connection=local` is not possible.

## Maintenance and Troubleshooting

💡 Also see this page for generic information about maintaining the services and troubleshooting: [Maintenance and Troubleshooting](maintenance-and-troubleshooting.md)

### Do I need to do anything to keep my Matrix server updated?

Yes. We don't update anything for you automatically.

See our [documentation page about upgrading services](maintenance-upgrading-services.md).

### How do I move my existing installation to another (VM) server?

If you have an existing installation done using this Ansible playbook, you can easily migrate that to another server following [our dedicated server migration guide](maintenance-migrating.md).

If your previous installation is done in some other way (not using this Ansible playbook), see [I installed Synapse some other way. Can I migrate such a setup to the playbook?](#i-installed-synapse-some-other-way-can-i-migrate-such-a-setup-to-the-playbook).

### What is this `/matrix/postgres/data-auto-upgrade-backup` directory that is taking up so much space?

When you [perform a major Postgres upgrade](maintenance-postgres.md#upgrading-postgresql), we save the the old data files in `/matrix/postgres/data-auto-upgrade-backup`, just so you could easily restore them should something have gone wrong.

After verifying that everything still works after the Postgres upgrade, you can safely delete `/matrix/postgres/data-auto-upgrade-backup`

### I get "Error response from daemon: configured logging driver does not support reading" when I run `docker logs matrix-synapse`. Why?

To prevent double-logging, Docker logging is disabled by explicitly passing `--log-driver=none` to all containers. Due to this, you cannot view logs using `docker logs matrix-*`.

See [this section](maintenance-and-troubleshooting.md#how-to-see-the-logs) on the page for maintenance and troubleshooting for more details to see the logs.

## Miscellaneous

### I would like to see this favorite service of mine integrated and become available on my Matrix server. How can I request it?

You can freely create an issue for feature request on the repository at GitHub [here](https://github.com/spantaleev/matrix-docker-ansible-deploy/issues/new/choose). Note this is a community project with no financial backing, and there is not assurance that your request would be eventually picked up by others and the requested feature would become available. The easiest way to get a feature into this project is to just develop it yourself.

Also, please note that this playbook intends to focus solely on Matrix and Matrix-related services. If your request is not specific to Matrix, you may as well to consider to submit it to the [mash-playbook](https://github.com/mother-of-all-self-hosting/mash-playbook), maintained by the members behind this matrix-docker-ansible-deploy project. [This document on the interoperability](https://github.com/mother-of-all-self-hosting/mash-playbook/blob/main/docs/interoperability.md) describes how to deploy services along with the Matrix services easily.
