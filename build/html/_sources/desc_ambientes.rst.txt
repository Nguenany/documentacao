Documento de Entrega de Ambientes
=================================

Este documento descreve os ambientes entregues, as suas configurações, os testes realizados e os utilizadores envolvidos.

1. Links dos Ambientes
----------------------
- **Ambiente de Desenvolvimento**
    - URL: https://dev.academiatis.local
    - Máquina/Servidor: `srv-dev-01`
    - Utilizadores existentes:
        - admin (Administrador)
        - dev_user (Desenvolvedor)

- **Ambiente de Testes**
    - URL: https://test.academiatis.local
    - Máquina/Servidor: `srv-test-01`
    - Utilizadores existentes:
        - qa_user (Qualidade)
        - admin_test (Administrador de Testes)

- **Ambiente de Produção**
    - URL: https://www.academiatis.com
    - Máquina/Servidor: `srv-prod-01`
    - Utilizadores existentes:
        - admin (Administrador)
        - suporte (Equipa de Suporte)

2. Validação dos Testes
-----------------------
Os seguintes testes foram realizados:

- **Testes de Autenticação**
  - Resultado: ✅ Sucesso
  - Observação: Login e logout validados para todos os perfis.

- **Testes de Integração**
  - Resultado: ⚠️ Erro encontrado
  - Descrição: API de pagamentos retornava timeout.
  - Resolução: Ajuste no *timeout* do conector, erro corrigido.

- **Testes de Desempenho**
  - Resultado: ✅ Sucesso
  - Observação: O sistema respondeu com < 2s em 95% das requisições.

3. Arquitetura dos Ambientes
----------------------------
[imagem aqui]

- **Camada Web**: Nginx + Certificados HTTPS.
- **Camada de Aplicação**: Odoo + OpenEduCat.
- **Camada de Base de Dados**: PostgreSQL 14.
- **Monitorização**: Prometheus + Grafana.

4. Configurações Realizadas
---------------------------
- Configuração do **Nginx** para *reverse proxy* em todas as máquinas.
- Ativação de **certificados SSL/TLS** (Let's Encrypt).
- Ajuste de parâmetros no **PostgreSQL**:
  - `max_connections = 200`
  - `shared_buffers = 2GB`
- Criação de backups automáticos:
  - Frequência: diária
  - Retenção: 7 dias
- Integração com sistema de monitorização.
