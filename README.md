# IstanciaGerenciadaSQL
Este laboratório tem como objetivo praticar o processo de configuração de uma instância de Banco de Dados na plataforma Microsoft Azure.

A Instância Gerenciada do SQL no Azure é um serviço de banco de dados inteligente e escalável que combina a ampla compatibilidade do motor do SQL Server com os benefícios de uma plataforma totalmente gerenciada como serviço (PaaS). É uma opção ideal para migrar aplicações locais de SQL Server para a nuvem com o mínimo de alterações, pois oferece recursos e funcionalidades semelhantes às de uma instância do SQL Server tradicional, mas com a vantagem de gerenciamento automatizado, alta disponibilidade e segurança integrada no Azure. 

**Como configurar uma Istancia Gerenciada do SQL no Azure**

Entre no Portal do Azure: Para criar sua instância no portal do Azure, primeiro você precisará entrar no portal do Azure e preencher as informações na página Criar Instância Gerenciada de SQL do Azure.
ETAPAS
1. Entre no portal do Azure.
2. Vá para o Hub SQL do Azure em aka.ms/azuresqlhub.
3. No painel da Instância Gerenciada de SQL do Azure, selecione Mostrar opções.
4. Na janela de opções da Instância Gerenciada de SQL do Azure , selecione Criar Instância Gerenciada de SQL.

Preencha as informações obrigatórias exigidas na guia Básico, que é o requisito mínimo para provisionar uma Instância Gerenciada de SQL.
- Assinatura: Sua assinatura.
- Grupo de recursos: Um grupo de recursos novo ou existente.
- Nome da instância gerenciada	Qualquer nome válido.
- Região	A região na qual você deseja criar a instância gerenciada de SQL.
- Pertence a um pool de instâncias?	Selecione Sim para que essa instância seja criada dentro de um pool de instâncias.
- Método de autenticação	Usar a autenticação do SQL. (Para este início rápido, use a autenticação SQL. Mas, para melhorar a segurança, use a autenticação do Microsoft Entra.)
- Logon de administrador da Instância Gerenciada	Qualquer nome de usuário válido. (Não use serveradmin, pois essa é uma função reservada no nível de servidor.)
- Senha:	Qualquer senha válida.	(A senha deve ter no mínimo 16 caracteres e atender a requisitos de complexidade definidos.)

Em Detalhes da instância gerenciada, selecione Configurar instância gerenciada na seção Computação + armazenamento para abrir a página Computação + armazenamento.

A descrição a seguir fornece recomendações para a computação e o armazenamento para sua instância gerenciada SQL de exemplo:

- Camada de Serviço	Uso Geral: atende à maioria das cargas de trabalho de produção e é a opção padrão. A camada de serviço Uso Geral de Última Geração aprimorada também é uma ótima escolha para a maioria das cargas de trabalho.
- Geração do hardware	Série Standard (Gen 5): geração de hardware padrão, que define os limites de computação e de memória.
- vCores	Designe um valor: Os vCores representam a quantidade exata de recursos de computação que sempre são provisionados para a carga de trabalho. Oito vCores é o padrão.
- Armazenamento em GB:	Designe um valor. Selecione-o com base no tamanho de dados esperado.
- Licença do SQL Server: Selecione o modelo de licenciamento aplicável.	Use o pagamento conforme o uso, uma licença SQL existente com o Benefício Híbrido do Azure ou habilite os direitos de failover híbrido
- Redundância do armazenamento de backup: O armazenamento de backup com redundância geográfica é o padrão e o recomendado, embora a redundância local e de zona geográfica permita maior flexibilidade de custo e residência de dados de região única.

Depois de designar sua configuração de Computação + Armazenamento, use Aplicar para salvar suas configurações e navegar de volta para a página Criar Instância Gerenciada SQL do Azure.

GUIA REDE
Preencha informações opcionais na guia Rede . Se você omitir essas informações, o portal aplicará as configurações padrão.

Rede virtual / sub-rede: Crie ou use uma rede virtual existente.	Se uma rede ou sub-rede não estiver disponível, ela deverá ser modificada para atender aos requisitos de rede antes de selecioná-la como um destino para a nova instância gerenciada de SQL.
Tipo de conexão: Escolha um tipo de conexão adequado.
Ponto de extremidade público:	Selecione Desabilitar.	Para que a instância gerenciada de SQL fique acessível por meio do ponto de extremidade de dados público, será necessário habilitar essa opção.
Permitir o acesso de (se o Ponto de extremidade público estiver habilitado)	Selecione Sem Acesso	O portal configura o grupo de segurança com um ponto de extremidade público.
De acordo com a situação, selecione uma das seguintes opções:
* Serviços do Azure: recomendamos essa opção quando você estiver se conectando de Power BI ou de outro serviço multilocatário.
* Internet: use para fins de teste quando quiser criar rapidamente uma instância gerenciada de SQL. Não recomendado para ambientes de produção.
* Sem acesso: esta opção cria a regra de segurança Negar. Modifique essa regra para tornar uma instância gerenciada de SQL acessível por meio de um ponto de extremidade público.

Selecione Examinar + criar para examinar suas escolhas antes de criar uma instância gerenciada de SQL. Ou defina as configurações de segurança selecionando Avançar: Configurações de segurança.

Guia Segurança
Para este início rápido, deixe as configurações na guia Segurança em seus valores padrão.

Selecione Examinar + criar para examinar suas escolhas antes de criar uma instância gerenciada de SQL. Ou defina mais configurações personalizadas selecionando Avançar: configurações adicionais.

Configurações adicionais
Preencha as informações opcionais na guia Configurações adicionais. Se você omitir essas informações, o portal aplicará as configurações padrão.

A tabela a seguir oferece detalhes sobre as informações na guia Configurações adicionais:

Ordenação	Escolha a ordenação que você deseja usar para sua instância gerenciada de SQL. Se estiver migrando bancos de dados do SQL Server, verifique a ordenação de origem usando SELECT SERVERPROPERTY(N'Collation') e use esse valor.
Fuso horário	Selecione o fuso horário observado pela instância gerenciada de SQL.
Replicação geográfica	Selecione Não.	Habilite essa opção somente se você planeja usar a instância gerenciada de SQL como um grupo de failover secundário.
Janela de manutenção	Escolha uma janela de manutenção adequada.

Selecione Examinar + criar para examinar suas escolhas antes de criar uma instância gerenciada de SQL. Ou, então, configure as marcas do Azure selecionando Avançar: Marcas (recomendado).

Marcações
Adicione marcas aos recursos no modelo do ARM (modelo do Azure Resource Manager). As marcas ajudam você a organizar logicamente seus recursos. Os valores de marca são mostrados nos relatórios de custo e permitem outras atividades de gerenciamento por marca. Considere pelo menos marcar sua nova instância gerenciada de SQL com a marca Proprietário para identificar quem criou e a marca Ambiente para identificar se esse sistema é Produção, Desenvolvimento etc.

Examinar + criar
Na guia Revisar + criar , examine suas escolhas e selecione Criar para implantar sua instância gerenciada de SQL.

Fonte: https://learn.microsoft.com/pt-br/azure/azure-sql/managed-instance/instance-create-quickstart?view=azuresql&tabs=azure-portal
