# Auditoria Interna de Segurança da Informação — Botium Toys Brasil

**Protótipo de auditoria interna · Framework: NIST CSF · Data: 19/09/2026**

---

## 1. Contextualização (cenário localizado)

A **Botium Toys** é uma pequena empresa brasileira que desenvolve e vende brinquedos, com sede única no Rio de Janeiro (RJ) que acumula escritório administrativo, loja física e depósito. Com o crescimento do e-commerce próprio, passou a atender clientes em todo o Brasil e também na Europa, o que submete a empresa simultaneamente à **LGPD (Lei nº 13.709/2018)**, ao **GDPR** (por tratar dados de titulares na UE) e ao **PCI DSS** (por aceitar e processar cartões internamente).

A gerência de TI solicitou auditoria interna para mapear riscos, lacunas de controle e exposição a sanções da **ANPD**, do **Procon/CDC** e das bandeiras/adquirentes.

---

## 2. Escopo e objetivos

**Escopo:** todo o programa de segurança da Botium Toys — equipamentos de colaboradores, rede interna, sistemas, aplicações, dados de clientes e instalações físicas.

**Objetivos:** avaliar os ativos existentes, preencher os checklists de controles e conformidade e recomendar as implementações necessárias para elevar a postura de segurança.

---

## 3. Ativos gerenciados pela TI

|Categoria|Ativos|
|---|---|
|Infraestrutura on-premises|Servidores e equipamentos do escritório|
|Equipamentos de usuário|Desktops, notebooks, smartphones, estações remotas, headsets, docks, periféricos, câmeras de vigilância|
|Produtos|Estoque da loja e do depósito anexo (venda presencial e online)|
|Sistemas e serviços|Contábil/fiscal, telefonia, banco de dados, segurança, e-commerce, gestão de estoque|
|Conectividade|Acesso à internet e rede interna|
|Dados|Retenção e armazenamento, incluindo dados pessoais e de cartão|
|Legado|Sistemas em fim de vida que exigem monitoramento humano|

---

## 4. Avaliação de risco

**Nota de risco: 8/10 (alto).**

|Dimensão|Avaliação|
|---|---|
|Impacto da perda de ativos|Médio — a TI não sabe quais ativos estão em risco (inventário inexistente)|
|Risco de multas e sanções|Alto — LGPD, GDPR e PCI DSS não plenamente atendidos|
|Causa-raiz|Ausência da função **Identificar** do NIST CSF: sem inventário, classificação e análise de impacto|

**Principais achados:** acesso irrestrito de todos os colaboradores aos dados internos (inclusive dados de cartão e dados pessoais sensíveis), ausência de criptografia, ausência de backups e de plano de continuidade, ausência de IDS e política de senhas apenas nominal.

---

## 5. Checklist de controles

A Botium Toys possui atualmente este controle?

|#|Controle|Sim|Não|Observação|
|---|---|:-:|:-:|---|
|1|Menor privilégio (_least privilege_)||✕|Todos os colaboradores acessam todos os dados|
|2|Plano de recuperação de desastres||✕|Inexistente|
|3|Política de senhas|✓||Existe, porém com requisitos insuficientes|
|4|Separação de funções||✕|Não implementada|
|5|Firewall|✓||Regras adequadamente definidas|
|6|Sistema de detecção de intrusão (IDS)||✕|Não instalado|
|7|Backups||✕|Sem cópias de dados críticos|
|8|Antivírus|✓||Instalado e monitorado regularmente|
|9|Monitoramento e intervenção manual em sistemas legados|✓||Ocorre, mas sem cronograma nem procedimento claro|
|10|Criptografia||✕|Dados de cartão trafegam e são armazenados em claro|
|11|Sistema de gerenciamento de senhas||✕|Sem cofre central; resets via chamado|
|12|Fechaduras (escritório, loja, depósito)|✓||Adequadas|
|13|CFTV|✓||Atualizado|
|14|Detecção/prevenção de incêndio|✓||Alarme e sprinklers funcionais|

**Placar: 7 controles presentes · 7 ausentes.**

---

## 6. Checklist de conformidade

### 6.1 PCI DSS

|Boa prática|Sim|Não|
|---|:-:|:-:|
|Apenas usuários autorizados acessam dados de cartão dos clientes||✕|
|Dados de cartão são armazenados, aceitos, processados e transmitidos internamente em ambiente seguro||✕|
|Procedimentos de criptografia protegem os pontos de contato e os dados da transação||✕|
|Políticas seguras de gerenciamento de senhas adotadas||✕|

