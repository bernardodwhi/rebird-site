# RELATÓRIO R-0 — Rebird: publicação de rebird.ia.br

Data: 27/10/2026 · Executor: Claude Code, na máquina do titular · Referência: `docs/SPEC-R0.md`

## Resumo
O site está publicado no GitHub Pages a partir de `bernardodwhi/rebird-site` (`main` / raiz), com o domínio personalizado `rebird.ia.br`. Só falta o titular configurar o DNS no Registro.br para o domínio abrir no navegador e o HTTPS ficar disponível. Nenhum conteúdo foi alterado. O repositório `vectis-site` e o domínio vectis.ia.br não foram tocados.

## 1. Integridade (`SHA256SUMS`)
- A pasta já estava no destino previsto (`C:\Users\berna\OneDrive\Documentos importantes\GitHub\rebird-site`).
- `sha256sum -c SHA256SUMS`: os 10 ficheiros conferem (`OK`).
- Os blobs do commit também conferem com os hashes. Os ficheiros estão em LF e o Git converteu-os sem diferença.

## 2. Verificação local
Servi a pasta com `python -m http.server 8080` e abri as páginas no navegador interno (Chromium).

| Página | HTTP | "Vectis" visível | `mailto:` |
|---|---|---|---|
| `index.html` | 200 | não | `contato@rebird.ia.br` (7 ligações) |
| `privacidade.html` | 200 | só a nota de versão | `contato@rebird.ia.br` |
| `termos.html` | 200 | só a nota de versão | `contato@rebird.ia.br` |
| `exclusao-de-dados.html` | 200 | só a nota de versão | `contato@rebird.ia.br` |

- Orbe: renderiza num canvas WebGL, com esferas violeta animadas. Na primeira frame vê-se só o quadrado de fundo.
- A consola não mostrou erros.
- Pedidos externos: só Google Fonts, como a SPEC prevê, e as ligações para as políticas do WhatsApp nas páginas legais.

## 3. Repositório
- Repositório: https://github.com/bernardodwhi/rebird-site (público, criado vazio, sem README, licença nem .gitignore).
- Commit: `bba555f684fac855da8aaad7bb906ecb050e7e75`. Mensagem: `R-0: site Rebird — migração do site Vectis, páginas legais v2.0`, com o trailer `Co-Authored-By` do Claude.
- Push: `main` → `origin/main`. Confirmei com `git ls-remote`.

## 4. GitHub Pages
- Source: *Deploy from a branch*, `main` / `/ (root)`.
- Custom domain: `rebird.ia.br`, lido do `CNAME` e confirmado no campo das definições.
- Build *pages build and deployment*: `success` às 16:00:45 UTC ([run 40536437118](https://github.com/bernardodwhi/rebird-site/actions/runs/40536437118)).
- Teste pelo IP do Pages (`185.199.108.153`, cabeçalho `Host: rebird.ia.br`): as quatro páginas respondem 200 com o título Rebird.
- DNS Check: «in progress».
- *Enforce HTTPS*: indisponível («domain is not properly configured»). Fica por ativar depois do DNS.
- `bernardodwhi.github.io/rebird-site/` responde 301, como esperado com domínio personalizado.

## 5. Pendências

### Do titular (agora)
1. **DNS no Registro.br.** Às 16h01 UTC de 27/10, `rebird.ia.br` existe mas não tem registos A e `www.rebird.ia.br` não existe. Falta acrescentar os quatro registos A (185.199.108–111.153) e o CNAME `www` → `bernardodwhi.github.io.`, conforme a SPEC.
2. **HTTPS.** Depois de o DNS propagar e o GitHub emitir o certificado, marcar *Enforce HTTPS* em Settings → Pages.

### Conflito entre regras da SPEC (para decisão do titular)
O `index.html` contém duas palavras que a regra «Nunca escrever "chatbot", "robô"…» proíbe:
- linha 388: «…e nenhum dos dois fala como um robô.»
- linha 390: «…o que separa um sistema projetado de um chatbot solto.»

As duas aparecem em sentido de contraste: o produto não é isto. Não as alterei, porque a SPEC proíbe alterações de conteúdo nesta sessão. Fica para decidir em R-1.

### R-1 (da SPEC)
Logótipo definitivo; fontes auto-hospedadas; redirecionamento de vectis.ia.br; e-mail `contato@rebird.ia.br` ativo no Zoho antes da verificação na Meta.

### Nota
Este relatório não entrou no commit R-0. Foi commitado depois, com as edições de R-1 (abaixo).

## Adenda — R-1, escopo fechado (27/10/2026)
Fiz quatro substituições em `index.html`. Antes de cada uma, confirmei que o texto original ocorria exatamente uma vez:

1. «e nenhum dos dois fala como um robô.» → «e nenhum dos dois fala como uma mensagem gravada.»
2. «<b>Aqui está a alavanca:</b>» → «<b>Aqui está o ganho real:</b>»
3. «de um chatbot solto.» → «de uma automação solta.»
4. «<b>Não entrega</b> um bot pronto em minutos» → «<b>Não entrega</b> automação pronta em minutos»

- **Nota:** «alavanca» era resíduo da marca anterior (Vectis).
- As substituições 1 e 3 resolvem o conflito da SPEC registado acima. A página deixa de conter «chatbot» e «robô».
- O diff de `index.html` tem só estas quatro linhas e os finais de linha continuam LF.
- Regenerei `SHA256SUMS` sobre todos os ficheiros da pasta, exceto o próprio `SHA256SUMS`, já com este relatório incluído.
- Nada mais foi alterado. Não toquei no `vectis-site`.
