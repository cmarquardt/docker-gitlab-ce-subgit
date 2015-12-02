# gitlab-ce-subgit

Image: [marq/gitlab-ce-subgit](https://hub.docker.com/r/marq/gitlab-ce-subgit/)

[GitLab](http://gitlab.org)'s Community Edition, with [SubGit](http://www.subgit.com) installed.

All of [GitLab's Docker-related documentation](http://doc.gitlab.com/omnibus/docker/) remains valid; the only difference compared to the official Docker images provided by GitLabHQ is that the image contains an installation of SubGit, a tool for migrating and even mirroring subversion and git source code repositories. In addition, one more volume (`/etc/subgit`) is exposed, allowing to store SubGit related  things like a license key.

[Subgit's SVN to Gitlab Howto](http://www.subgit.com/gitlab.html) is a worthwhile read.

## Volumes

`/etc/gitlab`: Configuration of the SubGit server

`/var/opt/gitlab`: Repositories

`/var/log/gitlab`: Logfiles

`/etc/subgit`: Location for subgit.key (if available; SubGit will find it there)

`/etc/cron.d`: Location for cron jobs (e.g., backups; see below)

## Usage

For GitLab itself, see http://doc.gitlab.com/omnibus/docker/.

For SubGit and Gitlab, see http://www.subgit.com/gitlab.html.

In contrast to the original image, the cron daemon is also launched when starting up GitLab. This allows processing of cron jobs added to /etc/cron.d. 

## Tags

Note that the tag `:latest` is automatically build from the official GitLab repository; whenever GitlabHQ decides to push a new (even experimental) image. I handle versioned tags manually, based on officially tagged images as available in the Official GitLab repository. Should I forget to update, please raise a ticket at github. Thanks!

## Related

Bertrand Roussel provides at standalone Docker image ([corfr/subgit](https://registry.hub.docker.com/u/corfr/subgit/) | [Github](https://github.com/CoRfr/docker-subgit)) for an alternative approach to use SubGit with (in fact any) dockerized git repository servers.
