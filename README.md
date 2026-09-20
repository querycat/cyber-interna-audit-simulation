## Auditoria Interna de Segurança da Informação — Botium Toys (cenário Brasil)

Auditoria interna de segurança baseada no NIST Cybersecurity Framework, com checklist de controles e de conformidade em LGPD, GDPR, PCI DSS e SOC 1/SOC 2. Cenário fictício adaptado do **Google Cybersecurity Certificate** e localizado para a realidade regulatória brasileira.

## Sobre o projeto

A Botium Toys é uma empresa fictícia de pequeno porte que desenvolve e vende brinquedos, com sede única (escritório + loja + depósito) e presença crescente no e-commerce, atendendo clientes no Brasil e na União Europeia.

Este repositório documenta uma auditoria interna de segurança conduzida sobre o programa de segurança da empresa, com o objetivo de:

- identificar riscos, ameaças e vulnerabilidades aos ativos críticos;
- avaliar quais controles administrativos, técnicos e físicos estão implementados;
- verificar a aderência às normas e regulamentações aplicáveis;
- recomendar ações priorizadas para elevar a postura de segurança.

## Diferencial desta versão

O cenário original é estadunidense. Nesta adaptação, o caso foi reconstruído para o contexto brasileiro, o que introduziu exigências que não existiam no material de origem:

- LGPD (Lei nº 13.709/2018) — registro das operações de tratamento (art. 37), definição de bases legais, nomeação e publicação do encarregado/DPO (art. 41), prazos e formulário de comunicação de incidente da ANPD;
- Art. 14 da LGPD — tratamento de dados de crianças e adolescentes, risco crítico por se tratar de uma empresa de brinquedos;
- CDC — responsabilidade solidária no fornecimento em caso de vazamento;
- GDPR mantido, por haver titulares na UE;
- PCI DSS mantido, por haver aceite e processamento interno de cartões.

## Estrutura do repositório

```text
├── README.md
├── audit/
│   └── audit.md
└── docs/
    ├── control-and-complice-checklist.md
    ├── control-categories.md
    └── scope.md
```

## Metodologia

A auditoria segue as cinco funções do NIST CSF — Identificar, Proteger, Detectar, Responder e Recuperar — com foco inicial em Identificar, já que a ausência de inventário e classificação de ativos é a causa-raiz apontada na avaliação de risco.

### Etapas executadas:

1. Definição de escopo e objetivos da auditoria;
2. Levantamento dos ativos gerenciados pela TI;
3. Avaliação de risco com atribuição de nota;
4. Preenchimento do checklist de controles (administrativos, técnicos e físicos/operacionais);
5. Preenchimento do checklist de conformidade;
6. Elaboração de recomendações priorizadas (P0 a P3).

## Resultados

### Nota de risco: 8/10 (alto).

#### Controles

| Situação | Quantidade | Controles                                                                                  |
|---|---|---|
| Implementados | 7 | Política de senhas (nominal), firewall, antivírus, monitoramento de legado, fechaduras, CFTV, detecção de incêndio |
| Ausentes| 7 | Menor privilégio, segregação de funções, plano de recuperação de desastres, backups, IDS, criptografia, cofre de senhas |

### Conformidade

| Norma | Situação |
|---|---|
| PCI DSS | Nenhuma das quatro boas práticas atendida |
| LGPD | Parcial — há política de privacidade e plano de notificação, mas faltam inventário, DPO e tratamento de dados de menores |
| GDPR | Parcial — notificação em 72h e políticas documentadas atendidas; privacidade e inventário não |
| SOC 1/ SOC 2 | Parcial — integridade e disponibilidade atendidas; acesso e confidencialidade não |

### Principais recomendações

| Prioridade | Ação |
|---|---|
| P0 | Criptografia de dados de cartão e dados pessoais, em repouso e em trânsito |
| P0 | Controle de acesso por menor privilégio e separação de funções (RBAC) |
| P0 | Rotina de backup com teste de restauração e plano de continuidade |
| P1 | 	Inventário e classificação de ativos e operações de tratamento |
| P1 | Nomeação do encarregado (DPO) e revisão das bases legais |
| P1 | Consentimento parental verificável para dados de menores |
| P2 | Política de senhas robusta, cofre corporativo e MFA |
| P2 | Implantação de IDS/IPS |

O relatório completo, com justificativas e prazos, está em [audit.md](https://github.com/querycat/cyber-internal-audit-simulation/blob/main/audit/audit.md).

## Competências demonstradas

- Auditoria interna de segurança da informação
- Aplicação do NIST Cybersecurity Framework
- Classificação de controles (preventivo, detectivo, corretivo, dissuasório)
- Análise de conformidade: LGPD, GDPR, PCI DSS, SOC 1/SOC 2
- Avaliação e priorização de riscos
- Comunicação de achados técnicos para stakeholders não técnicos

## Aviso

A Botium Toys é uma empresa fictícia. Os dados, achados e recomendações deste repositório são um exercício acadêmico de portfólio e não constituem consultoria jurídica ou parecer de conformidade.

## Autoria

querycat — em transição de carreira de desenvolvimento de software para cibersegurança, com foco em unir experiência em pagamentos e antifraude ao conhecimento de segurança.

[GitHub](https://github.com/querycat) · [LinkedIn](https://github.com/querycat)

## Licença

Distribuído sob a licença MIT. Veja LICENSE para mais informações.
