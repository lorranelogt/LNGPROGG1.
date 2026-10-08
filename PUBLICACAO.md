# Publicação e entrega

Os arquivos estão preparados, mas os serviços precisam ser configurados na conta do aluno. Não há links de publicação ativos incluídos nesta entrega.

## 1. GitHub

1. Extraia o ZIP.
2. Crie um repositório público, por exemplo `projeto-indicadores-economicos`.
3. Use **Add file → Upload files** para enviar o conteúdo interno de `projeto-g1`, preservando suas subpastas. `app.py`, `requirements.txt` e `index.html` devem aparecer na raiz do repositório.
4. Confirme o envio com **Commit changes**. Não envie somente o ZIP.
5. Confira se os arquivos da pasta `dados` e o notebook também foram enviados. Arquivos ocultos são opcionais para executar, mas recomenda-se enviá-los por Git para preservar tema e organização.

## 2. GitHub Pages

1. Abra **Settings → Pages** do repositório.
2. Em **Source**, escolha **Deploy from a branch**.
3. Selecione a branch `main` e a pasta `/(root)`; clique em **Save**.
4. Aguarde a conclusão e copie o endereço que o GitHub exibir.
5. Abra esse endereço e confira a página e os downloads.

Se o projeto for colocado dentro de uma subpasta de um repositório existente, publique a raiz e acrescente o nome da subpasta ao endereço do Pages. Para facilitar, prefira um repositório dedicado com os arquivos na raiz.

## 3. Streamlit Community Cloud

1. Entre em https://share.streamlit.io/ usando sua conta vinculada ao GitHub.
2. Use **Create app** e selecione o repositório.
3. Escolha a branch `main` e indique `app.py` como arquivo principal. Se estiver em subpasta, informe o caminho completo, por exemplo `projeto-g1/app.py`.
4. Nas configurações avançadas, selecione Python 3.11 ou 3.12 se disponível.
5. Clique em **Deploy** e aguarde a instalação de `requirements.txt`.
6. Copie o endereço exibido e teste os filtros, o radar, o download e o botão de banco.

## 4. Conectar os links

No final de `index.html`, altere somente os valores vazios deste objeto usando os endereços reais:

```javascript
const links = {github: "", streamlit: ""};
```

Atualize também a seção Links da entrega do README e faça novo commit.

## 5. Entregar ao professor

- Link do repositório GitHub.
- Link da página GitHub Pages.
- Link do dashboard Streamlit.
- `notebooks/analise_indicadores_economicos.ipynb`.
- `app.py` (com `analise.py` disponível no repositório).
- CSV da pasta `dados`.

Antes de entregar, abra os três links em uma janela anônima para conferir acesso público.

Referências de publicação consultadas:
- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
- https://docs.streamlit.io/deploy/streamlit-community-cloud/deploy-your-app
