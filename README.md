# Achi Proof of Space

Achi's proof of space is written in C++. Includes a plotter, prover, and
verifier. It exclusively runs on 64 bit architectures. Read the
[Proof of Space document](https://www.chia.net/assets/Chia_Proof_of_Space_Construction_v1.1.pdf) to
learn about what proof of space is and how it works.

## C++ Usage Instructions

### Compile

```bash
# Requires cmake 3.14+

mkdir -p build && cd build
cmake ../
cmake --build . -- -j 6
```

### Run tests

```bash
./RunTests
```

### CLI usage

```bash
./ProofOfSpace -k 25 -f "plot.dat" -m "0x1234" create
./ProofOfSpace -k 25 -f "final-plot.dat" -m "0x4567" -t TMPDIR -2 SECOND_TMPDIR create
./ProofOfSpace -f "plot.dat" prove <32 byte hex challenge>
./ProofOfSpace -k 25 verify <hex proof> <32 byte hex challenge>
./ProofOfSpace -f "plot.dat" check <iterations>
```

### Benchmark

```bash
time ./ProofOfSpace -k 25 create
```


### Hellman Attacks usage

There is an experimental implementation which implements some of the Hellman
Attacks that can provide significant space savings for the final file.


```bash
./HellmanAttacks -k 18 -f "plot.dat" -m "0x1234" create
./HellmanAttacks -f "plot.dat" check <iterations>
```

## Python

Finally, python bindings are provided in the python-bindings directory.

### Install

```bash
python3 -m venv .venv
. .venv/bin/activate
pip3 install .
```

### Run python tests

Testings uses pytest. Linting uses flake8 and mypy.

```bash
py.test ./tests -s -v
```
