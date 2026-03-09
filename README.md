# Como corrigir/configurar o `vscode jupyter notebook error` no `Linux Ubuntu`

## Resumo

Neste documento estao contidos os principais comandos e configuracoes para corrigir/configurar o `vscode jupyter notebook error` no `Linux Ubuntu`.

## _Abstract_

_In this document are contained the main commands and settings to fix/configure the `vscode jupyter notebook error` on `Linux Ubuntu`._


## Descrição

### `vscode jupyter notebook error`

O `vscode jupyter notebook error` normalmente aparece quando o `Visual Studio Code` nao consegue localizar um interpretador `Python` válido, iniciar o servidor `Jupyter` local ou carregar um `kernel` com as dependências mínimas para abrir e executar arquivos `.ipynb`. Em geral, a correção passa por garantir que o sistema esteja atualizado, instalar `python3`, `pip`, `venv`, `jupyter` e `ipykernel`, e depois selecionar explicitamente o interpretador e o `kernel` corretos dentro do `VS Code`.[2][3][4]


## 1. Como corrigir/configurar o `vscode jupyter notebook error` no `Linux Ubuntu` [1][2][3][4]

Para corrigir/configurar o `vscode jupyter notebook error` no `Linux Ubuntu`, voce pode seguir estes passos:

1. Abrir o `Terminal Emulator`. Voce pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```



2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    ```bash
    sudo apt clean
    ```

    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local. E util para liberar espaco, pois remove apenas os pacotes que nao podem mais ser baixados (ou seja, versoes antigas de pacotes que foram atualizados). Digite o seguinte comando:
    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependencias de outros pacotes e que nao sao mais necessarios. Digite o seguinte comando:
    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizacoes disponiveis para os pacotes que estao instalados em seu sistema. Digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt update
    ```

    2.5 **Corrigir pacotes quebrados**: Isso atualizara a lista de pacotes disponiveis e tentara corrigir pacotes quebrados ou com dependencias ausentes:
    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar o `cache` do gerenciador de pacotes `apt` novamente:
    ```bash
    sudo apt clean
    ```

    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt list --upgradable
    ```

    2.8 Realmente atualizar os pacotes instalados para as suas versoes mais recentes, com base na ultima vez que voce executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`:
    ```bash
    sudo apt full-upgrade -y
    ```



3. Instalar os pacotes base para Python e ambientes virtuais:

    ```bash
    sudo apt install python3 python3-pip python3-venv -y
    ```

4. Atualizar o `pip` do usuario atual:

    ```bash
    python3 -m pip install --upgrade pip
    ```

5. Se o erro acontecer dentro de um projeto especifico, criar e ativar um ambiente virtual na raiz do projeto:

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate
    ```

6. Instalar os pacotes necessarios para o `Jupyter Notebook` e para o registro do `kernel` Python:

    ```bash
    python3 -m pip install jupyter notebook jupyterlab ipykernel ipywidgets
    ```

7. Registrar o ambiente como um `kernel` disponivel para o `Jupyter`:

    ```bash
    python3 -m ipykernel install --user --name vscode-jupyter-fix --display-name "Python (.venv)"
    ```

8. Instalar ou reinstalar as extensoes oficiais do `VS Code` para `Python` e `Jupyter`:

    ```bash
    code --install-extension ms-python.python
    code --install-extension ms-toolsai.jupyter
    ```

9. Abrir ou reabrir o `VS Code` na pasta do projeto:

    ```bash
    code .
    ```

10. No `VS Code`, abrir o arquivo `.ipynb`, usar `Python: Select Interpreter` para escolher o `Python` correto e depois usar `Notebook Kernel` ou `Jupyter: Select Notebook Kernel` para selecionar o `kernel` `Python (.venv)`.

11. Se o notebook ainda não iniciar, recarregar a janela do editor com `Developer: Reload Window` e testar no `Terminal Emulator` se o `Jupyter` sobe sem erro:

    ```bash
    jupyter notebook --version
    jupyter kernelspec list
    python3 -c "import ipykernel, notebook, jupyterlab; print('ok')"
    ```

12. Se o comando `code` não existir no `Terminal Emulator`, abrir o `VS Code`, usar `Ctrl + Shift + P`, procurar por `Shell Command: Install 'code' command in PATH` e depois repetir os passos 8 e 9.


## 2. Verificações rápidas

- Confirmar se o `VS Code` esta usando o mesmo interpretador onde `jupyter` e `ipykernel` foram instalados.

- Confirmar se o arquivo `.venv/bin/python` existe no projeto, quando a estratégia com ambiente virtual for usada.

- Confirmar se `jupyter kernelspec list` mostra o `kernel` registrado.

- Confirmar se as extensões `ms-python.python` e `ms-toolsai.jupyter` estao instaladas e habilitadas.


## Compatibilidade

- Testado como procedimento padrão para `Linux Ubuntu`.

- Também costuma funcionar em `Debian` e `WSL`, desde que `python3`, `pip` e `VS Code` estejam disponíveis.


## Licença

Este repositório inclui o arquivo `LICENSE.txt`.



## Referências

[1] OPENAI. ***Troubleshooting: erro: `jupyter notebook` no `vs code`.***. Disponivel em: <https://chatgpt.com/g/g-p-6980caf949648191ad6acfcdbe590f9e-instalar/c/69a9ac96-f434-832e-b231-02220167bd65>. ChatGPT. Acessado em: 09/03/2026.

[2] MICROSOFT. ***Jupyter Notebooks in Visual Studio Code***. Disponivel em: <https://code.visualstudio.com/docs/datascience/jupyter-notebooks>. Acessado em: 09/03/2026.

[3] MICROSOFT. ***Python in Visual Studio Code***. Disponivel em: <https://code.visualstudio.com/docs/languages/python>. Acessado em: 09/03/2026.

[4] PYTHON SOFTWARE FOUNDATION. ***venv - Creation of virtual environments***. Disponivel em: <https://docs.python.org/3/library/venv.html>. Acessado em: 09/03/2026.

