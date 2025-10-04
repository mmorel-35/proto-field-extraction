# proto-field-extraction

proto-field-extraction is a library that supports extracting fields from the protobuf message by giving its type info and the field path.

This folder is the source-of-truth.

## Building

This project supports both Bazel WORKSPACE and bzlmod (MODULE.bazel) build modes with Bazel 7.6.1.

### Using WORKSPACE mode

```bash
bazel build --config=workspace //...
bazel test --config=workspace //...
```

### Using bzlmod mode (default in Bazel 7.6.1)

```bash
bazel build --config=bzlmod //...
bazel test --config=bzlmod //...
```

Or simply use the default (bzlmod is enabled by default in Bazel 7.6.1):

```bash
bazel build //...
bazel test //...
```
