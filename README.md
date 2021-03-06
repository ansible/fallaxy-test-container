# Ansible Galaxy stub server

[![Docker Repository on Quay](https://quay.io/repository/ansible/fallaxy-test-container/status "Docker Repository on Quay")](https://quay.io/repository/ansible/fallaxy-test-container)

A mock server of both Ansible Galaxy and Automation Hub to use for CI testing.
It will henceforth be now known as Fallaxy Server.

## Usage

To use locally run the following

```
docker run --rm -p 8080:8080 -e FALLAXY_TOKEN=my_token quay.io/ansible/fallaxy-test-container:latest
```

From there you can access the Galaxy API by navigating to;

* `http://127.0.0.1:8080/api/v2/collections/` - Galaxy
* `http://127.0.0.1:8080/api/automation-hub/v3/collections/` - Automation Hub

## Notes

As well as implementing parts of the `v2` and `v3` API, this endpoint also
exposes the following routes:

* `GET  /api/custom/collections/<filename>` - Download the collection based on the filename specified.
* `POST /api/custom/reset/` - Reset all the existing collections and clear the cache. POST `{"clear":false}` to just reset the collections and rebuild from the cache.
