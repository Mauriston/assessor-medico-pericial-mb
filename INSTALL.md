# Instalação — assessor-pericial-dgpm406

Skill de assessoria normativa médico-pericial, baseada na DGPM-406 (9ª Revisão) da Marinha do Brasil, com a legislação correlata (Portaria GM-MD nº 3.551/2021 e leis citadas). Não depende de nenhum serviço externo obrigatório.

## Estrutura

```
assessor-pericial-dgpm406/
├── SKILL.md                              # instruções principais e hierarquia de fontes
├── INSTALL.md                            # este arquivo
└── referencias/
    ├── correcoes.md                      # errata datada (começa vazia)
    ├── redacao-pericial.md               # formato dos blocos de IS, transcrições e assinatura
    ├── roteamento-finalidade.md          # capítulo/norma por finalidade e vínculo
    ├── enquadramento-beneficio.md        # enquadramento em benefícios (Portaria 3.551/2021)
    ├── doencas-de-lei.json               # resumo estruturado das 17 doenças da Portaria 3.551/2021
    ├── formas-conclusao.json             # laudos permitidos por finalidade e vínculo, com verificações
    ├── entrevista-previa.md              # procedimento de entrevista antes de redigir uma IS
    ├── gatilho-ingresso-normal.md        # atalho para IS de Ingresso sem alterações
    ├── portaria-3551-2021/               # texto da Portaria, um arquivo por doença
    ├── cid10.md / cid10.json             # tabela CID-10 local (nome oficial a partir do código)
    ├── exemplos.md                       # casos-modelo para calibração
    └── dgpm-406/
        ├── indice.md                     # sumário e índice temático dos Capítulos 1–18
        ├── capitulo-01.md … capitulo-18.md   # texto-fonte do corpo normativo
        └── anexos/
            ├── indice-anexos.md          # tabela A–AB: conteúdo e fonte de cada anexo
            ├── anexo-n.md / anexo-o.md / anexo-u.md / anexo-v.md   # texto-fonte
            └── anexo-n-condicoes-inaptidao.json, anexo-o-exames-minimos.json   # apoio estruturado
```

## Instalação

**Claude Code:** clone o repositório na pasta de skills do usuário:

```bash
git clone https://github.com/Mauriston/assessor-medico-pericial-mb.git ~/.claude/skills/assessor-pericial-dgpm406
```

**Claude.ai / Cowork:** envie o arquivo `.skill` pela tela de skills, se a conta permitir.

## Fontes

- **Nível 1 (normativo, DGPM-406):** os Capítulos 1–18 e os Anexos N, O, U e V estão transcritos localmente e são lidos com Read/Grep. Os demais Anexos (formulários DS-1 a DS-8 e tabelas de uso pontual) não estão transcritos; quando for preciso citação literal deles, a skill lê o PDF local `referencias/dgpm-406/DGPM-406-9a-rev.pdf` (íntegra, 370 páginas).
- **Nível 2 (normas externas):** se o usuário anexar a norma, ela é a fonte prioritária. Na falta, a skill faz busca controlada em fontes oficiais (`planalto.gov.br`, `in.gov.br`, `portalmedico.org.br`).

## Dependências

Nenhuma conexão obrigatória. Se houver ferramenta de busca web, a skill a usa apenas para normas de Nível 2 ausentes do pacote.

## Uso com dados reais

A skill orienta o uso de dados hipotéticos. Não insira nomes completos, números de identificação pessoal ou dados de saúde reais no chat.

## Observações

- A pasta `referencias/correcoes.md` é um registro de errata. Cada instalação mantém a sua própria errata.
- As transcrições de Portarias e Anexos devem ser conferidas contra a publicação oficial quando um valor numérico for decisivo para um enquadramento.
