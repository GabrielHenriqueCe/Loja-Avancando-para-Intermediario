# Loja-Avancando-para-Intermediario

> **Evolução do projeto de fundamentos para Programação Orientada a Objetos**  
> Sistema profissional de gestão de vendas aplicando encapsulamento, classes e boas práticas de POO

---

## 📖 Sobre o Projeto

Este é a **segunda versão** do meu sistema de vendas, agora completamente refatorado utilizando **Programação Orientada a Objetos (POO)**. Representa a evolução natural do aprendizado, migrando de uma abordagem procedural com métodos estáticos para uma arquitetura orientada a objetos, aplicando os pilares fundamentais da POO.

### 🔗 Links Relacionados
- **📚 Versão com Fundamentos (Procedural):** [Loja-Simples-Utilizando-os-Fundamentos](https://github.com/GabrielHenriqueCe/Loja-Simples-Utilizando-os-Fundamentos)

---

## 🎯 Objetivos do Projeto

✅ Aplicar os **4 pilares da POO** (Encapsulamento, Herança, Polimorfismo, Abstração)  
✅ Demonstrar **evolução técnica** do paradigma procedural para orientado a objetos  
✅ Implementar **separação de responsabilidades** com classes especializadas  
✅ Praticar **boas práticas** de código limpo e arquitetura  
✅ Criar **base sólida** para sistemas escaláveis e manuteníveis

---

## 🏗️ Arquitetura - Paradigma Orientado a Objetos

### 📦 Classes Implementadas

```
Pratica/
├── Produto          → Gerenciamento de produtos e estoque
├── Caixa            → Controle financeiro e descontos
├── Menu             → Interface e navegação do usuário
├── Ler              → Validação e leitura de dados
└── Program          → Orquestração e fluxo principal
```

#### **Classe `Produto`**
Responsabilidade: Encapsular dados e comportamentos de produtos

**Campos Privados (Encapsulamento):**
- `codigo`, `nome`, `preco`
- `quantidadeEstoque`, `quantidadeVendida`, `valorTotalVendas`

**Métodos Públicos:**
- `SetCodigo()`, `GetCodigo()` - Acesso controlado ao código
- `SetNome()`, `GetNome()` - Manipulação do nome
- `SetPreco()`, `GetPreco()` - Validação de preço (não negativo)
- `AdicionarEstoque()`, `RemoverEstoque()` - Gestão de estoque com validação
- `RegistrarVenda()` - Controle de vendas realizadas
- `ExibirInfo()` - Apresentação formatada dos dados

#### **Classe `Caixa`**
Responsabilidade: Gerenciar sistema financeiro e políticas de desconto

**Campos Privados:**
- `saldo` - Controle financeiro
- `valorMinimoDesconto` - Threshold para aplicação
- `percentualDesconto` - Porcentagem configurável

**Métodos Públicos:**
- Getters e Setters para todos os campos
- Controle centralizado de políticas comerciais

#### **Classe `Menu`**
Responsabilidade: Interface com usuário e navegação

**Métodos Estáticos:**
- `ExibirMenuInicial()` - Menu principal
- `ExibitMenuRelatorio()` - Relatórios e configurações
- `ExibirMenuEdit()` - Edição de produtos
- `ExibirMenuEstoque()` - Gestão de inventário
- `ExibirMenuVenda()` - Processamento de vendas
- `chamarMenu()` - Factory method para menus
- `Pausa()` - Controle de fluxo

#### **Classe `Ler`**
Responsabilidade: Validação robusta de entrada de dados

**Métodos Estáticos:**
- `LerOpcao()` - Validação de opções de menu
- `LerDecimal()` - Validação de valores monetários
- `Confirmar()` - Confirmação de ações críticas (s/n)

---

## 🚀 Funcionalidades

### 💰 Sistema de Vendas
- ✅ Seleção de produtos com informações detalhadas
- ✅ Validação de quantidade disponível em estoque
- ✅ Aplicação automática de descontos configuráveis
- ✅ Feedback completo: produto, quantidade, desconto e total
- ✅ Atualização automática de estoque e saldo
- ✅ Registro de histórico de vendas

### 📊 Relatórios e Gestão
- ✅ Visualização de saldo atual do caixa
- ✅ Relatório de vendas por produto
- ✅ Total vendido (quantidade e valor)
- ✅ Configuração de valor mínimo para desconto
- ✅ Ajuste de percentual de desconto

### ✏️ Edição de Produtos
- ✅ Alterar nome dos produtos
- ✅ Modificar preços com validação
- ✅ Interface intuitiva com cancelamento de operações

### 📦 Controle de Estoque
- ✅ Adicionar produtos ao inventário
- ✅ Remover produtos com validação de disponibilidade
- ✅ Visualização em tempo real das quantidades

---

## 🔄 Da Programação Procedural para POO

### Comparação de Paradigmas

| Aspecto            | Versão Procedural                 | Versão POO 
|--------------------|-----------------------------------|------------
| **Dados**          | Variáveis globais dispersas       | Encapsulados em classes 
| **Organização**    | Métodos estáticos soltos          | Classes com responsabilidades claras 
| **Reutilização**   | Repetição de código               | Objetos instanciáveis 
| **Manutenção**     | Alterações impactam todo código   | Mudanças isoladas por classe 
| **Escalabilidade** | Difícil adicionar funcionalidades | Fácil extensão via herança 
| **Validação**      | Espalhada pelos métodos           | Centralizada nos Setters 

### Exemplo Prático de Refatoração

**Antes (Procedural):**
```csharp
static double Produto1Valor = 1500.00;
static int Produto1Quantidade = 15;
static string Produto1 = "Notebook";

static void processarVenda(int quantidade) {
    // Lógica misturada com dados globais
}
```

**Depois (POO):**
```csharp
class Produto {
    private double preco;
    private int quantidadeEstoque;
    private string nome;
    
    public void SetPreco(double novoPreco) {
        if (novoPreco >= 0) {
            preco = novoPreco;
        }
    }
    
    public void RemoverEstoque(int quantidade) {
        if (quantidade > 0 && quantidade <= quantidadeEstoque) {
            quantidadeEstoque -= quantidade;
        }
    }
}

// Uso:
Produto p1 = new Produto();
p1.SetNome("Notebook");
p1.SetPreco(1500.00);
```

---

## 🎓 Conceitos de POO Aplicados

### 🔒 Encapsulamento
- **Campos privados:** Dados protegidos de acesso direto
- **Métodos públicos:** Interface controlada para manipulação
- **Validação:** Regras de negócio nos Setters (ex: preço não negativo)

```csharp
private double preco; // Acesso restrito

public void SetPreco(double novoPreco) {
    if (novoPreco >= 0) { // Validação centralizada
        preco = novoPreco;
    }
}
```

### 🏗️ Abstração
- **Ocultação de complexidade:** Usuário interage apenas com métodos públicos
- **Separação de responsabilidades:** Cada classe tem papel específico
- **Interface simplificada:** `ExibirInfo()` esconde detalhes de formatação

### 🎯 Coesão
- **Classe Produto:** Só gerencia dados e comportamentos de produtos
- **Classe Caixa:** Exclusivamente para controle financeiro
- **Classe Menu:** Apenas interface e navegação
- **Classe Ler:** Somente validação de entrada

### 🔗 Baixo Acoplamento
- Classes independentes e reutilizáveis
- Mudanças em uma classe não quebram outras
- Facilita testes e manutenção

---

## 💻 Tecnologias e Conceitos

**Linguagem:** C# (.NET Console Application)  
**Paradigma:** Programação Orientada a Objetos  
**Conceitos Aplicados:**
- Classes e Objetos
- Encapsulamento (private/public)
- Métodos Get/Set
- Instanciação de objetos (`new`)
- Separação de responsabilidades
- Validação em camadas
- Métodos estáticos utilitários

---

## 🎮 Como Usar

### Menu Principal
1. **Relatórios e Opções** - Visualize vendas e configure descontos
2. **Editar Produtos** - Altere nomes e preços
3. **Atualizar Estoque** - Adicione ou remova produtos
4. **Realizar Venda** - Processe vendas com desconto automático
5. **Sair** - Encerre o sistema

### Fluxo de Venda Típico
1. Acesse **Realizar Venda**
2. Escolha o produto pelo código
3. Informe a quantidade desejada
4. Confirme a venda (s/n)
5. Sistema aplica desconto se aplicável
6. Estoque e saldo atualizados automaticamente

---

## 📈 Roadmap - Próximas Evoluções

### 🔜 Em Desenvolvimento
- [ ] **Arrays and Strings** - Manipulação avançada de coleções e textos
- [ ] **More On Classes** - Aprofundamento em POO
- [ ] **Inheritance & Polymorphism** - Hierarquias de classes e sobrescrita
- [ ] **Structs, Enums, Exceptions & Files** - Tipos de valor e tratamento de erros
- [ ] **Generics** - Classes e métodos genéricos reutilizáveis

### 🎯 Melhorias Futuras
- [ ] Implementar **Herança** (classe ProdutoPerecivel extends Produto)
- [ ] Adicionar **Polimorfismo** (métodos CalcularDesconto override)
- [ ] Criar **Interfaces** (IVendavel, IEstocavel)
- [ ] Sistema de **Exceções customizadas**
- [ ] Padrão **Repository** para gerenciar coleções
- [ ] **LINQ** para consultas em produtos
- [ ] **Serialização** (salvar/carregar dados em JSON)

---

## 📊 Comparação: Fundamentos vs POO

| Métrica              | Versão Procedural | Versão POO 
|----------------------|-------------------|------------
| **Linhas de Código** | ~600 linhas       | ~450 linhas 
| **Complexidade**     | Alta (tudo junto) | Baixa (separado) 
| **Reutilização**     | Baixa             | Alta 
| **Testabilidade**    | Difícil           | Fácil 
| **Manutenibilidade** | Média             | Alta 
| **Escalabilidade**   | Limitada          | Excelente 

---

## 🎯 Lições Aprendidas

### Do Procedural para POO
✅ **Organização:** Código mais estruturado e legível  
✅ **Proteção:** Dados seguros com encapsulamento  
✅ **Clareza:** Responsabilidades bem definidas  
✅ **Flexibilidade:** Fácil adicionar novas funcionalidades  
✅ **Profissionalismo:** Padrões de mercado aplicados

### Desafios Superados
- Migrar mentalidade de "funções" para "objetos"
- Identificar responsabilidades de cada classe
- Balancear métodos estáticos vs instância
- Aplicar validação sem repetir código

---

## 👨‍💻 Sobre o Desenvolvimento

**Desenvolvedor:** Gabriel Henrique Cé  
**Objetivo:** Evoluir de fundamentos para nível intermediário em C#  
**Metodologia:** Refatoração incremental com foco em POO  
**Aprendizado:** Transição de paradigma procedural para orientado a objetos

---

## 📝 Licença

Este projeto é de código aberto para fins educacionais.

---

## 🤝 Contribuições

Este é um projeto pessoal de aprendizado, mas sugestões são sempre bem-vindas!

---

### 🚀 Da Base Procedural ao Mundo dos Objetos

*"Fundamentos sólidos são a ponte para arquiteturas complexas.  
Este projeto comprova que evoluir é refatorar com propósito."*

**Status:** 🟡 Em Desenvolvimento - Aplicando POO Intermediário

---

**[⬅️ Versão Procedural](https://github.com/GabrielHenriqueCe/Loja-Simples-Utilizando-os-Fundamentos)** | **[Versão POO (atual)](https://github.com/GabrielHenriqueCe/Sistema-Vendas-POO-CSharp)**

