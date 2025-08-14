# GoLang High-Performance Sync Tool

Uma ferramenta de alta performance para comparação e cópia de arquivos em diretórios de grande escala, com uma interface web interativa para monitoramento em tempo real. Este projeto foi reconstruído a partir de uma versão inicial em Python para alcançar máxima velocidade e escalabilidade utilizando o poder da concorrência do Go.

## Problema Resolvido

Sincronizar diretórios com dezenas de milhares de arquivos (50.000+) pode ser um processo extremamente lento. Ferramentas que operam de forma sequencial se tornam um gargalo, levando horas para completar tarefas de comparação e cópia. Esta ferramenta foi projetada para resolver esse problema, executando operações de I/O de forma massivamente paralela.

## Principais Funcionalidades

-   🚀 **Núcleo de Alta Performance:** Utiliza Goroutines e Canais para realizar varredura de diretórios, cálculo de hash (SHA-256) e cópia de arquivos de forma concorrente, reduzindo drasticamente o tempo de execução.
-   🖥️ **Interface Web Interativa:** Uma UI web moderna permite iniciar e monitorar todas as operações em tempo real, com logs detalhados e uma barra de progresso precisa.
-   ⏯️ **Controle Total da Operação:** Botões para **Pausar**, **Retomar** e **Cancelar** operações longas, dando ao usuário controle total sobre o processo.
-   📊 **Relatórios Detalhados:**
    -   Gera relatórios de **comparação** em JSON e CSV, detalhando arquivos ausentes, diferentes e exclusivos do destino.
    -   Gera relatórios de **cópia** em JSON, listando arquivos copiados com sucesso e falhas.
    -   Inclui um visualizador web para analisar os relatórios de forma clara e organizada.
-   ⚙️ **Seleção Inteligente:** Preenche automaticamente as listas de seleção com os relatórios disponíveis, facilitando o fluxo de trabalho.
-   🗑️ **Exclusão de Arquivos:** Ignora automaticamente arquivos temporários do sistema (como `Thumbs.db` e `.DS_Store`) para manter os relatórios limpos.
-   📦 **Executável Único:** A aplicação é compilada em um único binário, com a interface web embarcada. Nenhuma dependência externa é necessária para executar.

## Estrutura do Projeto (Lógica)


/go-sync-tool
├── main.go                       # Ponto de entrada e lógica principal
├── collected_data/               # Diretório de saída para relatórios de coleta
├── comparison_results/           # Diretório de saída para relatórios de comparação
└── copy_results/                 # Diretório de saída para relatórios de cópia


## Tecnologias Utilizadas

-   **Backend:** Go (GoLang)
-   **Comunicação Real-Time:** WebSockets (utilizando a biblioteca `gorilla/websocket`)
-   **Frontend:** HTML, CSS e JavaScript (vanilla)

## Como Começar

### Pré-requisitos

-   Ter o [Go](https://golang.org/dl/) (versão 1.18 ou superior) instalado.

### Instalação e Execução

1.  Clone o repositório:
    ```bash
    git clone [https://github.com/seu-usuario/go-sync-tool.git](https://github.com/seu-usuario/go-sync-tool.git)
    cd go-sync-tool
    ```

2.  Instale as dependências:
    ```bash
    go mod tidy
    ```

3.  Compile o executável:
    ```bash
    go build
    ```

4.  Execute a aplicação:
    -   No Windows: `.\go-sync-tool.exe`
    -   No Linux/macOS: `./go-sync-tool`

5.  Abra seu navegador e acesse `http://localhost:8080`.

## Como Usar

1.  **Coletar Dados:** Na seção 1, insira o caminho completo do diretório de **Origem** e clique em "Coletar Origem". Repita o processo para o diretório de **Destino**.
2.  **Comparar:** Na seção 2, os relatórios de coleta recém-criados aparecerão nas caixas de seleção. Escolha a origem e o destino e clique em "Comparar".
3.  **Copiar Arquivos:** Na seção 3, a caixa de seleção será preenchida com os relatórios de comparação. Selecione o relatório desejado e clique em "Iniciar Cópia".
4.  **Visualizar Relatórios:** Use os botões "Visualizar" nas seções 3 e 4 para abrir os relatórios de comparação ou de cópia em uma nova aba do navegador.

## Licença

Este projeto está licenciado sob a Licença MIT. Veja o arquivo `LICENSE` para mais detalhes.
