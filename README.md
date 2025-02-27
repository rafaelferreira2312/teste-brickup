# Desafio BrickUp - Full Stack PL (Versão 1.5.7)

## Introdução
Este projeto tem como objetivo projetar uma arquitetura de software na AWS para uma plataforma de gerenciamento de projetos de construção. A solução permitirá que arquitetos, engenheiros, empreiteiros e outras partes interessadas colaborem de forma eficiente compartilhando documentos, modelos 3D, cronogramas, orçamentos e comunicação em tempo real.

## Objetivos da Arquitetura
- **Escalabilidade**: Deve suportar um alto volume de usuários simultâneos e grande carga de dados.
- **Disponibilidade**: Garantia de alta disponibilidade com redundância e resiliência.
- **Segurança**: Proteção de dados confidenciais e conformidade com boas práticas de segurança.
- **Facilidade de Manutenção**: Uso de serviços gerenciados para reduzir custos operacionais.
- **Automatização**: Implementação de CI/CD para implantação rápida e segura.

## Infraestrutura na AWS

### 1. **Frontend Web Application**
- **Serviços AWS Utilizados**:
  - **Amazon S3**: Armazena arquivos estáticos da aplicação.
  - **Amazon CloudFront**: CDN para distribuir o conteúdo de forma rápida e segura.

### 2. **Backend API**
- **Serviços AWS Utilizados**:
  - **Amazon API Gateway**: Gerencia requisições para o backend.
  - **AWS Lambda**: Executa a lógica de negócio de forma serverless.

### 3. **Banco de Dados**
- **Serviços AWS Utilizados**:
  - **Amazon DynamoDB**: Banco de dados NoSQL para metadados dos projetos.
  - **Amazon RDS**: Banco de dados relacional para armazenar dados estruturados.

### 4. **Armazenamento de Arquivos**
- **Serviços AWS Utilizados**:
  - **Amazon S3**: Armazena documentos, imagens, vídeos e modelos 3D.

### 5. **Comunicação (Chat em Tempo Real)**
- **Serviços AWS Utilizados**:
  - **Amazon Chime SDK**: Gerencia mensagens instantâneas e chamadas de vídeo.

### 6. **Alertas via E-mail**
- **Serviços AWS Utilizados**:
  - **Amazon SES**: Envio de e-mails transacionais e notificativos.

### 7. **Painel Administrativo**
- **Serviços AWS Utilizados**:
  - **AWS Amplify ou AWS AppSync**: Gerencia os dados exibidos no painel de administração.

### 8. **CI/CD - Integração Contínua e Entrega Contínua**
- **Serviços AWS Utilizados**:
  - **AWS CodePipeline**: Automatiza a implantação da aplicação.
  - **AWS CodeBuild**: Constrói e testa o código antes da implantação.

## Diagramas de Infraestrutura

Os diagramas estão incluídos na documentação anexada ao repositório e podem ser visualizados aqui:
![Arquitetura AWS](/projeto%20de%20construção%20em%20nuvem%20-%20AWS.jpgprojeto-de-construcao-em-nuvem-AWS.jpg)

## Justificativa para Escolhas de Serviços

| Necessidade | Serviço AWS Escolhido | Justificativa |
|-------------|------------------|--------------|
| Armazenamento de arquivos | Amazon S3 | Alta disponibilidade e escalabilidade para grandes volumes de dados. |
| API backend | API Gateway + AWS Lambda | Arquitetura serverless com baixa latência e custo otimizado. |
| Banco de dados | Amazon RDS e DynamoDB | Combinação de banco relacional e NoSQL para alta performance e flexibilidade. |
| Chat em tempo real | Amazon Chime SDK | Plataforma escalável para comunicação de equipes. |
| Notificações por e-mail | Amazon SES | Serviço gerenciado de e-mails transacionais. |
| Painel administrativo | AWS Amplify/AppSync | Solução gerenciada para gerenciar a interface administrativa. |
| CI/CD | AWS CodePipeline + CodeBuild | Automatiza a implantação e manutenção da plataforma. |

## Requisitos de Segurança Implementados

- **Controle de Acesso**: IAM Policies para restringir acessos e permissões.
- **Criptografia**: Armazenamento de dados com criptografia em repouso e em trânsito.
- **Redundância**: Implantado em múltiplas zonas de disponibilidade para garantir alta disponibilidade.
- **Monitoramento**: Uso de AWS CloudWatch para logs e alertas de segurança.
- **Proteção contra DDoS**: Amazon Shield e AWS WAF para prevenção de ataques.

## Como Rodar o Projeto (Deploy)

### 1. Configurar a AWS CLI
```sh
aws configure
```

### 2. Criar o Bucket S3 para Frontend
```sh
aws s3 mb s3://meu-bucket-de-arquivos
```

### 3. Configurar API Gateway e Lambda
```sh
aws apigateway create-rest-api --name "ProjetoConstrucaoAPI"
```

### 4. Criar Banco de Dados RDS
```sh
aws rds create-db-instance --db-instance-identifier projetodb --engine mysql --allocated-storage 20 --db-instance-class db.t3.micro --master-username admin --master-user-password minhaSenhaSegura
```

### 5. Configurar CI/CD
```sh
aws codepipeline create-pipeline --pipeline-name MeuPipeline --role-arn arn:aws:iam::123456789012:role/service-role/AWSCodePipelineServiceRole
```

## Conclusão

Esta solução propõe uma arquitetura robusta e escalável na AWS para um sistema de gerenciamento de projetos de construção, garantindo segurança, alta disponibilidade e eficiência. O uso de serviços gerenciados minimiza a complexidade operacional e permite a rápida implementação de novas funcionalidades.

