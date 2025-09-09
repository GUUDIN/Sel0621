# Template Overleaf para Trabalhos Acadêmicos

Este template LaTeX foi criado para facilitar a produção de trabalhos acadêmicos no Overleaf, seguindo a estrutura e formatação de um documento PDF de exemplo. Ele está configurado para usar a fonte Times New Roman e inclui seções para introdução, questões, figuras, tabelas, equações e blocos de código.

## Estrutura do Projeto

- `main.tex`: O arquivo principal LaTeX que contém a estrutura do documento, pacotes necessários e exemplos de uso.
- `README.md`: Este arquivo, explicando o template.
- `images/`: (Opcional) Diretório para armazenar arquivos de imagem usados no documento. As imagens de exemplo (`example-image-a.pdf`, etc.) devem ser substituídas pelas suas próprias imagens.

## Como Usar

1.  **Faça o Upload para o Overleaf:** Crie um novo projeto no Overleaf e faça o upload de todos os arquivos deste template.
2.  **Edite `main.tex`:**
    *   **Título e Autores:** Atualize o `\title{}` e `\author{}` com as informações do seu trabalho.
    *   **Resumo:** Preencha o `\begin{abstract}` com o resumo do seu trabalho.
    *   **Seções:** Utilize as seções e subseções (`\section*{}`, `\subsection*{}`) como guias para organizar seu conteúdo. Lembre-se de adicionar `\addcontentsline{toc}{section}{}` ou `\addcontentsline{toc}{subsection}{}` para que apareçam no sumário.
    *   **Figuras:** Substitua `example-image-a` e outras imagens de exemplo pelas suas próprias imagens. Certifique-se de que as imagens estejam no diretório `images/` ou ajuste o caminho.
        ```latex
        \begin{figure}[h!]
            \centering
            \includegraphics[width=0.8\textwidth]{images/sua_imagem.png}
            \caption{Sua legenda aqui.}
            \label{fig:sua_label}
        \end{figure}
        ```
    *   **Tabelas:** Use o ambiente `tabular` para criar tabelas. O pacote `booktabs` oferece linhas horizontais mais profissionais (`\toprule`, `\midrule`, `\bottomrule`).
        ```latex
        \begin{table}[h!]
            \centering
            \caption{Sua legenda da tabela aqui.}
            \label{tab:sua_label}
            \begin{tabular}{ccc}
                \toprule
                Coluna 1 & Coluna 2 & Coluna 3 \\
                \midrule
                Dado 1 & Dado 2 & Dado 3 \\
                \bottomrule
            \end{tabular}
        \end{table}
        ```
    *   **Equações:** Utilize os ambientes `amsmath` para equações matemáticas.
        ```latex
        $$
        Sua equação aqui
        $$
        ```
    *   **Listagens de Código:** Use o ambiente `lstlisting` do pacote `listings` para incluir blocos de código (Python, Netlist, etc.).
        ```latex
        \begin{lstlisting}[language=Python, caption=Seu Código, label=lst:seu_codigo]
        print("Hello, World!")
        \end{lstlisting}
        ```
    *   **Referências:** Adicione suas referências no ambiente `thebibliography` no final do documento e cite-as no texto usando `\cite{}`.

## Personalização

-   **Pacotes:** Se precisar de funcionalidades adicionais, adicione os pacotes necessários no preâmbulo (`\usepackage{}`).
-   **Estilo:** Ajuste as configurações de `geometry` para alterar as margens, se necessário.

Este template serve como um ponto de partida. Sinta-se à vontade para adaptá-lo às suas necessidades específicas.

