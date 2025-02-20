# Change Log

## 2.3.2 [Unreleased](https://github.com/nteract/bookstore/compare/2.3.1...HEAD)

## [2.3.1](https://github.com/nteract/bookstore/releases/tag/2.3.1) 2019-07-16

### Fixing problems

This fixes an issue that arose where in certain cases cloning would hang indefinitely when trying to read content [#145](https://github.com/nteract/bookstore/issues/145).

## [2.3.0](https://github.com/nteract/bookstore/releases/tag/2.3.0) 2019-07-02

Thank you to the following contributors:

* Carol Willing
* Kyle Kelley
* M Pacer
* Matthew Seal
* Safia Abdalla
* Shelby Sturgis

The full list of changes they made can be seen [on GitHub](https://github.com/nteract/bookstore/issues?q=milestone%3A2.3.0)

### Significant changes

#### New Publishing endpoint

Previously our publishing endpoint was `/api/bookstore/published`, it is now `/api/bookstore/publish`.

#### Cloning

As of 2.3.0 cloning from S3 is now enabled by default.

Cloning allows access to multiple S3 buckets. To use them, you will need to set up your configuration for any such bucket.

#### Massive Testing improvements

We have built out a framework for unit-testing Tornado handlers. In addition, we have added a collection of unit tests that bring us to a coverage level in non-experimental code of well over 80%.

#### `/api/bookstore/`: Features and Versions

You can identify which features have been enabled and which version of bookstore is available by using the `/api/bookstore` endpoint.

#### REST API Documentation

All APIs are now documented at our [REST API docs](https://bookstore.readthedocs.io/en/latest/openapi.html) using the OpenAPI spec.

### Experimental
#### Clients (subject to change in future releases)

To enable access to bookstore publishing and cloning from within a notebook, we have created a Notebook and Bookstore clients. *This is still experimental* functionality at the moment and needs additional testing, so we discourage its use in production.
The design relies on an assumption that a single kernel is attached to a single notebook, and will break if you use multiple notebooks attached to the same kernel.

However, for those who wish to experiment, it offers some fun ways of exploring bookstore.

Example: if you run a notebook from within the top-level [`bookstore/ci`](https://github.com/nteract/bookstore/tree/master/ci) directory while running the integration test server with `yarn test:server` (see more about [local integration testing](https://bookstore.readthedocs.io/en/latest/project/local_ci.html)),
you should be able to publish from inside a notebook using the following code snippet:```

```python
from bookstore.client import BookstoreClient
book_store = BookstoreClient()
book_store.publish()
```

And if you have published your notebook to the local ci (e.g., publishing `my_notebook.ipynb` to the minio `bookstore` bucket with the `ci-published` published prefix), you can clone it from S3 using:

```python
from bookstore.client import BookstoreClient
book_store = BookstoreClient()
book_store.clone("bookstore", "ci-published/my_notebook.ipynb")
```

## Releases prior to 2.3.0

[2.2.1 (2019-02-03)](https://github.com/nteract/bookstore/releases/tag/2.2.1)

[2.2.0 (2019-01-29)](https://github.com/nteract/bookstore/releases/tag/2.2.0)

[2.1.0 (2018-11-20)](https://github.com/nteract/bookstore/releases/tag/2.1.0)

[2.0.0 (2018-11-13)](https://github.com/nteract/bookstore/releases/tag/2.0.0)

[0.1 (2018=10-16)](https://github.com/nteract/bookstore/releases/tag/0.1)
