# Como contribuir

Convenções válidas para todos os repositórios desta organização. Um repositório pode ter regras próprias no seu `CLAUDE.md` ou `CONTRIBUTING.md` — **as dele vencem dentro dele**.

## Idioma

Documentação, issues, PRs e mensagens de commit em **português**. Identificadores e comentários de código em inglês.

## Branches e Pull Requests

- **`main` é sempre lançável.** Nada entra direto: merge só por PR com checks verdes.
- **Uma branch por escopo**, em kebab-case: `tipo/descricao-curta` (`feat/motor-de-score`, `fix/parse-de-estado`). Apareceu trabalho de outro escopo no meio? É outra branch.
- **Fim de etapa = commit + PR.** Não acumule etapas num PR só. **PR acima de ~500 linhas é anti-padrão** — revisão fica superficial e o histórico, ilegível.
- **PR aberto é PR vivo.** Título e descrição valem para o que está na branch **agora**, não para o primeiro commit. Chegou commit que amplia ou desvia o escopo? Acerte os dois antes de pedir revisão ou mergear. Não é ritual por commit: é uma releitura antes de entregar para o revisor.
  - O título tem efeito além da revisão: no squash, PR com **mais de um commit** leva o **título do PR** para a `main` (com um só commit, prevalece a mensagem dele). Descrição velha engana quem revisa; título velho fica no histórico para sempre.
  - As mensagens de commit não se perdem no squash — a organização usa `COMMIT_MESSAGES`, então elas vão inteiras para o corpo do commit final. O que o PR carrega sozinho é a leitura do conjunto.
- Depois do merge, apague a branch local e a remota.

## Commits

[Conventional Commits 1.0.0](https://www.conventionalcommits.org/pt-br/v1.0.0/): `tipo(escopo): descrição`. Tipos aceitos: `feat fix docs refactor chore ci test style perf build revert`. Quebra de compatibilidade com `!` ou rodapé `BREAKING CHANGE:`.

A mensagem descreve o **efeito** da mudança, não o arquivo mexido.

## Versionamento e changelog

- [SemVer 2.0.0](https://semver.org/lang/pt-BR/) — **a tag git `vX.Y.Z` é a fonte da verdade da versão**, não o `package.json`.
- [Keep a Changelog 1.0.0](https://keepachangelog.com/pt-BR/1.0.0/) — toda mudança notável entra em `CHANGELOG.md`, primeiro sob `## [Não lançado]`.
- Correlação: `fix` → PATCH, `feat` → MINOR, quebra → MAJOR. O maior vence.

## Documentação

- **Atualize a doc no mesmo change.** Documentação que descreve o comportamento antigo é pior que documentação ausente.
- **Fonte canônica única:** cada informação tem um dono. Referencie, não duplique. Quando a duplicação for inevitável, **documente-a** com instrução de manter em sincronia.
- **Decisão com renúncia relevante vira ADR** (formato Nygard: contexto, decisão, consequências), numerada e imutável depois de aceita. Mudou a decisão? Nova ADR que supersede a antiga.

## O que nunca entra no repositório

- **Dado real, em qualquer forma** — nem amostra, nem CSV "pequeno", nem dump, nem print de tela. O que entra é o **script** que lê a base e o **esquema** (nomes de coluna, tipos, regras), nunca o conteúdo.
- **Informação pessoal identificável**, de cliente, de usuário ou de funcionário.
- **Credencial** — usuário, senha, token, string de conexão, chave de API. Nem "temporária", nem "de homologação". Segredo vive em `.env` local, fora do versionamento.

Se um segredo vazar para um commit, ele precisa ser **rotacionado**: remover do arquivo não basta, porque história de git não se despublica.

## Código

- Prefira a biblioteca padrão e os recursos nativos da plataforma. Não adicione dependência onde uma função resolve.
- Regra de negócio fora da camada de apresentação; funções puras separadas de I/O, porque são as testáveis sem mock.
- Corrija a causa, não silencie o aviso. Desabilitar linter é último recurso, e sempre com comentário justificando.
- Atalho consciente é **documentado** com o teto que ele tem e o caminho de correção — nunca escondido.

## Automação e CI

- GitHub Actions **pinadas por SHA**, com o número da versão em comentário ao lado.
- Cuidado com `[skip ci]`: alguns provedores honram e pulam o build de produção.
