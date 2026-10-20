# Manager ADV — CS Lawyers

**Plataforma de gestão jurídica, atendimento inteligente e automação de processos.**

## Sobre o projeto

O **Manager ADV** é uma plataforma desenvolvida para centralizar e aprimorar os processos operacionais de um escritório de advocacia, reunindo módulos de atendimento, gestão de atividades, auditoria, protocolo, acompanhamento processual e automação com inteligência artificial.

O projeto prevê a integração de um agente de IA desenvolvido no **n8n**, responsável por auxiliar no atendimento inicial, organizar informações, classificar solicitações, apoiar agendamentos e executar automações administrativas por meio de integrações configuradas.

O objetivo é construir um ambiente integrado, organizado e escalável, reduzindo tarefas repetitivas e facilitando o acompanhamento dos atendimentos.

> **Status:** em desenvolvimento e validação local. As funcionalidades e integrações devem ser consideradas operacionais somente após seus respectivos testes.

## Objetivos

- Centralizar os fluxos de trabalho em uma única plataforma.
- Aprimorar a organização e o acompanhamento dos atendimentos.
- Automatizar tarefas operacionais repetitivas.
- Integrar inteligência artificial aos processos de triagem e organização de informações.
- Conectar o sistema a ferramentas externas por meio de APIs e webhooks.
- Facilitar o agendamento de atendimentos e o encaminhamento para responsáveis.
- Manter rastreabilidade das operações e tratamento adequado de erros.
- Preparar uma arquitetura modular para futuras integrações.

## Módulos da plataforma

A plataforma contempla módulos voltados à organização das rotinas jurídicas, incluindo:

| Módulo | Finalidade |
|---|---|
| Atendimento | Centralização e acompanhamento das conversas e solicitações dos clientes. |
| Produção | Organização de atividades relacionadas à produção jurídica. |
| Auditoria | Apoio à conferência e ao controle de processos e informações. |
| Protocolo | Organização de atividades relacionadas aos protocolos. |
| Andamentos | Acompanhamento de informações e movimentações processuais. |
| Assessor | Apoio às atividades operacionais e à organização de demandas. |
| Treinamento IA | Configuração e evolução das instruções e comportamentos da inteligência artificial. |
| Configurações | Gerenciamento das configurações disponíveis na plataforma. |

A disponibilidade e o nível de implementação de cada funcionalidade dependem da versão atual do sistema.

## Agente de IA e automações

O projeto prevê um agente de IA orquestrado pelo n8n, com fluxos modulares para receber mensagens, interpretar solicitações, organizar informações e acionar ferramentas autorizadas.

### Funcionalidades planejadas

- Triagem inicial de contatos.
- Classificação de solicitações trabalhistas, cíveis e administrativas.
- Coleta estruturada de informações iniciais.
- Recuperação de contexto da conversa.
- Sugestões de respostas e apoio ao atendimento.
- Encaminhamento de solicitações para atendimento humano.
- Notificações por e-mail.
- Consulta de disponibilidade e agendamento de compromissos.
- Integração com informações processuais, conforme as operações disponíveis na API do ProJuris Adv.
- Registro de resultados, erros e estados das automações.

As funcionalidades que dependem de serviços externos serão habilitadas conforme a configuração e a validação de cada integração.

## Arquitetura e tecnologias

A arquitetura utiliza ou prevê o uso das seguintes tecnologias, conforme os componentes efetivamente implementados no projeto:

- **Frontend:** React e TypeScript.
- **Interface:** Tailwind CSS e componentes shadcn/ui.
- **Persistência e serviços de backend:** Supabase.
- **Automação:** n8n.
- **Inteligência artificial:** provedor de modelo de IA configurável.
- **Gestão jurídica:** ProJuris Adv, mediante API e operações suportadas.
- **Agenda:** Google Calendar.
- **Notificações:** Gmail / Google Workspace.
- **Mensageria:** camada de integração preparada para um provedor de WhatsApp a ser definido.

## Ambiente de testes

O desenvolvimento prioriza a validação local antes da publicação do sistema.

O primeiro fluxo de integração deverá permitir:

1. Enviar uma mensagem fictícia pelo módulo Atendimento.
2. Encaminhar os dados para um webhook do n8n.
3. Processar a solicitação por meio do fluxo de triagem.
4. Retornar uma resposta estruturada.
5. Exibir o resultado na conversa correspondente.
6. Testar o encaminhamento para atendimento humano.

