# TensorFlow Scala

TensorFlow API for the Scala Programming Language

## Set Up for Development

Make sure you have [CMake](https://cmake.org/install/) installed and
then perform the following steps:
  1. Clone this repository in a directory (e.g., `tensorflow_scala`).
  2. Compile the TensorFlow dynamic library by running the following
     commands in the
     [TensorFlow](https://github.com/tensorflow/tensorflow) source code
     directory:

     ```bash
     ./configure
     bazel build --config=opt --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-msse3 --copt=-msse4.1 --copt=-msse4.2 //tensorflow:libtensorflow.so
     ```

     Make sure to add the `--config=cuda` option when running the last
     command, if compiling with CUDA support.
  3. Copy the `bazel-bin/tensorflow/libtensorflow.so` file in a
     directory that is in `LD_LIBRARY_PATH`, or set `LD_LIBRARY_PATH`
     appropriately.

In order to compile, run the following command from within the
`tensorflow_scala` directory:

```bash
sbt compile
```

## Supported Features

- General features:
  - [x] Slice creation
    - [ ] Support int-based slicing too (rather than just long)
  - [ ] Op output slicing
- Op creation API helpers:
  - [x] Graph op creation context
  - [x] Name scope op creation context
  - [x] Device op creation context
  - [x] Colocation op creation context
  - [x] Control dependencies op creation context
  - [ ] "Static" name scope op creation context
  - [ ] Attribute op creation context
  - [ ] Container op creation context
  - [ ] Gradient override map op creation context (need gradient support first)
  - [ ] Kernel label map op creation context (may be unnecessary)
- Execution API helpers:
  - [ ] Default session
  - [ ] Session execution context
- General API features:
  - [ ] Variables
  - [ ] Gradients
  - [ ] Optimizers
  - [ ] Estimators
  - [ ] tfprof / op statistics collection

## TODOs

- Op creation:
  - Add tests for all of the op functions
  - Get graph from inputs
  - Assert same graph for inputs and control inputs
  - Convert to tensor function
  - Graph collections
  - Set Op.Output shape
  - Support re-entering existing name scopes
  - Reset default graph
  - Register op statistics
- Execution:
  - Revamp the session API
- General API:
  - Find a way to expose inner functions and implicits to the root API package.