# MetaGPT: The Multi-Agent Framework

<p align="center">
<a href=""><img src="docs/resources/MetaGPT-logo.jpeg" alt="MetaGPT logo: Enable GPT to work in software company, collaborating to tackle more complex tasks." width="150px"></a>
</p>

<p align="center">
<b>Assign different roles to GPTs to form a collaborative software entity for complex tasks.</b>
</p>

<p align="center">
<a href="docs/README_CN.md"><img src="https://img.shields.io/badge/文档-中文版-blue.svg" alt="CN doc"></a>
<a href="README.md"><img src="https://img.shields.io/badge/document-English-blue.svg" alt="EN doc"></a>
<a href="docs/README_JA.md"><img src="https://img.shields.io/badge/ドキュメント-日本語-blue.svg" alt="JA doc"></a>
<a href="https://discord.gg/wCp6Q3fsAk"><img src="https://img.shields.io/badge/Discord-Join-blue?logo=discord&logoColor=white&color=blue" alt="Discord Follow"></a>
<a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT"></a>
<a href="docs/ROADMAP.md"><img src="https://img.shields.io/badge/ROADMAP-路线图-blue" alt="roadmap"></a>
<a href="https://twitter.com/DeepWisdom2019"><img src="https://img.shields.io/twitter/follow/MetaGPT?style=social" alt="Twitter Follow"></a>
</p>

<p align="center">
   <a href="https://airtable.com/appInfdG0eJ9J4NNL/shrEd9DrwVE3jX6oz"><img src="https://img.shields.io/badge/AgentStore-Waitlist-ffc107?logoColor=white" alt="AgentStore Waitlist"></a>
   <a href="https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/geekan/MetaGPT"><img src="https://img.shields.io/static/v1?label=Dev%20Containers&message=Open&color=blue&logo=visualstudiocode" alt="Open in Dev Containers"></a>
   <a href="https://codespaces.new/geekan/MetaGPT"><img src="https://img.shields.io/badge/Github_Codespace-Open-blue?logo=github" alt="Open in GitHub Codespaces"></a>
   <a href="https://huggingface.co/spaces/deepwisdom/MetaGPT" target="_blank"><img alt="Hugging Face" src="https://img.shields.io/badge/%F0%9F%A4%97%20-Hugging%20Face-blue?color=blue&logoColor=white" /></a>
</p>

1. MetaGPT takes a **one line requirement** as input and outputs **user stories / competitive analysis / requirements / data structures / APIs / documents, etc.**
2. Internally, MetaGPT includes **product managers / architects / project managers / engineers.** It provides the entire process of a **software company along with carefully orchestrated SOPs.**
   1. `Code = SOP(Team)` is the core philosophy. We materialize SOP and apply it to teams composed of LLMs.

![A software company consists of LLM-based roles](docs/resources/software_company_cd.jpeg)

<p align="center">Software Company Multi-Role Schematic (Gradually Implementing)</p>

## MetaGPT's Abilities


https://github.com/geekan/MetaGPT/assets/34952977/34345016-5d13-489d-b9f9-b82ace413419



## Examples (fully generated by GPT-4)

For example, if you type `python startup.py "Design a RecSys like Toutiao"`, you would get many outputs, one of them is data & api design

![Jinri Toutiao Recsys Data & API Design](docs/resources/workspace/content_rec_sys/resources/data_api_design.png)

It costs approximately **$0.2** (in GPT-4 API fees) to generate one example with analysis and design, and around **$2.0** for a full project.




## Installation

### Installation Video Guide