O modo simulado permite validar o fluxo sem depender de um canal real de WhatsApp. Os dados simulados devem permanecer identificados e separados dos registros reais.

## Integrações externas

### n8n

Responsável por orquestrar os workflows, executar as automações e conectar o Manager ADV aos serviços externos.

### ProJuris Adv

Integração prevista para consultar e, quando suportado e autorizado, atualizar informações jurídicas. Cada operação deverá ser validada de acordo com a documentação da API e as permissões disponíveis.

### Google Calendar

Integração prevista para consultar disponibilidade e criar eventos na conta autorizada, após a configuração da autenticação.

### Gmail

Utilizado para notificações operacionais e encaminhamento de atendimentos que precisem de intervenção humana.

### WhatsApp

A arquitetura poderá receber um provedor de mensageria posteriormente. A integração real depende da escolha do provedor, da configuração das credenciais e da validação dos fluxos de envio e recebimento.

## Configuração e execução local

Os comandos exatos dependem dos arquivos e scripts disponíveis na versão do projeto.

### 1. Pré-requisitos

- Node.js em versão compatível com o projeto.
- npm ou o gerenciador de pacotes indicado pelos arquivos do repositório.
- n8n instalado e acessível.
- Credenciais do Supabase, caso a execução dependa dele.
- Credenciais adicionais para os serviços externos que forem habilitados.

### 2. Instalação

Clone o repositório e entre no diretório do projeto:

```bash
git clone <URL_DO_REPOSITORIO>
cd <DIRETORIO_DO_PROJETO>
```

Instale as dependências utilizando o gerenciador de pacotes correspondente ao projeto. Para npm, caso exista um `package.json` compatível:

```bash
npm install
```

### 3. Variáveis de ambiente

Consulte o arquivo `.env.example`, caso exista, para identificar as variáveis necessárias.

Crie o arquivo de ambiente apropriado para o projeto e configure os valores exigidos localmente. Não inclua credenciais reais no repositório.

As configurações podem incluir:

- URL e chave pública do Supabase.
- URLs dos webhooks do n8n.
- Credenciais e parâmetros de integração com APIs externas.
- Configuração do provedor de IA.
- Parâmetros de autenticação do Google Calendar e Gmail.

Os nomes exatos das variáveis devem corresponder aos utilizados pelo código.

### 4. Inicialização do frontend

Verifique os scripts disponíveis no `package.json`. Se o projeto utilizar o script padrão do Vite, a inicialização será:

```bash
npm run dev
```

O terminal informará o endereço local de acesso.

### 5. Configuração do n8n

1. Abra a instância local do n8n.
2. Importe o workflow JSON correspondente ao ambiente de teste.
3. Configure as credenciais necessárias.
4. Execute o workflow em modo de teste.
5. Configure a URL do webhook no Manager ADV.
6. Envie um payload de teste e confira a resposta.

A URL de teste e a URL de produção de um webhook podem ser diferentes. Utilize a URL correspondente ao modo de execução configurado.

## Segurança e responsabilidade

O sistema deve adotar controles adequados para proteger informações pessoais e jurídicas, incluindo:

- Armazenamento seguro de credenciais.
- Validação dos dados recebidos.
- Controle de acesso às informações.
- Tratamento de erros e prevenção de execuções duplicadas.
- Separação entre dados simulados e reais.
- Registro de operações sem exposição desnecessária de informações sensíveis.
- Encaminhamento humano para questões que exijam avaliação jurídica.

O agente de IA destina-se a auxiliar o atendimento e as tarefas operacionais. Ele não deve substituir a análise do advogado, emitir conclusões jurídicas definitivas ou prometer resultados.

## Roadmap

- [ ] Validar a inicialização local do Manager ADV.
- [ ] Tornar o módulo Atendimento funcional de ponta a ponta.
- [ ] Implementar o modo simulado de mensagens.
- [ ] Integrar o Manager ADV ao webhook de teste do n8n.
- [ ] Implementar triagem e classificação inicial com IA.
- [ ] Configurar persistência e contexto das conversas.
- [ ] Implementar encaminhamento humano e notificações por Gmail.
- [ ] Configurar e testar o Google Calendar.
- [ ] Validar as operações disponíveis na API do ProJuris Adv.
- [ ] Integrar o provedor de mensageria escolhido.
- [ ] Executar testes de segurança, falhas e duplicidade.
- [ ] Preparar o ambiente para publicação.

## Licença

Licença ainda não especificada. O uso e a distribuição deste projeto devem seguir a licença definida pelo responsável pelo repositório.
