
🔷 Fase 1: Planejamento e Modelagem
 Definir os requisitos funcionais e não funcionais
 Modelar o fluxo do sistema (professor, participante, quiz)
 Definir o modelo de dados OLAP (fato e dimensões)
 Desenhar as estruturas de dados no Redis
 
🔷 Fase 2: Configuração dos Ambientes
 Configurar Redis local ou em container Docker
 Configurar o banco OLAP (PostgreSQL ou Snowflake, por ex.)
 Criar script de criação de tabelas OLAP (fato e dimensões)
 Configurar o projeto Python com virtualenv ou poetry
 Instalar dependências (fastapi, redis, sqlalchemy, etc.)
 
🔷 Fase 3: Funcionalidades do Professor
 Criar endpoint para adicionar perguntas
 Armazenar pergunta no Redis e marcar como ativa
 Salvar pergunta no banco OLAP (dim_pergunta)
 Criar endpoint para listar todas as perguntas ativas
 
🔷 Fase 4: Funcionalidades do Participante
 Criar endpoint para iniciar quiz (criar sessão no Redis)
 Listar pergunta atual da sessão
 Enviar resposta da pergunta
 Verificar se resposta está correta
 Atualizar progresso no Redis (pontuação, respostas)
 Armazenar no Redis os dados para posterior envio ao OLAP
 Finalizar quiz e transferir dados para o banco analítico:
Registrar resposta (fato_respostas)
Atualizar dim_usuario e dim_tempo, se necessário

🔷 Fase 5: Relatórios e Estatísticas
 Criar endpoints para visualizar estatísticas:
Desempenho por categoria
Média de tempo por pergunta
Ranking de participantes
 Criar queries agregadas para OLAP (consultas exemplo)
 (Opcional) Criar cache de estatísticas mais acessadas no Redis
 
🔷 Fase 6: Melhorias e Extras
 Adicionar TTL para sessões no Redis
 Criar mecanismo de remoção automática de perguntas expiradas
 Adicionar autenticação básica para professores e participantes
 (Opcional) Frontend simples com Streamlit ou HTML+JS
 (Opcional) Dockerizar o projeto para facilitar o deploy
 (Opcional) Incluir logs com logging ou integração com ferramentas de observabilidade
 