- [Matthew Berman: How To Install MetaGPT - Build A Startup With One Prompt!!](https://youtu.be/uT75J_KG_aY)

### Traditional Installation

```bash
# Step 1: Ensure that NPM is installed on your system. Then install mermaid-js.
npm --version
sudo npm install -g @mermaid-js/mermaid-cli

# Step 2: Ensure that Python 3.9+ is installed on your system. You can check this by using:
python --version

# Step 3: Clone the repository to your local machine, and install it.
git clone https://github.com/geekan/metagpt
cd metagpt
python setup.py install
```

**Note:**

- If already have Chrome, Chromium, or MS Edge installed, you can skip downloading Chromium by setting the environment variable
  `PUPPETEER_SKIP_CHROMIUM_DOWNLOAD` to `true`.

- Some people are [having issues](https://github.com/mermaidjs/mermaid.cli/issues/15) installing this tool globally. Installing it locally is an alternative solution,

  ```bash
  npm install @mermaid-js/mermaid-cli
  ```

- don't forget to the configuration for mmdc in config.yml

  ```yml
  PUPPETEER_CONFIG: "./config/puppeteer-config.json"
  MMDC: "./node_modules/.bin/mmdc"
  ```

- if `python setup.py install` fails with error `[Errno 13] Permission denied: '/usr/local/lib/python3.11/dist-packages/test-easy-install-13129.write-test'`, try instead running `python setup.py install --user`

- To convert Mermaid charts to SVG, PNG, and PDF formats. In addition to the Node.js version of Mermaid-CLI, you now have the option to use Python version Playwright, pyppeteer or mermaid.ink for this task.

  - Playwright
    - **Install Playwright**

    ```bash
    pip install playwright
    ```

    - **Install the Required Browsers**

    to support PDF conversion, please install Chrominum.

    ```bash
    playwright install --with-deps chromium
    ```

    - **modify `config.yaml`**

    uncomment MERMAID_ENGINE from config.yaml and change it to `playwright`

    ```yaml
    MERMAID_ENGINE: playwright
    ```

  - pyppeteer
    - **Install pyppeteer**

    ```bash
    pip install pyppeteer
    ```

    - **Use your own Browsers**

    pyppeteer alow you use installed browsers,  please set the following envirment
    
    ```bash
    export PUPPETEER_EXECUTABLE_PATH = /path/to/your/chromium or edge or chrome
    ```

    please do not use this command to install browser, it is too old

    ```bash
    pyppeteer-install
    ```

    - **modify `config.yaml`**

    uncomment MERMAID_ENGINE from config.yaml and change it to `pyppeteer`

    ```yaml
    MERMAID_ENGINE: pyppeteer
    ```

  - mermaid.ink
    - **modify `config.yaml`**

    uncomment MERMAID_ENGINE from config.yaml and change it to `ink`

    ```yaml
    MERMAID_ENGINE: ink
    ```  

    Note: this method does not support pdf export.

### Installation by Docker

```bash
# Step 1: Download metagpt official image and prepare config.yaml
docker pull metagpt/metagpt:v0.3.1
mkdir -p /opt/metagpt/{config,workspace}
docker run --rm metagpt/metagpt:v0.3.1 cat /app/metagpt/config/config.yaml > /opt/metagpt/config/key.yaml
vim /opt/metagpt/config/key.yaml # Change the config

# Step 2: Run metagpt demo with container
docker run --rm \
    --privileged \
    -v /opt/metagpt/config/key.yaml:/app/metagpt/config/key.yaml \
    -v /opt/metagpt/workspace:/app/metagpt/workspace \
    metagpt/metagpt:v0.3.1 \
    python startup.py "Write a cli snake game"

# You can also start a container and execute commands in it
docker run --name metagpt -d \
    --privileged \
    -v /opt/metagpt/config/key.yaml:/app/metagpt/config/key.yaml \
    -v /opt/metagpt/workspace:/app/metagpt/workspace \
    metagpt/metagpt:v0.3.1

docker exec -it metagpt /bin/bash
$ python startup.py "Write a cli snake game"
```

The command `docker run ...` do the following things:

- Run in privileged mode to have permission to run the browser
- Map host directory `/opt/metagpt/config` to container directory `/app/metagpt/config`
- Map host directory `/opt/metagpt/workspace` to container directory `/app/metagpt/workspace`
- Execute the demo command `python startup.py "Write a cli snake game"`

### Build image by yourself

```bash
# You can also build metagpt image by yourself.
git clone https://github.com/geekan/MetaGPT.git
cd MetaGPT && docker build -t metagpt:custom .
```

## Configuration

- Configure your `OPENAI_API_KEY` in any of `config/key.yaml / config/config.yaml / env`
- Priority order: `config/key.yaml > config/config.yaml > env`

```bash
# Copy the configuration file and make the necessary modifications.
cp config/config.yaml config/key.yaml
```

| Variable Name                              | config/key.yaml                           | env                                             |
| ------------------------------------------ | ----------------------------------------- | ----------------------------------------------- |
| OPENAI_API_KEY # Replace with your own key | OPENAI_API_KEY: "sk-..."                  | export OPENAI_API_KEY="sk-..."                  |
| OPENAI_API_BASE # Optional                 | OPENAI_API_BASE: "https://<YOUR_SITE>/v1" | export OPENAI_API_BASE="https://<YOUR_SITE>/v1" |

## Tutorial: Initiating a startup

```shell
# Run the script
python startup.py "Write a cli snake game"
# Do not hire an engineer to implement the project
python startup.py "Write a cli snake game" --implement False
# Hire an engineer and perform code reviews
python startup.py "Write a cli snake game" --code_review True
```

After running the script, you can find your new project in the `workspace/` directory.

### Preference of Platform or Tool

You can tell which platform or tool you want to use when stating your requirements.

```shell
python startup.py "Write a cli snake game based on pygame"
```

### Usage

```
NAME
    startup.py - We are a software startup comprised of AI. By investing in us, you are empowering a future filled with limitless possibilities.

SYNOPSIS
    startup.py IDEA <flags>

DESCRIPTION
    We are a software startup comprised of AI. By investing in us, you are empowering a future filled with limitless possibilities.

POSITIONAL ARGUMENTS
    IDEA
        Type: str
        Your innovative idea, such as "Creating a snake game."

FLAGS
    --investment=INVESTMENT
        Type: float
        Default: 3.0
        As an investor, you have the opportunity to contribute a certain dollar amount to this AI company.
    --n_round=N_ROUND
        Type: int
        Default: 5

NOTES
    You can also use flags syntax for POSITIONAL ARGUMENTS
```

### Code walkthrough

```python
from metagpt.software_company import SoftwareCompany
from metagpt.roles import ProjectManager, ProductManager, Architect, Engineer

async def startup(idea: str, investment: float = 3.0, n_round: int = 5):
    """Run a startup. Be a boss."""
    company = SoftwareCompany()
    company.hire([ProductManager(), Architect(), ProjectManager(), Engineer()])
    company.invest(investment)
    company.start_project(idea)
    await company.run(n_round=n_round)
```

You can check `examples` for more details on single role (with knowledge base) and LLM only examples.

## QuickStart

It is difficult to install and configure the local environment for some users. The following tutorials will allow you to quickly experience the charm of MetaGPT.

- [MetaGPT quickstart](https://deepwisdom.feishu.cn/wiki/CyY9wdJc4iNqArku3Lncl4v8n2b)

Try it on Huggingface Space
- https://huggingface.co/spaces/deepwisdom/MetaGPT

## Citation

For now, cite the [Arxiv paper](https://arxiv.org/abs/2308.00352):

```bibtex
@misc{hong2023metagpt,
      title={MetaGPT: Meta Programming for Multi-Agent Collaborative Framework},
      author={Sirui Hong and Xiawu Zheng and Jonathan Chen and Yuheng Cheng and Jinlin Wang and Ceyao Zhang and Zili Wang and Steven Ka Shing Yau and Zijuan Lin and Liyang Zhou and Chenyu Ran and Lingfeng Xiao and Chenglin Wu},
      year={2023},
      eprint={2308.00352},
      archivePrefix={arXiv},
      primaryClass={cs.AI}
}
```

## Contact Information

If you have any questions or feedback about this project, please feel free to contact us. We highly appreciate your suggestions!

- **Email:** alexanderwu@fuzhi.ai
- **GitHub Issues:** For more technical inquiries, you can also create a new issue in our [GitHub repository](https://github.com/geekan/metagpt/issues).

We will respond to all questions within 2-3 business days.

## Demo

https://github.com/geekan/MetaGPT/assets/2707039/5e8c1062-8c35-440f-bb20-2b0320f8d27d

## Join us

📢 Join Our Discord Channel!
https://discord.gg/ZRHeExS6xv

Looking forward to seeing you there! 🎉
