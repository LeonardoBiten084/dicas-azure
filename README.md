# Boas Práticas e Dicas de Uso – Microsoft Azure

Este documento traz uma coleção de dicas práticas e recomendações técnicas para melhorar o uso do Microsoft Azure em ambientes de desenvolvimento, teste e produção. As orientações aqui são baseadas em boas práticas amplamente adotadas por profissionais da área.

---

## 📁 1. Organização com Resource Groups

**O que são:** grupos lógicos que armazenam recursos do Azure relacionados a um mesmo projeto ou aplicação.

**Dica:** crie grupos separados por ambiente e finalidade.  
**Exemplo:**
- `rg-app-ecommerce-dev`
- `rg-app-ecommerce-prod`
- `rg-analytics-infra`

**Por que usar?**
- Facilita a exclusão em lote
- Ajuda no controle de custos
- Melhora a organização por projeto

---

## 🏷️ 2. Uso de Tags (Etiquetas)

**Tags** são pares chave-valor que ajudam a categorizar e identificar recursos.

**Exemplos de tags:**
"env" = "prod"
"owner" = "time-analytics"
"cost-center" = "TI-2025"
Por que usar?

Auxilia em auditorias e controle de gastos

Permite relatórios e filtros no portal

Melhora a governança de TI

## 🌍 3. Escolha estratégica da região
Dica: escolha sempre a região geográfica mais próxima dos seus usuários.

Impacto direto:

Redução da latência

Melhor performance

Menores custos de saída de dados (egresso)

Exemplo: Para usuários no Brasil, use Brazil South (São Paulo) sempre que possível.

## 🔐 4. Segurança e Controle de Acesso
Use Azure Role-Based Access Control (RBAC) para atribuir permissões mínimas necessárias por função.

Integre com o Azure Active Directory (AAD) para autenticação centralizada.

Habilite MFA (autenticação multifator) para todos os administradores.

Evite: usar contas de administrador para tarefas rotineiras.
Melhor prática: use grupos de segurança com permissões específicas.

## 📈 5. Monitoramento e Logs
Sempre habilite ferramentas de observabilidade:

Application Insights: monitora performance de apps web.

Azure Monitor: coleta métricas e logs de diversos recursos.

Log Analytics: permite consultar eventos com linguagem Kusto (KQL).

Dica: configure alertas automáticos para:

Picos de CPU ou memória

Erros HTTP 5xx em APIs

Fails em funções ou pipelines

## 💸 6. Controle de Custos
Utilize orçamentos e alertas de custo via Azure Cost Management.

Acompanhe os custos por subscription, resource group ou tag.

Evite recursos em execução contínua desnecessária em ambientes de teste/dev.

Dica: desligue VMs e bancos fora do expediente em ambientes de desenvolvimento.

## 🧪 7. Isolamento de Ambientes
Separe os recursos por ambiente:

• Dev

• Homologação (Staging/Test)

• Produção (Prod)

• Como fazer isso:

• Criando resource groups distintos

• Usando tags (env=dev, env=prod)

• Criando múltiplas subscriptions, se necessário

## 🧰 8. Variáveis de Ambiente e Configurações
Em App Services, Functions ou Containers:

Nunca exponha dados sensíveis (como strings de conexão) no código-fonte.

Use as Application Settings para armazenar variáveis de ambiente.

Marque chaves sensíveis como deployment slot setting quando usar slots.

## 🛠️ 9. Deploy e Integração Contínua (CI/CD)
Use o Azure DevOps ou GitHub Actions para automação de deploy.

Crie pipelines separados por ambiente (com aprovação manual para produção).

Automatize testes e validações antes do deploy.

Dica: Utilize slots de deployment no App Service para fazer swap entre staging e produção sem downtime.

## 📦 10. Automação e Infraestrutura como Código
Use ARM Templates, Bicep, Terraform ou Pulumi para provisionar recursos de forma reprodutível.

Versione sua infraestrutura no repositório Git, junto ao código.

Vantagens:

• Recriação de ambientes em minutos

• Controle de mudanças via versionamento

• Escalabilidade e consistência

Feito por **Leonardo Bitencourt**

