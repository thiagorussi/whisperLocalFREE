# Whisper.cpp Transcrição - Guia de Instalação e Uso (Linux Mint)

Este repositório contém o passo a passo para instalar, configurar e utilizar o [whisper.cpp](https://github.com/ggerganov/whisper.cpp) para transcrever vídeos localmente em sua máquina Linux Mint.

---

## Requisitos

Antes de tudo, instale as dependências necessárias:

```bash
sudo apt update
sudo apt install git cmake build-essential ffmpeg
```

---

## Clonar o Projeto

```bash
mkdir ~/whisper-transcricao
cd ~/whisper-transcricao
git clone https://github.com/ggerganov/whisper.cpp
cd whisper.cpp
```

---

## 🔧 Compilar o Whisper.cpp

```bash
make
```

Os binários serão gerados em `build/bin/`.

---

## Baixar o Modelo (exemplo com base)

```bash
./models/download-ggml-model.sh base
```

Modelos disponíveis: `tiny`, `base`, `small`, `medium`, `large`.

---

## Converter Vídeo para Áudio (.wav)

```bash
ffmpeg -i ~/Vídeos/reuniao.mkv -ar 16000 -ac 1 -c:a pcm_s16le audio.wav
```

Isso gera o arquivo `audio.wav` no mesmo diretório.

---

## Transcrever com whisper.cpp

```bash
./build/bin/whisper-cli -m models/ggml-base.bin -f audio.wav -l pt -otxt -of ./transcrições/reuniao
```

- `-m`: caminho para o modelo
- `-f`: caminho do áudio
- `-l`: idioma (pt = português)
- `-otxt`: gerar arquivo .txt
- `-of`: nome base do arquivo de saída

---

## Estrutura Recomendada

```
whisper-transcricao/
├── audio.wav
├── transcrições/
│   └── reuniao.txt
└── whisper.cpp/
    ├── models/
    │   └── ggml-base.bin
    └── build/bin/whisper-cli
```

---

## Autor

Criado por Thiago Russi
