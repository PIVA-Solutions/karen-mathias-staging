# Handoff — Deploy da homologação Karen Mathias (2026-10-10)

Sessão de origem: Claude Code, conversa "Site da Karen", 2026-10-10.
Repositório: https://github.com/PIVA-Solutions/karen-mathias-staging

## 1. Objetivo e status

**Objetivo:** publicar a homologação do portfólio da cliente Karen Mathias em
https://karenmathias.pivasolutions.com.br, com HTTPS, seguindo o mesmo padrão do
`rg-performance-staging` (pasta `site/` publicada no GitHub Pages via GitHub Actions,
subdomínio de `pivasolutions.com.br`).

**Status: CONCLUÍDO.**

- Repositório criado (público) na org PIVA-Solutions, um único commit na `main`.
- GitHub Pages com `build_type=workflow`, domínio `karenmathias.pivasolutions.com.br`
  (`protected_domain_state: verified`).
- Certificado HTTPS `approved` (expira em 2027-01-07); `https_enforced=true`.
  `http://` responde 301 para `https://`.
- Runs do workflow "Deploy to GitHub Pages":
  - `38020291305` (push, 2026-10-10T03:21:49Z): success
  - `38020302999` (workflow_dispatch, 2026-10-10T03:22:01Z): success
- Validação final:
  - `curl -sI https://karenmathias.pivasolutions.com.br` → `HTTP/1.1 200 OK`
  - `curl -s https://karenmathias.pivasolutions.com.br | grep -c "noindex"` → `1`
  - `curl -sI https://karenmathias.pivasolutions.com.br/img/glasses.jpg` → `HTTP/1.1 200 OK`

## 2. Decisões ainda não registradas em arquivo

O repositório não tem `DECISIONS.md`, `PROJECT.md`, `ROADMAP.md` nem `reports/`. No workspace
The Chosen (`C:\PIVA Solutions\The-Chosen\Karen Mathias\`) também não existe `PROJECT.md`
para este projeto. Destino sugerido entre parênteses (a confirmar, já que esses arquivos
ainda não existem).

1. **Domínio de homologação configurado só pela API do Pages, sem arquivo `CNAME` na raiz**,
   igual à RG. (DECISIONS.md)
2. **Pages em modo Actions** (`build_type=workflow`), deploy pelo
   `.github/workflows/deploy-pages.yml`, que publica `site/` a cada push na `main` que mexa
   em `site/**` (ou por `workflow_dispatch`). (DECISIONS.md / PROJECT.md)
3. **Repositório público**, só com a branch `main` (sem branches extras para deploy).
   (DECISIONS.md)
4. **Commit inicial publicado exatamente como veio no zip**, sem alterar site, README ou
   workflow; commitado com `core.autocrlf=false` para não converter finais de linha.
   O commit não tem linha `Co-Authored-By`, porque a mensagem foi definida pelo usuário.
   (reports/ — registro do deploy)
5. **DNS:** CNAME `karenmathias.pivasolutions.com.br → piva-solutions.github.io` no
   Registro.br (configurado pelo usuário antes desta sessão). (PROJECT.md)

## 3. Trabalho em andamento

Nenhum trabalho de código em andamento.

- Branch de trabalho: `main` (único branch antes deste handoff).
- Último commit na `main`: `c0dfa26` — "Homologação do portfólio Karen Mathias".
- Arquivos tocados: nenhum arquivo do site/README/workflow foi editado; o commit adicionou
  os 19 arquivos do zip (`.github/workflows/deploy-pages.yml`, `README.md`,
  `site/index.html`, 16 imagens em `site/img/`).
- Este handoff está na branch `chore/handoff-deploy-homologacao` (não mesclada na `main`).

## 4. Pendências, riscos e próximos passos (em ordem)

1. **Coletar o feedback da Karen** usando o roteiro de testes do `README.md`.
2. **Resolver as pendências do `README.md`**, todas ainda abertas:
   - trocar as imagens pelos arquivos originais em alta qualidade;
   - confirmar as cores da Mutti (três aparecem como `#F86C51` no Canva);
   - links dos reels do Case 1;
   - confirmar o Behance (`behance.net/karenmathias_sm`);
   - WhatsApp, se a Karen quiser.
3. **Criar `PROJECT.md` / `DECISIONS.md`** para o projeto, conforme a The Chosen
   (`_SYSTEM/CLAUDE.md`), e registrar as decisões da seção 2. (a confirmar: se ficam no
   repositório ou na pasta do workspace)
4. **Decidir o destino deste handoff**: mesclar `chore/handoff-deploy-homologacao` na `main`
   ou mantê-lo só na branch. Atenção: o workflow só dispara para mudanças em `site/**`, então
   mesclar `docs/` não gera deploy.
5. **Produção** em `karenmathias.com.br` sem `noindex`: não iniciado. Modelo (novo repositório
   ou mesmo repositório com outro domínio) e DNS: a confirmar.

**Riscos:**

- O site tem `noindex`; não pode ir para produção sem removê-lo.
- Várias imagens foram recortadas de gravação de tela (segundo o README), com qualidade
  inferior.
- Certificado expira em 2027-01-07; o GitHub Pages renova automaticamente enquanto o DNS
  apontar para `piva-solutions.github.io` (a confirmar se há monitoramento).
- O repositório é público: tudo que entrar nele (inclusive `docs/`) fica visível.

## 5. Detalhes operacionais desta conversa

- **Cópia local com git:**
  `C:\PIVA Solutions\The-Chosen\Karen Mathias\karen-mathias-staging\karen-mathias-staging\`
  (remote `origin` = `https://github.com/PIVA-Solutions/karen-mathias-staging.git`).
  O zip original continua em `C:\PIVA Solutions\The-Chosen\Karen Mathias\karen-mathias-staging.zip`
  e foi conferido como idêntico à pasta descompactada (`diff -r`, incluindo `.github/`).
- **Conta GitHub usada:** `AlmeidaaPauloo` (admin ativo na org PIVA-Solutions), via `gh`.
- **Comandos de configuração do Pages usados:**

  ```bash
  gh api -X POST repos/PIVA-Solutions/karen-mathias-staging/pages -f build_type=workflow
  gh api -X PUT repos/PIVA-Solutions/karen-mathias-staging/pages -f cname=karenmathias.pivasolutions.com.br
  gh api -X PUT repos/PIVA-Solutions/karen-mathias-staging/pages -F https_enforced=true
  ```

- **Conferir o estado do Pages/certificado:**

  ```bash
  gh api repos/PIVA-Solutions/karen-mathias-staging/pages
  ```

- **Disparar e acompanhar deploy manual:**

  ```bash
  gh workflow run deploy-pages.yml -R PIVA-Solutions/karen-mathias-staging
  gh run list -R PIVA-Solutions/karen-mathias-staging --limit 3
  gh run watch <run-id> -R PIVA-Solutions/karen-mathias-staging --exit-status
  ```

- **Observação:** o push inicial já disparou um deploy antes de o Pages estar ativado; ele
  ficou na fila e terminou com sucesso depois da ativação. O certificado já estava aprovado
  na primeira consulta, sem precisar de espera.
- **Regras dadas pelo usuário nesta conversa:** não editar site, README nem workflow sem
  pedido explícito; não criar branches extras nem arquivo `CNAME`; não tocar em outros
  repositórios da org.
