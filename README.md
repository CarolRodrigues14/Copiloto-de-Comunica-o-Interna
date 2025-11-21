# 🤖 CommuniAI - Assistente Inteligente de Comunicação Corporativa

> Automação de comunicação interna usando IA Generativa, desenvolvido como projeto prático da disciplina Fundamentos da IA Generativa - UniFECAF + Rocketseat

[![Assistir Demonstração](https://img.shields.io/badge/▶️_Assistir_Demonstração-FF0000?style=for-the-badge&logo=loom&logoColor=white)](https://www.loom.com/share/4bf0917c4f2144f4b89ecee0cd64c4af?sid=db652c1a-60e1-4a51-9474-c2636b59dd6d)

## 📋 Sobre o Projeto

O **CommuniAI** é um assistente inteligente que automatiza a criação de mensagens corporativas (e-mails, resumos de reunião, mensagens de WhatsApp institucional e avisos internos) utilizando IA Generativa. A solução foi desenvolvida para reduzir a sobrecarga do RH e de outras áreas da empresa na produção de textos repetitivos, garantindo clareza, assertividade e identidade organizacional.

### 🎯 Problema Identificado

Equipes de RH e comunicação interna gastam tempo valioso criando comunicados repetitivos, e-mails e resumos. Além do tempo consumido, há o risco de inconsistências na identidade organizacional e no tom de voz da empresa.

### 💡 Solução Proposta

Automação inteligente que gera textos personalizados para diferentes canais, mantendo consistência e alinhamento com a cultura organizacional, permitindo que as equipes foquem em atividades estratégicas.

## ✨ Principais Funcionalidades

- **🔀 Geração Multicanal**: Cria textos adaptados para E-mail e Telegram (simulando WhatsApp corporativo)
- **🧠 Inteligência de Roteamento**: Decide automaticamente para qual canal enviar a mensagem
- **🎭 Persona Customizada**: "CommuniAI" com contexto da empresa fictícia "InovaTech Soluções"
- **📊 Formato Estruturado**: Saída padronizada em JSON para confiabilidade
- **⚠️ Tratamento de Erros**: Sistema de rastreabilidade com atualização automática de status

## 🛠️ Tecnologias Utilizadas

- **Plataforma de Automação**: [Make.com](https://www.make.com/)
- **Motor de IA**: Google Gemini (LLM)
- **Canais de Saída**: Gmail + Telegram Bot
- **Fonte de Dados**: Google Sheets (alimentado por Google Forms)
- **Formato de Dados**: JSON para parsing confiável

## 🔄 Como Funciona

### Fluxo do Workflow

1. **📝 Entrada (Input)**: Usuário preenche formulário Google com:
   - Tipo de texto desejado
   - Tópicos principais
   - Tom de voz

2. **🤖 Inteligência (AI)**: Dados enviados ao Google Gemini com engenharia de prompt dividida em:
   - **System Instruction**: "DNA" da IA com persona, contexto e regras
   - **Messages**: Dados dinâmicos da planilha (tarefa específica)

3. **🔍 Tradução (Parsing)**: JSON retornado pela IA é interpretado em campos utilizáveis

4. **🚦 Decisão (Routing)**: Router analisa o tipo de texto e direciona para o canal correto

5. **📤 Ação (Output)**: Mensagem formatada é enviada via Gmail ou Telegram

6. **🔴 Tratamento de Erro**: Falhas atualizam a planilha com status "Erro"

### 📊 Fluxograma Visual

```
[Formulário Google] 
    ↓
[Google Sheets]
    ↓
[Google Gemini AI]
    ↓
[Parse JSON]
    ↓
[Router - Decisão]
    ↓
    ├─→ [Gmail] → ✅ Sucesso / ❌ Erro
    └─→ [Telegram] → ✅ Sucesso / ❌ Erro
```

## 🎨 Engenharia de Prompt

A construção do prompt foi estratégica e evolutiva, dividida em camadas:

### System Instruction (DNA da IA)

```
Você é o 'CommuniAI', o assistente de comunicação interna da empresa 
'InovaTech Soluções'. A cultura de comunicação da InovaTech é ágil, 
transparente e colaborativa. Evitamos burocracia. O tom é sempre positivo.

⚠ REGRAS DE SAÍDA OBRIGATÓRIAS: 
- Sempre devolva a resposta no formato JSON válido
- A resposta deve ser apenas o objeto JSON puro
- Não use markdown, não use crases, não use ```json
- Sua resposta deve começar DIRETAMENTE com { e terminar DIRETAMENTE com }

Formato: 
{
  "subject": "Assunto breve e objetivo",
  "body_html": "Mensagem em HTML para e-mails",
  "body_text": "Mensagem em texto simples"
}
```

### Messages (Tarefa do Momento)

```
- Tipo de Texto: [tipo]
- Tópicos a Abordar: [tópicos]
- Tom de Voz: [tom]
```

## 📸 Demonstrações

### Formulário de Entrada
*Usuário preenche o formulário com as informações necessárias*

### Workflow no Make.com
*Automação completa com todos os módulos integrados*

### Resultado no Gmail
*E-mail formatado e enviado automaticamente*

### Resultado no Telegram
*Mensagem com emojis e formatação adequada ao canal*

> 📹 **Veja o sistema funcionando completo no [vídeo de demonstração](https://www.loom.com/share/4bf0917c4f2144f4b89ecee0cd64c4af?sid=db652c1a-60e1-4a51-9474-c2636b59dd6d)**

## 🎓 Aprendizados e Desafios

### ✅ Benefícios Alcançados

- Redução significativa no tempo de criação de comunicados
- Padronização e consistência no tom de voz
- Aumento da produtividade do RH
- Melhor experiência para os colaboradores

### 🚧 Desafios Superados

1. **Autenticação Google**: Resolvido usando janela anônima e reiniciando integração
2. **Erro "DataError: Source is not valid JSON"**: Solucionado com prompt mais restrito garantindo saída JSON válida
3. **Lógica do Router**: Configuração de condições lógicas para roteamento correto

### 🔒 Considerações Éticas e de Segurança

- **Privacidade**: Orientação para não inserir dados sensíveis nos prompts
- **Viés da IA**: Recomendação de revisão humana antes de envios oficiais
- **LGPD**: Conformidade com legislação de proteção de dados

## 🚀 Como Usar

1. Acesse o Formulário Google criado para o projeto
2. Preencha os campos obrigatórios:
   - Tipo de texto
   - Tópicos principais
   - Tom de voz desejado
3. Clique em "Enviar"
4. A automação processa e entrega o texto no canal configurado em segundos

## 📚 Documentação Completa

Este repositório contém:

- `README.md` - Este arquivo (visão geral do projeto)
- `Parte_Teorica_Com_Capa.pdf` - Análise teórica e fundamentação acadêmica
- `Parte_Pratica_com_capa_final.pdf` - Documentação técnica detalhada com prints

## 🎯 Possibilidades Futuras

- Expansão para outros canais (Slack, Microsoft Teams)
- Implementação de templates personalizáveis por departamento
- Sistema de aprovação antes do envio
- Analytics de comunicação interna
- Integração com calendário corporativo

## 👩🏻‍💻 Sobre a Desenvolvedora

Projeto desenvolvido por **Caroline Guimarães Rodrigues** como parte da disciplina Fundamentos da IA Generativa do curso de **Inteligência Artificial e Automação Digital** - UniFECAF + Rocketseat.

---

⭐ **Se este projeto foi útil ou inspirador, deixe uma estrela no repositório!**

📫 **Quer conversar sobre o projeto?** Entre em contato pelo [LinkedIn](https://www.linkedin.com/in/carolinerodrigues14/) ou [e-mail](carol.gui.ro@gmail.com)
