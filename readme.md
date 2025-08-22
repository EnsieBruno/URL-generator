# 🔗 URL-Generator

Um gerador de links simples e eficiente que encapsula dados de CNPJ e número de pedido em uma URL, e permite a pré-visualização de um iframe a partir dessa mesma URL. O projeto utiliza codificação Base64 para proteger os dados sensíveis durante a transmissão.

---

## ✨ Recursos

-   **Geração de Link Personalizado**: Crie uma URL única com base em um link de iframe, CNPJ e número de pedido.
-   **Codificação Segura**: Os dados são codificados em **Base64** para serem transmitidos de forma segura e compacta através da URL.
-   **Pré-visualização de Iframe**: Visualize o conteúdo do link do iframe em tempo real antes de gerar a URL final.
-   **Compartilhamento Fácil**: A URL gerada pode ser facilmente compartilhada, e a página de destino irá decodificar automaticamente os dados para exibir o iframe correto.

---

## 🛠️ Como Funciona

O projeto é dividido em duas partes principais:

### `home.html` (Gerador de Link)

Esta é a interface principal onde o usuário insere os dados.

1.  **Entrada de Dados**: O usuário preenche os campos **"iframe link"**, **"CNPJ"** e **"Número do Pedido"**.
2.  **Visualização (Opcional)**: A função `atualizarPreview()` permite que o usuário veja o conteúdo do iframe antes de gerar o link. A função `limparPreview()` limpa a visualização e o link gerado.
3.  **Geração do Link**: A função **`gerarLink()`** coleta os valores dos campos, cria um objeto JSON e o converte para uma string Base64.
4.  **Montagem da URL**: A string codificada em Base64 é anexada a uma URL de destino (`sender-prev.html`) como um parâmetro de consulta, por exemplo: `sender-prev.html?d=SuaStringBase64`.
5.  **Exibição do Link**: O link completo é exibido na tela, pronto para ser copiado ou clicado.

### `sender-prev.html` (Página de Destino)

Esta página é a responsável por receber e processar a URL gerada.

1.  **Decodificação**: A função **`carregarIframe()`** extrai o parâmetro de consulta `d` da URL.
2.  **Processamento dos Dados**: O valor de Base64 é decodificado de volta para a string JSON original e, em seguida, analisado para extrair os dados do iframe.
3.  **Exibição do Conteúdo**: O link do iframe é usado para definir o `src` de um iframe na página, exibindo o conteúdo original.
4.  **Limpeza**: A função `limparInput()` pode ser usada para resetar campos de formulário, se necessário.

---

## 🚀 Como Usar

1.  Abra o arquivo `home.html` no seu navegador.
2.  Insira o link do iframe, CNPJ e número do pedido nos campos correspondentes.
3.  Clique em **"Gerar Link"** para criar a URL com os dados codificados.
4.  Use o link gerado para compartilhar ou acessar a página de destino, que exibirá o conteúdo do iframe automaticamente.
