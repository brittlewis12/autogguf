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
usage: autogguf [-h] [--quants QUANTS] [--verbose]
                [--full-precision FULL_PRECISION] [--fp FP] [--imatrix IMATRIX]
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
                        `q2_k`,`q3_k_s`,`q3_k_m`,`q3_k_l`,`q4_0`,`q4_1`,
                        `q4_k_s`,`q4_k_m`,`q5_0`,`q5_1`,`q5_k_s`,`q5_k_m`,
                        `q6_k`,`q8_0`,`bf16`,`iq1_s`,`iq1_m`,`iq2_xxs`,
                        `iq2_xs`,`iq2_s`,`iq2_m`,`q2_k_s`,`iq3_xxs`,
                        `iq3_xs`,`iq3_s`,`iq3_m`,`iq4_xs`,`iq4_nl`
  --verbose, -v         Increase output verbosity.
  --full-precision FULL_PRECISION
                        The full precision GGUF format to convert to and quantize
                        from. `f16` (default) or `f32`.
  --fp FP               Path to fp16 or fp32 GGUF file for quantization. Implies
                        skipping download and initial conversion to FP16.
  --imatrix IMATRIX     Path to custom imatrix file for imatrix quantization. Skips
                        downloading calibration dataset and generating imatrix.
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
