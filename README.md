# projeto-ensinando-falcoes-2026
Este projeto é dedicado a ensino de novos desenvolvedores em MakeCode

INTRODUÇÃO PIX
📱 PIX Service – Integração para Fintechs
Este repositório contém a implementação e documentação da funcionalidade PIX para a nossa fintech. O objetivo é fornecer uma interface simples, segura e escalável para criação, consulta e liquidação de transações via PIX, seguindo as diretrizes do Banco Central do Brasil.

🚀 Visão Geral
O módulo PIX oferece:

🔐 Segurança: comunicação criptografada, autenticação mTLS e conformidade com padrões do BACEN.

⚡ Alta performance: endpoints otimizados para baixa latência.

🧩 Flexibilidade: integração via API REST, Webhooks e suporte a QR Code dinâmico e estático.

📊 Observabilidade: logs estruturados, métricas e rastreamento distribuído.

🏗️ Arquitetura da Solução
A solução é composta por:

Código
/pix-service
 ├── src/
 │    ├── controllers/     # Endpoints REST
 │    ├── services/        # Regras de negócio PIX
 │    ├── clients/         # Comunicação com PSP/BACEN
 │    ├── webhooks/        # Processamento assíncrono
 │    └── utils/           # Helpers e middlewares
 ├── docs/                 # Documentação adicional
 ├── tests/                # Testes unitários e integrados
 └── README.md
🔧 Requisitos
Node.js 18+ ou outra stack equivalente

Certificados mTLS válidos (ICP-Brasil)

Chave PIX registrada no DICT

Credenciais do PSP parceiro

📡 Endpoints Principais
🔹 Criar Cobrança Imediata
POST /pix/cobranças

json
{
  "valor": "150.00",
  "descricao": "Pagamento de serviço",
  "chave": "email@exemplo.com",
  "infoAdicionais": [
    { "nome": "pedido", "valor": "12345" }
  ]
}
Resposta:

json
{
  "txid": "A1B2C3D4E5",
  "qrCode": "000201010212...",
  "status": "ATIVA"
}
🔹 Consultar Cobrança
GET /pix/cobranças/{txid}

🔹 Receber Notificações (Webhook)
O serviço expõe um endpoint configurável para receber notificações de liquidação:

POST /pix/webhook

json
{
  "endToEndId": "E123456789",
  "valor": "150.00",
  "horario": "2024-01-01T12:00:00Z"
}
🔐 Segurança
Autenticação via OAuth2 Client Credentials

Certificados mTLS obrigatórios

Validação de assinatura JWS

Rate limiting e proteção contra replay attacks

🧪 Testes
Execute:

Código
npm test
Inclui:

Testes unitários

Testes de integração com mocks do PSP

Testes de contrato (OpenAPI)

📘 Documentação Adicional
Especificação OpenAPI: /docs/openapi.yaml

Guia de homologação com PSP

Exemplos de QR Code dinâmico

🤝 Contribuição
Contribuições são bem-vindas. Para colaborar:

Crie uma branch feature/

Abra um Pull Request

Aguarde revisão do time

📄 Licença
Este projeto é distribuído sob a licença MIT.
