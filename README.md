# gitlab-ce-subgit

Docker image: [marq/gitlab-ce-subgit](https://hub.docker.com/r/marq/gitlab-ce-subgit/)

[GitLab](http://gitlab.org)'s Community Edition, with [SubGit](http://www.subgit.com) v3.3.5 installed and `cron` running.

All of [GitLab's Docker-related documentation](http://doc.gitlab.com/omnibus/docker/) remains valid; the only difference compared to the [official Docker image(s)](https://hub.docker.com/r/gitlab/gitlab-ce/) provided by GitLab HQ is that this image contains an installation of SubGit, a tool for migrating and even mirroring subversion and git source code repositories. In addition, one more volume (`/etc/subgit`) is exposed, allowing to store SubGit related  things like a license key. Finally, the `cron` daemon is started up upon launching the image, and the corresponding system directory `/etc/cron.d` is also exported.

[Subgit's SVN to Gitlab Howto](http://www.subgit.com/gitlab.html) is a worthwhile read. Note that his Docker image only contains the SubGit software, but no configuration or license files for it. There are also no cron jobs configured.

## Volumes

`/etc/gitlab`: Configuration of the GitLab server

`/var/opt/gitlab`: Repositories

`/var/log/gitlab`: Logfiles

`/etc/subgit`: Location for subgit.key (if available, SubGit will find it there)

`/etc/cron.d`: Location for cron jobs (e.g., backups)

## Usage

For GitLab itself, see http://doc.gitlab.com/omnibus/docker/.

For SubGit and Gitlab, see http://www.subgit.com/gitlab.html.

## GitLab Versions and Tags

The images are in general tagged with the GitLab version they are based on, and follow the name naming scheme as the official releases. I handle these versioned tags manually; should I forget to update them, please raise a ticket at github. Thanks!

Finally, images with the `:latest` tag are automatically build from the official GitLab repository whenever GitLab HQ decides to push a new (even experimental) image.

## SubGit Versions

Present images are using Subgit v3.3.5 (actually since v9.5.2 of GitLab), as does the `:latest` one.

For older images, previous SubGit versions were used. In particular:

 - GitLab v9.0 up to v9.5.1: SubGit v3.2.5
 - GitLab v8.11 up to v8.17.8: SubGit v3.2.2

For a while, I was maintaining alternate images with the older v3.0.0 of SubGit included. The images can be distinguished by their tags, e.g.:

    gitlab-ee-subgit:8.11.0-ee.1:        GitLab v8.11.0 (EE), SubGit v3.2.2
    gitlab-ee-subgit:8.11.0-ee.1-3.0.0:  GitLab v8.11.0 (EE), SubGit v3.0.0

Since September 2016, however, v3.0.0 of SubGit was no longer available; hence, versions after v8.11.2 are build with the then current SubGit version.

## Related

Bertrand Roussel provides at standalone Docker image ([corfr/subgit](https://registry.hub.docker.com/u/corfr/subgit/) | [Github](https://github.com/CoRfr/docker-subgit)) for an alternative approach to use SubGit with (in fact any) dockerized git repository servers.

If you are looking for a Docker image combining GitLab's Enterprise Edition (EE) with SubGit, please check out [marq/gitlab-ee-subgit](https://hub.docker.com/r/marq/gitlab-ee-subgit/).
