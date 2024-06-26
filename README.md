# ELF

ELF (Exponent-Less Float-point encoding) is a simple yet effective, near-lossless floating-point compression method, that transforms floating-point parameters within pre-trained models (PTMs) in such a way that the common exponent field of the transformed parameters can be completely eliminated to save storage space. ELF is embarrassingly parallel via data parallelism, achieving an extreme compression & decompression speed. 
<div align="center">
  <img width="350" alt="elf_com_decom" src="https://github.com/ds2-lab/ELF/assets/21178173/9c673335-a588-48f7-a8a1-88e6e916781a">
</div>


We also developed ELVES, a compression framework integrating ELF and several other data reduction methods. ELVES uses the most effective method to compress PTMs that exhibit different patterns. 

## Publication
Everything You Always Wanted to Know About Storage Compressibility of Pre-Trained ML Models but Were Afraid to Ask (VLDB'24 to appear).

The preprint of our VLDB'24 paper can be viewed at: https://arxiv.org/abs/2402.13429.

This branch contains the source code of ELF & ELVES.

## ELF Build
Package Installation
```bash
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y gcc g++ libeigen3-dev make python3-pip
```
Build ELF and DE
```bash
mkdir build
make
```

## ELVES Compression Examples
Package Installation
```
pip3 install -r requirements.txt
```
Run the Example
```
cd ELVES
python3 main.py
```

## ELF Usage
```
./build/elf_pthread -c -i ELVES/model_compressed/elves_compression/distilbert-base-cased/fl_weights/f32_65783040.bin -p f32 -o ELVES/model_compressed/elves_compression/distilbert-base-cased/exponential_dedup/f32/ -n 65783040
```
### Parameter Explanation
| Parameter | Explanation |
|:----------|:----------|
| -i | input binary file |
| -p | parameter type: f16 for floating 16, f32 for floating 32, f64 for floating 64 |
| -n | parameter number |
| -c | compression      |
| -d | decompression    |
| -o | output folder specified |




