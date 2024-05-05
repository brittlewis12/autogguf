# autogguf[.py]

Automatically convert HuggingFace models to GGUF

inspired by [mlabonne](https://twitter.com/maximelabonne/status/1746812715606348138)’s [AutoGGUF.ipynb](https://colab.research.google.com/drive/1P646NEg33BZy4BfLDNpTz0V0lwIU3CHu)

## Pre-requisites

- Python 3
- huggingface_hub: `pip3 install huggingface_hub`
  - hf_transfer, for high bandwidth environments: `pip3 install hf_transfer`
    - _set an environment variable:_ `HF_HUB_ENABLE_HF_TRANSFER=1`
- llama.cpp: install or update with `./autogguf -u`

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
                [--vocab-type VOCAB_TYPE] [--pad-vocab] [--fp16 FP16]
                [--skip-download] [--skip-upload] [--only-upload] [--no-accelerator]
                [--update-llama] [--llama-path LLAMA_PATH] [--hf-user HF_USER]
                [--hf-token HF_TOKEN]
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
  --fp16 FP16           Path to fp16 GGUF file for quantization. Implies
                        skipping conversion of to FP16.
  --skip-download       Skip downloading the model to convert from HuggingFace Hub.
                        Defaults to false.
  --skip-upload         Skip uploading converted files to HuggingFace Hub. Defaults
                        to false.
  --only-upload         Upload the .gguf files in the current directory to HuggingFace
                        Hub. Defaults to false.
  --no-accelerator, -n  Disable GPU acceleration for llama.cpp compilation. Only
                        takes effect when installing or updating llama.cpp. Defaults
                        to false.
  --update-llama, -u    Update the llama.cpp repo before converting. Installs
                        llama.cpp if llama-path doesn’t exist. Defaults to false.
  --llama-path LLAMA_PATH, -lp LLAMA_PATH
                        The path to the llama.cpp repo.
  --hf-user HF_USER     Your HuggingFace username for uploading converted models.
  --hf-token HF_TOKEN   Your HuggingFace API token for uploading converted models.
                        Reads from `$HF_TOKEN` by default.
```
