# GOV.UK Toolbox
## What's in this repo

The `govuk-toolbox-image` repository defines an [OCI] container image for running ad hoc tasks on Kubernetes.

[OCI]: https://opencontainers.org/

## Building Locally
If you are on a GDS MacBook, you will need to include the ZScaler Root CA in the Docker Build Process.

First, copy the ZScaler Root CA certificate from your device keychain to `~/.docker/certs/zscaler.crt`:
```
mkdir -p ~/.docker/certs && \
security find-certificate -a -c "Zscaler" -p > ~/.docker/certs/zscaler.crt
```

Then, build the Docker Image locally using the --secret feature:
```
docker build --secret id=zscaler_ca,src=$HOME/.docker/certs/zscaler.crt -t toolbox .
```

## Maintenance
### Deployment

[release](https://github.com/alphagov/govuk-toolbox-image/blob/0fa1bb15d14185c8e42e3762a4f18c5879a96ba2/.github/workflows/release.yml) runs on a merge 
to main which tags the commit and creates a [GitHub release](https://github.com/alphagov/govuk-toolbox-image/releases) 
(e.g. `v1`). [build-and-publish-image](https://github.com/alphagov/govuk-toolbox-image/blob/0fa1bb15d14185c8e42e3762a4f18c5879a96ba2/.github/workflows/deploy.yml) 
creates and pushes both an amd64 and arm build to GHCR and ECR tagged with that version. 

### Team

[GOV.UK Platform Engineering team](https://github.com/orgs/alphagov/teams/gov-uk-platform-engineering) looks after this repo. If you're inside GDS, you can find us in [#govuk-platform-engineering](https://gds.slack.com/channels/govuk-platform-engineering) or view our [project board](https://github.com/orgs/alphagov/projects/71).

## Licence

[MIT License](LICENCE)
