# autogguf[.py] - Automatically convert HuggingFace models to GGUF

## Pre-requisites

- Python 3
- huggingface_hub: `pip3 install huggingface_hub`
- llama.cpp: `git clone https://github.com/ggerganov/llama.cpp`

## Installation

```sh
$ git clone https://github.com/brittlewis12/autogguf
$ cd autogguf
$ chmod +x autogguf
$ ./autogguf -h
```

## Usage

```sh
$ ./autogguf -h
usage: autogguf [-h] [--quants QUANTS] [--verbose] [--model-type MODEL_TYPE]
                [--vocab-type VOCAB_TYPE] [--pad-vocab] [--skip-fp16]
                [--skip-download] [--skip-upload] [--update-llama]
                [--llama-path LLAMA_PATH] [--hf-user HF_USER] [--hf-token HF_TOKEN]
                model_id

convert HuggingFace models to GGUF, automatically.

positional arguments:
  model_id              The HuggingFace model ID to convert. Required.

options:
  -h, --help            show this help message and exit
  --quants QUANTS, -q QUANTS
                        Comma-separated list of quant levels to convert. Defaults to
                        all non-imatrix k-quants and 8_0. All quantization levels:
                        `q2_k`, `q2_k_s` `q3_k_l`, `q3_k_m`, `q3_k_s`, `q4_0`,
                        `q4_1`, `q4_k_m`, `q4_k_s`, `q5_0`, `q5_1`, `q5_k_m`,
                        `q5_k_s`, `q6_k`, `q8_0`, `iq2_xxs`, `iq2_xs`.
  --verbose, -v         Increase output verbosity.
  --model-type MODEL_TYPE, -m MODEL_TYPE
                        The model architecture type. `llama` (default), `mistral`, or
                        anything else.
  --vocab-type VOCAB_TYPE, -vt VOCAB_TYPE
                        The model vocabulary type: `spm`, `hfft`, `bpe`, or None
                        (default). Ignored for model-type of `llama` or `mistral`.
  --pad-vocab, -pv      Pad the vocabulary in case of mismatches. Defaults to false.
  --skip-fp16           Skip converting the model to FP16. Defaults to false.
  --skip-download       Skip downloading the model to convert from HuggingFace Hub.
                        Defaults to false.
  --skip-upload         Skip uploading converted files to HuggingFace Hub. Defaults
                        to false.
  --update-llama, -u    Update the llama.cpp repo before converting. Defaults to
                        false.
  --llama-path LLAMA_PATH, -lp LLAMA_PATH
                        The path to the llama.cpp repo.
  --hf-user HF_USER     Your HuggingFace username for uploading converted models.
  --hf-token HF_TOKEN   Your HuggingFace API token for uploading converted models.
                        Reads from `$HF_TOKEN` by default.
```
