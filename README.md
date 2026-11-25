# settings

Host de configurações e protocolo de abas administrativas do ThinkIac.

Repositório: https://github.com/ThinkIac/settings.

## Uso no ThinkIac

Este pacote foi extraído de `packages/settings`. Preserve a identidade `settings` do manifest ao instalá-lo em um workspace Lógos. Views, rotas, ferramentas e hooks são descobertos pelo runtime e dependem dos provedores correspondentes. Esta extração publica o código atual; não converte JavaScript para LógosType nem implementa instalação por perfil.

## Dependências e validação

Consulte `package.json` e os imports para as capacidades exigidas do host.

Scripts disponíveis: `npm run test`.

## Segurança e dados locais

Credenciais devem ser configuradas no ambiente de destino. Não acompanham esta extração bancos, sessões, uploads, perfis pessoais, arquivos `.env`, caches ou backups. As exclusões foram registradas em relatório externo à publicação. Configure segredos pelo host, sem incluí-los em commits.

## Documentação anterior

# Settings

O Settings hospeda configurações declaradas por outros pacotes. O mapa geral
fica no [README central](../../README.md#contratos-de-pacotes-e-interface).

## Aba administrativa

Use `manifest.settingsTab` para configuração administrativa. A declaração pode
ser um objeto ou uma lista. O renderer padrão é `iframe` e resolve uma view do
próprio pacote. Para formulário declarativo, use `renderer: "schema"` com uma
`surface` válida conforme o contrato de [ui-schema](../ui-schema/README.md).

```json
{
  "manifest": {
    "settingsTab": {
      "id": "general",
      "label": "Geral",
      "renderer": "schema",
      "surface": "settings.general"
    }
  }
}
```

## Integrações e credenciais

Use `manifest.keysTab` para credenciais e integrações. Também aceita objeto ou
lista e segue os mesmos renderers. O pacote dono continua responsável por
autenticar, autorizar e validar toda leitura ou escrita. Não envie segredos no
manifesto nem no schema da interface.

`systemTab` existe apenas por compatibilidade e não deve ser usado por pacotes
novos. Use uma view em iframe quando o fluxo não couber numa superfície
declarativa.

## Registros encontrados no código

- `router`: `tabs`.

A lista é um inventário estático e pode incluir registros em testes; não garante disponibilidade sem os provedores do host.

Há imports relativos para diretórios superiores. A instalação isolada e a composição por perfil precisam resolver esses vínculos antes de remover a cópia da base.

