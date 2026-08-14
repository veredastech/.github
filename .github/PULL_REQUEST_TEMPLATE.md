<!-- Padrão da organização. Um repositório pode sobrepor este arquivo com o seu próprio. -->

## O que muda, e por quê

<!-- O efeito da mudança para quem usa, não a lista de arquivos mexidos. Se existir issue ou ID rastreável (chave de board, ADR, débito), cite aqui. -->

## Como verificar

<!-- O comando ou o caminho que prova que funciona. "Rodei local" não é verificação; `pytest -q` e o resultado, sim. -->

## Antes de pedir revisão

- [ ] Commits no padrão [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/), em português
- [ ] `CHANGELOG.md` atualizado sob `## [Não lançado]`, se a mudança for notável
- [ ] Documentação mais próxima atualizada **no mesmo PR** — doc que descreve o comportamento antigo é pior que doc ausente
- [ ] Nenhum dado real, credencial ou informação pessoal entrou no diff (nem em teste, nem em fixture, nem em print)
- [ ] Decisão com renúncia relevante virou ADR

## Tamanho

<!-- PR acima de ~500 linhas é anti-padrão: revisão fica superficial e o histórico fica ilegível. Se passou disso, diga por que não deu para quebrar. -->
