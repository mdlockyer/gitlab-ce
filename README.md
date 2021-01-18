# Unraid Docker templates

## GitLab-CE

This template is built from the GitLab-CE Omnibus package, and should work out of the box.

### Pre-configuring the container with Unraid's *Extra Parameters* field

To setup the GitLab-CE docker container with an external URL, some extra setup is required. This section documents the additional `docker run` parameters that are needed. In Unraid, additional `run` arguments are provided using the `Extra Parameters` field in the GUI.

You can pre-configure the GitLab container by adding the environment variable `GITLAB_OMNIBUS_CONFIG` to the Docker run command. This variable can contain any `gitlab.rb` setting and is evaluated before the loading of the container’s `gitlab.rb` file.

Here's an example for configuring GitLab to use an external URL using the `GITLAB_OMNIBUS_CONFIG` environment variable in Unraid's `Extra Parameters` field:

`--hostname my.domain.com --env GITLAB_OMNIBUS_CONFIG="external_url 'http://my.domain.com/';"`

More information about pre-configuring the GitLab Docker container can be found [here](https://docs.gitlab.com/omnibus/docker/#use-tagged-versions-of-gitlab)

#### Generating SSL/TLS Certificates

The Gitlab Omnibus ships with Let’s Encrypt in the package. If you want to use this container on Unraid with another Let’s Encrypt service (E.g., SWAG) then the `GITLAB_OMNIBUS_CONFIG` environment variable added to the `Extra Parameters` field in the Unraid GUI needs to include the `gitlab.rb` setting `letsencrypt['enable'] = false`.