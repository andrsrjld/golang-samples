# Docker Containers for golang-samples

We run tests for all supported versions of Go in Docker containers. This
directory contains `Dockerfile`s for each version of Go. You can run tests in
these containers to make sure your setup is the same as the test environment.

See [`CONTRIBUTING.md`](/CONTRIBUTING.md),
[`system_tests.sh`](/testing/kokoro/system_tests.sh), and the `.cfg` files in
[`/testing/kokoro`](/testing/kokoro).

When new minor versions are released, we should build and push new versions of
these repos.

```
gcloud config set project golang-samples-tests
for d in `find . -type d`; do
  cd $d
  gcloud builds submit gcr.io/golang-samples-tests/$d
  cd -
done
```