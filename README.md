**⚠** **NÃO ME RESPOSABILIZO **⚠**

# Osintgram 🔎📸

[![version-1.3](https://img.shields.io/badge/version-1.3-green)](https://github.com/Datalux/Osintgram/releases/tag/1.3)
[![GPLv3](https://img.shields.io/badge/license-GPLv3-blue)](https://img.shields.io/badge/license-GPLv3-blue)
[![Python3](https://img.shields.io/badge/language-Python3-red)](https://img.shields.io/badge/language-Python3-red)
[![Telegram](https://img.shields.io/badge/Telegram-Channel-blue.svg)](https://t.me/osintgram)
[![Docker](https://img.shields.io/badge/Docker-Supported-blue)](https://img.shields.io/badge/Docker-Supported-blue)

Osintgram é um **OSINT** ferramenta no Instagram para coletar, analisar e executar **reconhecimento**

<p align="center">
<img align="center" src=".img/carbon.png" width="900">
</p>

Disclaimer: responsabilidade: **APENAS PARA FINS EDUCACIONAIS! Os colaboradores não assumem qualquer responsabilidade pelo uso desta ferramenta.**


Aviso: É aconselhável **não** usar sua própria conta/conta principal ao usar esta ferramenta.

## Ferramentas e comandos 🧰

O Osintgram oferece um shell interativo para realizar análises na conta do Instagram de qualquer usuário por seu apelido. Você pode ter:

```text
- addrs           Obtenha todos os registrados endereçados por fotos de destino
- captions        Obter legendas de fotos do usuário
- comments        Obtenha o total de comentários das postagens do alvo
- followers       Obtenha seguidores alvo
- followings      Obter usuários seguidos por destino
- fwersemail      Receba e-mail de seguidores alvo
- fwingsemail     Obter e-mail de usuários seguidos por destino
- fwersnumber     Obtenha o número de telefone dos seguidores de destino
- fwingsnumber    Obtenha o número de telefone dos usuários seguido pelo destino
- hashtags        Get hashtags used by target
- info            Obter informações de destino
- likes          Obtenha curtidas totais das postagens do alvo
- mediatype       Get user's posts type (photo or video)
- photodes        Get description of target's photos
- photos          Download user's photos in output folder
- propic          Download user's profile picture
- stories         Download user's stories  
- tagged          Get list of users tagged by target
- wcommented      Get a list of user who commented target's photos
- wtagged         Get a list of user who tagged target
```

You can find detailed commands usage [here](doc/COMMANDS.md).

[**Latest version**](https://github.com/Datalux/Osintgram/releases/tag/1.3) |
[Commands](doc/COMMANDS.md) |
[CHANGELOG](doc/CHANGELOG.md)

## FAQ
1. **Can I access the contents of a private profile?** No, you cannot get information on private profiles. You can only get information from a public profile or a profile you follow. The tools that claim to be successful are scams!
2. **What is and how I can bypass the `challenge_required` error?** The `challenge_required` error means that Instagram notice a suspicious behavior on your profile, so needs to check if you are a real person or a bot. To avoid this you should follow the suggested link and complete the required operation (insert a code, confirm email, etc)


## Instação ⚙️


```
git clone https://github.com/jovemsigilosodobembr/Osintgrams.git
```
```
cd Osintgrams
```

```
python3 -m venv venv
```

```
pip install -r requirements.txt
```

```
make setup
```
ou 

nano /config/credentials.ini


  


6. Open the `credentials.ini` file in the `config` folder and write your Instagram account username and password in the corresponding fields
    
    Alternatively, you can run the `make setup` command to populate this file for you.

7. Run the main.py script in one of two ways

    * As an interactive prompt `python3 main.py <target username>`
    * Or execute your command straight away `python3 main.py <target username> --command <command>`
    
### Use Osintgram v2 (beta)
You can use Osintgram2 beta just switching to `v2` [branch](https://github.com/Datalux/Osintgram/tree/v2).
The v2 has some improvements and faster with a new command execution interface. Try it just running `git checkout v2`.

## Docker Quick Start 🐳

This section will explain how you can quickly use this image with `Docker` or `Docker-compose`.

### Prerequisites

Before you can use either `Docker` or `Docker-compose`, please ensure you do have the following prerequisites met.

1. **Docker** installed - [link](https://docs.docker.com/get-docker/)
2. **Docker-composed** installed (if using Docker-compose) - [link](https://docs.docker.com/compose/install/)
3. **Credentials** configured - This can be done manually or by running the `make setup` command from the root of this repo

**Important**: Your container will fail if you do not do step #3 and configure your credentials

### Docker

If docker is installed you can build an image and run this as a container.

Build:

```bash
docker build -t osintgram .
```

Run:

```bash
docker run --rm -it -v "$PWD/output:/home/osintgram/output" osintgram <target>
```

- The `<target>` is the Instagram account you wish to use as your target for recon.
- The required `-i` flag enables an interactive terminal to use commands within the container. [docs](https://docs.docker.com/engine/reference/commandline/run/#assign-name-and-allocate-pseudo-tty---name--it)
- The required `-v` flag mounts a volume between your local filesystem and the container to save to the `./output/` folder. [docs](https://docs.docker.com/engine/reference/commandline/run/#mount-volume--v---read-only)
- The optional `--rm` flag removes the container filesystem on completion to prevent cruft build-up. [docs](https://docs.docker.com/engine/reference/run/#clean-up---rm)
- The optional `-t` flag allocates a pseudo-TTY which allows colored output. [docs](https://docs.docker.com/engine/reference/run/#foreground)

### Using `docker-compose`

You can use the `docker-compose.yml` file this single command:

```bash
docker-compose run osintgram <target>
```

Where `target` is the Instagram target for recon.

Alternatively you may run `docker-compose` with the `Makefile`:

`make run` - Builds and Runs with compose. Prompts for a `target` before running.

### Makefile (easy mode)

For ease of use with Docker-compose, a `Makefile` has been provided.

Here is a sample work flow to spin up a container and run `osintgram` with just two commands!

1. `make setup`   - Sets up your Instagram credentials
2. `make run`     - Builds and Runs a osintgram container and prompts for a target

Sample workflow for development:

1. `make setup`          - Sets up your Instagram credentials
2. `make build-run-testing`   - Builds an Runs a container without invoking the `main.py` script. Useful for an `it` Docker session for development
3. `make cleanup-testing`     - Cleans up the testing container created from `build-run-testing`







## External library 🔗

[Instagram API](https://github.com/ping/instagram_private_api)
