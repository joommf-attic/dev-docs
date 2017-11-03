# Updating packages etc

## Release new version on PyPI

This is the process for the "code" repository in
https://github.com/joommf, for example
https://github.com/joommf/discretisedfield :

- make changes as required
- edit `setup.py` and increase version number
- `git tag -a X.Y.Z -m "update version number / major new feature"`
- run `make release` to upload new version to PyPI

PyPI webpage for example:https://pypi.python.org/pypi/discretisedfield


## Update conda-forge package

Once the PyPI is updated, we can rebuild the conda packages:

- Find the conda-forge repository (conda-forge/<package>-feedstock), for our example:
  https://github.com/conda-forge/discretisedfield-feedstock

- fork the repository

- edit `recipe/meta.yml`:
  - update version number
  - update sha256 key
    (run `openssl sha256 <tarfile>` on the tar file we can download from the pypi page)
  - update build number if version number doesn't change, reset to 0 otherwise
- create pull request
- if all tests pass, merge

## Docker images

### `joommf/oommf` image

- https://hub.docker.com/r/joommf/oommf/
- provides OOMMF compiled from source
- Dockerfile to create this image is at https://github.com/fangohr/oommf/tree/master/docker/oommf

### `joommf/joommf` image

- https://hub.docker.com/r/joommf/joommf/
- provides complete JOOMMF installation
- XXX Dockerfile location?
- use case?

### `joommf/tryjoommf` image

- https://hub.docker.com/r/joommf/tryjoommf/
- container that is used in jupyter hub installation (http://tryjoommf.soton.ac.uk)
- Dockerfile at https://github.com/joommf/try-joommf-deploy/tree/master/joommf-docker-image
