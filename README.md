# medical-appointment-z
📝 prompt-chaining-article-generator
Um gerador técnico de artigos automatizado utilizando LangChain com estratégias avançadas de Prompt Chaining. Este projeto demonstra como criar fluxos de trabalho modulares onde o output de um prompt serve como input para o próximo, permitindo a criação de conteúdo estruturado e coerente.

Nota: O nome do projeto no package.json é prompt-chaining-article-generator, mas este README pode ser adaptado para o diretório atual (modulo03-mcp-na-pratica).

🚀 Funcionalidades Principais
Geração de Artigos Técnicos: Criação automática de artigos baseados em tópicos fornecidos.
Prompt Chaining: Arquitetura onde múltiplos prompts são encadeados para refinar o conteúdo (ex: Pesquisa → Estrutura → Redação → Revisão).
Templates Reutilizáveis: Uso de templates de prompt configuráveis para diferentes estilos ou formatos de artigo.
Multi-modelo: Suporte a modelos via OpenAI e Ollama (configurável via .env).
API RESTful: Servidor Fastify exposto para requisições externas.
Testes Robustos: Scripts dedicados para testes unitários, E2E e desenvolvimento.
🛠️ Tecnologias Utilizadas
Tecnologia	Versão	Descrição
LangChain	^1.2.17	Framework principal para orquestração de LLMs
@langchain/openai	^1.2.5	Integração com modelos OpenAI
@openrouter/sdk	^0.5.1	Acesso a modelos via OpenRouter (custo-eficiente)
Fastify	^5.7.4	Servidor web para expor endpoints de geração
Node.js	>=24.10.0	Ambiente de execução
📁 Estrutura do Projeto
Run
modulo03-mcp-na-pratica/
├── src/
│   ├── index.ts          # Ponto de entrada e lógica principal
│   ├── prompts/          # Templates de prompt (separados por funcionalidade)
│   └── chains/           # Definição das cadeias de prompts (chaining logic)
├── tests/
│   ├── unit.test.ts      # Testes unitários dos componentes
│   └── e2e.test.ts       # Testes de integração do fluxo completo
├── .env.example          # Modelo de variáveis de ambiente (API Keys, etc.)
├── package.json          # Dependências e scripts
└── README.md             # Documentação
🚀 Como Usar
1. Clonar e Configurar
Run
git clone <URL_DO_REPOSITORIO>
cd modulo03-mcp-na-pratica
npm install
2. Configurar Variáveis de Ambiente
Crie um arquivo .env baseado no exemplo:

Run
cp .env.example .env
# Adicione suas chaves API (OpenAI, OpenRouter, etc.)
3. Executar o Gerador
Modo Desenvolvimento (com hot-reload):
Run
npm run dev
O servidor estará rodando e pronto para receber requisições.

Produção:
Run
npm start
4. Usar a API
Após iniciar, envie uma solicitação para gerar um artigo:

Run
curl -X POST http://localhost:3000/generate \
  -H "Content-Type: application/json" \
  -d '{"topic": "Inteligência Artificial em 2024"}'
5. Rodar Testes
Todos os testes: npm run test
Testes Unitários (Dev): npm run test:unit:dev
Testes E2E (Dev): npm run test:e2e:dev
🧠 Como Funciona o Prompt Chaining
O projeto utiliza uma cadeia de prompts para garantir qualidade no conteúdo gerado:

Prompt 1 (Pesquisa/Brainstorming): Gera ideias e estrutura básica baseada no tópico.
Prompt 2 (Estruturação): Define títulos, subtítulos e pontos principais.
Prompt 3 (Redação): Escreve o conteúdo detalhado para cada seção.
Prompt 4 (Revisão/Polimento): Corrige erros, melhora o tom e formata o texto final.
Cada etapa pode ser configurada em src/prompts/*.ts e a lógica de encadeamento em src/chains/index.ts.

📝 Licença
Este projeto está licenciado sob a licença MIT.

💡 Dica para Desenvolvedores
Para personalizar o estilo dos artigos, edite os arquivos dentro da pasta src/prompts/ e ajuste a lógica de encadeamento em src/chains/. O sistema é modular, permitindo adicionar novos passos à cadeia facilmente.