**Exposição:** multas contratuais da adquirente/bandeira, aumento de taxas, e em caso de vazamento, responsabilidade solidária no fornecimento (art. 7º, parágrafo único, do CDC) e possível suspensão do credenciamento para transacionar cartões.

### 6.2 LGPD (Lei nº 13.709/2018) — adaptação brasileira do bloco de privacidade

|Boa prática|Sim|Não|
|---|:-:|:-:|
|Dados pessoais de clientes (BR e UE) mantidos privados e seguros||✕|
|Existe plano de comunicação de incidente ao regulador e aos titulares dentro do prazo legal|✓||
|Dados devidamente classificados e inventariados (registro de operações de tratamento — art. 37)||✕|
|Políticas, procedimentos e processos de privacidade documentados e aplicados|✓||

**Pontos de atenção específicos do Brasil:**

- A empresa tem plano de notificação em 72 horas herdado da lógica do GDPR. Sob a LGPD, a comunicação de incidente à ANPD segue o regulamento próprio da Autoridade, com prazo em **dias úteis** e formulário específico — vale confirmar o prazo vigente no site da ANPD e ajustar o _playbook_ interno, pois o plano atual pode estar desalinhado.
- Não há indicação de **encarregado (DPO) nomeado e publicado**, exigência do art. 41.
- Dados de crianças e adolescentes: por vender brinquedos, é altamente provável o tratamento de dados de menores, sujeito ao art. 14 (melhor interesse e consentimento específico de um dos pais ou responsável). **Este é o maior risco jurídico do cenário localizado e não aparecia no original.**
- Falta **registro das operações de tratamento** e definição das bases legais (art. 7º/art. 11).

### 6.3 GDPR (mantido — clientes na UE)

|Boa prática|Sim|Não|
|---|:-:|:-:|
|Dados de clientes da UE mantidos privados/seguros||✕|
|Plano de notificação em até 72h em caso de violação|✓||
|Dados classificados e inventariados||✕|
|Políticas de privacidade documentadas e aplicadas|✓||

### 6.4 SOC 1 / SOC 2

|Boa prática|Sim|Não|
|---|:-:|:-:|
|Políticas de acesso de usuários estabelecidas||✕|
|Dados sensíveis (PII/SPII) mantidos confidenciais||✕|
|Integridade dos dados — consistentes, completos, exatos e validados|✓||
|Disponibilidade dos dados para pessoas autorizadas|✓||

---

## 7. Recomendações priorizadas

|Prioridade|Ação|Justificativa de risco|
|---|---|---|
|**P0 — imediato**|Implementar criptografia em repouso e em trânsito para dados de cartão e dados pessoais|Não conformidade direta com PCI DSS e art. 46 da LGPD; maior vetor de multa|
|**P0**|Restringir acesso por menor privilégio e segregação de funções (RBAC)|Todos os colaboradores acessam dados de cartão e PII hoje|
|**P0**|Implantar rotina de backup com teste de restauração e plano de continuidade/DR|Perda total de dados críticos em caso de ransomware ou sinistro|
|**P1 — 30 dias**|Inventariar e classificar ativos e operações de tratamento (função Identificar do NIST CSF; art. 37 LGPD)|Sem inventário não há gestão de risco possível|
|**P1**|Nomear e publicar o encarregado (DPO) e revisar bases legais|Exigência legal expressa não atendida|
|**P1**|Tratar dados de menores com consentimento parental verificável|Setor de brinquedos; risco sancionatório e reputacional elevado|
|**P2 — 90 dias**|Endurecer política de senhas e adotar cofre corporativo + MFA|Reduz _brute force_, fadiga de senha e chamados de reset|
|**P2**|Instalar IDS/IPS|Ausência de capacidade de detecção na rede|
|**P2**|Formalizar cronograma e runbook de manutenção dos sistemas legados|Atividade existe, mas sem previsibilidade ou critério de intervenção|
|**P3**|Revisar o plano de resposta a incidentes para contemplar os prazos e o formulário da ANPD, além do GDPR|Plano atual cobre a UE, mas pode não atender o regulador brasileiro|

**Controles físicos:** fechaduras, CFTV e sistema de incêndio estão adequados — manter o ciclo de manutenção e a retenção das imagens em prazo compatível com a política de privacidade.

