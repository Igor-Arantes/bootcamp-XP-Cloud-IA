# Introdução à Computação em Nuvem (Cloud)

## O que é Cloud?

**Cloud Computing** ou **Computação em Nuvem** é um modelo de fornecimento de recursos computacionais (como servidores, armazenamento, bancos de dados, redes, software, etc.) pela internet. Esses recursos são disponibilizados sob demanda por provedores de serviços como AWS, Microsoft Azure, Google Cloud, entre outros.

---

## Diferenças entre Cloud e o Modelo On-Premise

| Característica         | On-Premise                              | Cloud                                        |
|------------------------|------------------------------------------|---------------------------------------------|
| **Infraestrutura**     | Instalada localmente (na empresa)        | Hospedada remotamente pelos provedores      |
| **Custos**             | Alto investimento inicial (CAPEX)        | Custo sob demanda (OPEX)                    |
| **Manutenção**         | Responsabilidade da empresa              | Responsabilidade do provedor de cloud       |
| **Escalabilidade**     | Limitada à capacidade física instalada   | Altamente escalável e elástica              |
| **Tempo de implementação** | Mais demorado                      | Rápido, quase imediato                       |
| **Segurança**          | Controlada internamente                  | Gerenciada pelo provedor com altos padrões  |

---

## Benefícios da Computação em Nuvem

- **Escalabilidade:** É possível aumentar ou reduzir recursos conforme a demanda.
- **Redução de custos:** Elimina a necessidade de grandes investimentos iniciais.
- **Alta disponibilidade:** Serviços em nuvem oferecem redundância e recuperação de desastres.
- **Acesso remoto:** Acesso aos serviços e dados de qualquer lugar com internet.
- **Inovação rápida:** Permite testes e implantações ágeis de novos produtos e soluções.
- **Segurança:** Fornecedores implementam camadas avançadas de proteção e conformidade.

---

## Características da Computação em Nuvem

- **Sob demanda:** Recursos são provisionados conforme necessário, sem intervenção manual.
- **Ampla rede de acesso:** Acesso via internet de qualquer local.
- **Pool de recursos:** Compartilhamento eficiente de recursos físicos e virtuais entre clientes.
- **Elasticidade rápida:** Ajuste automático dos recursos conforme a carga de trabalho.
- **Serviço medido:** Monitoramento e controle de uso para cobrança transparente e precisa.

---

A adoção de cloud transforma a forma como empresas operam e inovam, tornando-se um pilar essencial da transformação digital.

# Criação de Máquina Virtual Simples na Azure para Hospedagem de API e Página Web

## Objetivo
Implementar uma máquina virtual (VM) simples na Microsoft Azure para hospedar:
- Uma API com poucas requisições
- Uma página web estática ou de baixo tráfego

---

## Passo a Passo da Criação via Interface (Portal Azure)

### 1. Acesso ao Portal Azure
- Acesso feito via: [https://portal.azure.com](https://portal.azure.com)

---

### 2. Navegação até o Serviço de Máquinas Virtuais
- Menu lateral esquerdo → **Máquinas Virtuais** → **+ Criar**
- Escolha: **Máquina virtual do Azure**

---

### 3. Configurações Básicas

#### Assinatura e Grupo de Recursos
- **Assinatura:** padrão da conta
- **Grupo de Recursos:** `web-hosting-rg`
  - *Motivo:* Organização e gerenciamento fácil de recursos relacionados ao projeto.

#### Nome da Máquina Virtual
- **Nome:** `vm-web-api`
  - *Motivo:* Nome descritivo e fácil de identificar.

#### Região
- **Região:** Brasil Sul (ou região mais próxima ao público alvo)
  - *Motivo:* Menor latência para usuários locais.

#### Imagem do SO
- **Imagem:** Ubuntu Server 22.04 LTS
  - *Motivo:* Estabilidade, suporte de longo prazo e compatibilidade com servidores web e APIs Python/Node.js.

#### Tamanho
- **Tamanho:** `Standard B1s (1 vCPU, 1 GB RAM)`
  - *Motivo:* Ideal para workloads leves e custo reduzido (paga por uso).

#### Método de Autenticação
- **Tipo:** Chave SSH pública
  - *Motivo:* Mais seguro que autenticação por senha.

---

### 4. Configurações de Disco

- **Tipo de Disco:** Disco SSD padrão
  - *Motivo:* Balanceia custo e performance para aplicações leves.

---

### 5. Rede

- **VNet/Sub-rede:** Criada automaticamente ou já existente
- **IP público:** Sim (estático opcional)
- **Portas abertas:**
  - Porta 22 (SSH)
  - Porta 80 (HTTP)
  - Porta 443 (HTTPS)
  - *Motivo:* Acesso remoto para configuração e acesso web externo.

---

### 6. Monitoramento

- **Monitoramento habilitado:** Sim
  - *Motivo:* Para acompanhar o desempenho e diagnosticar problemas.

---

### 7. Revisão e Criação

- Revisão das configurações e clique em **Criar**
- Após provisionamento, acesso à VM via terminal SSH:

```bash
ssh azureuser@<IP-da-VM>

