# Projeto de Validação e Análise de Usuário

Este projeto integra funcionalidades para validar documentos de identificação e buscar informações de perfis em redes sociais (especificamente X), fornecendo um resumo consolidado das características do usuário.

## Descrição

O objetivo deste projeto é coletar e validar informações de usuários a partir de um formulário, um documento de identificação e um perfil no X, gerando um relatório unificado que mapeia as características do usuário.

- **Seção 1**: Coletar dados básicos do usuário via formulário.
- **Seção 2**: Validar um documento de identificação enviado como PDF ou imagem usando OCR.
- **Seção 3**: Buscar informações de perfil no X (nome, bio, seguidores, contas seguidas).
- **Resumo**: Apresentar um relatório unificado com todas as informações relevantes.

## Pré-requisitos

Antes de executar o projeto, certifique-se de ter os seguintes itens configurados:

### Dependências

- **Python 3.8+**

- Bibliotecas Python necessárias:

  - `ipywidgets`
  - `pytesseract`
  - `opencv-python`
  - `pdf2image`
  - `selenium`

  Instale todas as dependências com:

  ```bash
  pip install ipywidgets pytesseract opencv-python pdf2image selenium
  ```

### Configurações Adicionais

- **Tesseract-OCR**:
  - Instale o Tesseract no sistema (ex.: `C:\Program Files\Tesseract-OCR\tesseract.exe` no Windows).
- **Poppler**:
  - Necessário para suporte a PDFs com `pdf2image`.
  - No Linux: `sudo apt-get install poppler-utils`
  - No Windows: Baixe do Poppler para Windows e adicione ao PATH.
  - No macOS: `brew install poppler`
- **ChromeDriver**:
  - Baixe o ChromeDriver correspondente à sua versão do Chrome em chromedriver.chromium.org.
  - Adicione o `chromedriver` ao PATH ou especifique o caminho no código (ex.: `webdriver.Chrome(executable_path='caminho/do/chromedriver.exe')`).

## Instalação

Siga os passos abaixo para configurar o projeto:

1. Clone o repositório (substitua `<URL_DO_REPOSITORIO>` pela URL real do seu repositório):

   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd <NOME_DO_REPOSITORIO>
   ```

2. Crie e ative um ambiente virtual (opcional, mas recomendado):

   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/macOS
   venv\Scripts\activate     # Windows
   ```

3. Instale as dependências:

   ```bash
   pip install -r requirements.txt
   ```

   Para criar o `requirements.txt`, você pode usar:

   ```bash
   echo -e "ipywidgets\npytesseract\nopencv-python\npdf2image\nselenium" > requirements.txt
   ```

4. Configure os caminhos do Tesseract e ChromeDriver no código (ajuste conforme necessário no script).

## Uso

O projeto foi projetado para ser executado em um ambiente Jupyter Notebook ou similar, devido ao uso de `ipywidgets` para interfaces interativas. Siga os passos abaixo:

1. Execute os scripts em sequência:
2. **Seção 1**: Preencha o formulário com:
   - Nome completo (ex.: "Pedro Israel da Rocha Smith").
   - CPF (ex.: "44182607133").
   - Nome de usuário no X (ex.: "@PedroSmiithh").
3. **Seção 2**: Faça o upload do RG (em formato PDF ou imagem: `.pdf`, `.png`, `.jpg`, `.jpeg`) para validação.
4. **Seção 3**: Clique em "Buscar Perfil" para coletar dados do perfil no X (nome, bio, seguidores, contas seguidas).
5. **Resumo**: Execute a ultima seção para visualizar todas as informações obtidas através desse projeto


## Limitações

- **OCR**: A precisão do OCR (Tesseract) pode variar dependendo da qualidade da imagem ou PDF do RG. Imagens de baixa resolução ou com ruído podem levar a falhas na validação.
- **X**: O scraping de perfis no X depende da estrutura HTML atual da plataforma, que pode mudar. Além disso, requisições frequentes podem ser bloqueadas pelo X. Para uso em larga escala, considere ferramentas OSINT como Social Searcher.
- **Performance**: O uso do Selenium pode ser lento para grandes volumes de dados devido à necessidade de carregar páginas web.

## Resolução de Possíveis Problemas

- **Erro no Tesseract**: Certifique-se de que o caminho do Tesseract está correto e que o arquivo `por.traineddata` está no diretório `tessdata`.
- **Erro no ChromeDriver**: Verifique se a versão do ChromeDriver corresponde à sua versão do Chrome e se o executável está no PATH.
- **Perfil não encontrado no X**: Confirme se o nome de usuário está correto e se o perfil é público. Se o erro persistir, o X pode estar bloqueando requisições automáticas.
