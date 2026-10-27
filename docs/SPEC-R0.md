# SPEC R-0 — Rebird: publicar o site institucional em rebird.ia.br

Executor: Claude Code, na máquina do titular (GitHub Desktop logado como `bernardodwhi`).
Esta pasta **é** o site, pronto. Nada aqui é alterado nesta sessão. A sessão cria o repositório, publica e relata.

## Procedência (27/10/2026)
Migração do site da Vectis (repositório `vectis-site`, pacote v2 de 02/10/2026, no ar em vectis.ia.br) para a marca Rebird, feita pelo Cowork com substituições verificadas: nome, e-mails (`contato@rebird.ia.br`), nota de origem do nome, rodapé e páginas legais (versão 2.0, titular Rebird Tecnologia Ltda., CNPJ 69.813.320/0001-67, sede em Sete Lagoas/MG; software licenciado à sociedade pelo desenvolvedor). O logótipo "V" foi retirado; fica o wordmark `Rebird` com o ponto violeta até haver marca definitiva. Paleta definitiva (27/10): fundo #11110F; superfícies de acento #6E3DB8; tinta de acento #9B74E8; acento escuro #4A2680; ponto #8F6BE0; texto sobre acento #F7F3FF (contrastes AA conferidos). Texto: «Nenhuma delas começa pelo código.», «informar → agendar → receber → encaminhar», fecho «Não pedimos que mude a empresa. Diga-nos onde o atendimento trava…». Validado offline em Chromium a 1280 e 375 px: páginas 200, orbe a renderizar, sem erros de script. Único pedido externo: Google Fonts (Manrope, IBM Plex Mono), herdado do site Vectis — auto-hospedar em R-1. Hashes em `SHA256SUMS`.

## Tarefas, na ordem
1. Copiar esta pasta para `C:\Users\berna\OneDrive\Documentos importantes\GitHub\rebird-site`. Conferir `SHA256SUMS`.
2. Servir localmente (`npx serve .` ou `python -m http.server 8080`) e abrir: índice, `privacidade.html`, `termos.html`, `exclusao-de-dados.html`. Confirmar que não há "Vectis" visível (só a nota histórica de versão), que os `mailto:` apontam para `contato@rebird.ia.br` e que o orbe renderiza.
3. `git init` → commit `R-0: site Rebird — migração do site Vectis, páginas legais v2.0`. Criar repositório **público** `bernardodwhi/rebird-site` e fazer push da `main`.
4. Settings → Pages → Deploy from a branch → `main` / `/ (root)`. Confirmar `rebird.ia.br` em Custom domain (vem do `CNAME`). *Enforce HTTPS* só quando disponível.
5. Escrever `docs/RELATORIO-R0.md` (commit, URL, estado do Pages, pendências).
6. **Não tocar** no repositório `vectis-site` nem em vectis.ia.br nesta sessão. A desativação do site Vectis (redirecionamento para rebird.ia.br) é decisão posterior do titular.

## DNS — feito pelo titular no Registro.br
Zona de `rebird.ia.br` → «Configurar endereçamento» → modo avançado. **Não delegar NS.** Acrescentar:
```
(nome em branco)   A      185.199.108.153
(nome em branco)   A      185.199.109.153
(nome em branco)   A      185.199.110.153
(nome em branco)   A      185.199.111.153
www                CNAME  bernardodwhi.github.io.
```
Se o Zoho Mail de rebird.ia.br for configurado antes, os registos MX/TXT dele convivem com estes.

## Regras
Nunca escrever "chatbot", "robô" ou "agente de IA" na página. Nenhum dado pessoal do titular além do nome público "Bernardo Dumont" (nas páginas legais, o nome civil como encarregado, exigido pela LGPD). Nenhuma alteração de conteúdo nesta sessão.

## Pendências para R-1
Logótipo definitivo; fontes auto-hospedadas; redirecionamento de vectis.ia.br; e-mail `contato@rebird.ia.br` activo no Zoho antes da verificação na Meta.
