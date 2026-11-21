# assessor-pericial-dgpm406
 
Skill para Claude que assessora a redação de documentos médico-periciais de Inspeção de Saúde (IS) com base na **DGPM-406 (9ª Revisão)**, normas da Marinha do Brasil, e na legislação correlata.
 
A skill atua como assessor normativo: esclarece dúvidas sobre procedimentos, competências, finalidades e formatos de laudo, e ajuda a redigir entrevista, exame clínico e conclusão de IS, sempre com citação da norma de origem.
 
> **Aviso:** esta é uma ferramenta de apoio à redação e à consulta normativa. Não é publicação oficial da Marinha do Brasil nem substitui a análise do médico-perito, a norma vigente nem a orientação de órgão competente. Confira sempre o texto no documento oficial antes de utilizá-lo em um ato administrativo.
 
## O que a skill faz
 
- Responde dúvidas sobre a DGPM-406: competência de Juntas, tipos e finalidades de IS, Atestado de Origem (AO), VDF, término de incapacidade e restrições, saídas, recursos e revisão.
- Conduz uma entrevista prévia para levantar os dados que a finalidade exige (vínculo, posto ou graduação, idade, diagnóstico, rotina de trabalho).
- Escolhe o laudo cabível para cada finalidade e vínculo, com base em `referencias/formas-conclusao.json`.
- Redige os três blocos de uma IS (entrevista, exame clínico e conclusão), com a frase de encerramento e o referenciamento normativo.
- Enquadra benefícios conforme a Portaria GM-MD nº 3.551/2021 (doenças especificadas em lei).
- Converte código CID-10 em nome oficial da doença, usando tabela local.
## Conteúdo
 
| Caminho | Conteúdo |
|---|---|
| `SKILL.md` | Instruções principais, hierarquia de fontes e regras de redação |
| `INSTALL.md` | Estrutura detalhada e instruções de instalação |
| `referencias/dgpm-406/` | Texto-fonte dos Capítulos 1 a 18, índice temático e tabela dos Anexos |
| `referencias/dgpm-406/anexos/` | Anexos N, O, U e V transcritos, com versões estruturadas em JSON para N e O |
| `referencias/portaria-3551-2021/` | Texto da Portaria, um arquivo por doença |
| `referencias/enquadramento-beneficio.md` | Critérios de enquadramento em benefícios |
| `referencias/redacao-pericial.md` | Formato dos blocos de IS, transcrições e bloco de assinatura |
| `referencias/roteamento-finalidade.md` | Capítulo ou norma aplicável por finalidade e vínculo |
| `referencias/formas-conclusao.json` | Laudos permitidos por finalidade e vínculo, com condições de uso e verificações |
| `referencias/entrevista-previa.md` | Entrevista prévia: dados a levantar antes de redigir uma IS |
| `referencias/gatilho-ingresso-normal.md` | Atalho para IS de Ingresso sem alterações (`# CONCURSO SEXO IDADE`) |
| `referencias/cid10.json` / `cid10.md` | Tabela CID-10 local |
| `referencias/exemplos.md` | Casos-modelo para calibrar a resposta |
 
## Instalação
 
**Claude Code:**
 
```bash
git clone https://github.com/Mauriston/assessor-medico-pericial-mb.git ~/.claude/skills/assessor-pericial-dgpm406
```
 
**Claude.ai / Cowork:** envie o arquivo `.skill` pela tela de skills, se a sua conta permitir.
 
Detalhes em [`INSTALL.md`](INSTALL.md).
 
## Fontes e limites
 
- **Anexos não transcritos:** os Anexos A a M, P a T e W a AB (majoritariamente formulários DS-1 a DS-8 e tabelas de uso pontual) não estão no pacote. Quando for preciso citação literal deles, a skill solicita o PDF oficial da DGPM-406 ao usuário.
- **Transcrições:** os textos de Portaria e de Anexos foram convertidos de PDF para Markdown. Confira no texto publicado os limiares numéricos que decidam um enquadramento.
- **Normas externas:** se o usuário anexar a norma, ela é usada como fonte prioritária. Na falta, a skill pode fazer busca controlada em fontes oficiais.
## Privacidade
 
Não insira no chat nomes completos, números de identificação pessoal nem dados de saúde reais. Use dados hipotéticos ao testar ou ao redigir modelos.
 
## Contribuição
 
Correções de transcrição, atualizações normativas e novos casos de calibração são bem-vindos por *issue* ou *pull request*. Ao propor uma correção, indique a norma ou a publicação oficial de referência.
 
## Licença

O código e a documentação desta skill (arquivos `SKILL.md`, `INSTALL.md`, `README.md` e os resumos e ferramentas em `referencias/`) são distribuídos sob a licença MIT, conforme o arquivo [`LICENSE`](LICENSE).

**Esta licença não se aplica às normas citadas.** A DGPM-406 (9ª Revisão), a Portaria GM-MD nº 3.551/2021, as leis e as demais normas reproduzidas ou resumidas em `referencias/` são atos oficiais de seus respectivos órgãos. Os textos aqui transcritos servem à consulta e à redação, não substituem a publicação oficial e não passam a integrar a licença MIT. Consulte sempre o texto vigente no Diário Oficial ou na fonte normativa original.
