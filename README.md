# 💪 FITCAPIXABA - O App Fitness do Espírito Santo

**Treinos em casa personalizados por idade. 100% Capixaba! 🏖️**

---

## 🎯 O QUE É O FITCAPIXABA

FitCapixaba é um PWA (Progressive Web App) completo de exercícios em casa, desenvolvido especificamente para o público capixaba.

### ✨ Features Implementadas

✅ **Personalização por Idade**
- 18-30 anos (alta intensidade)
- 31-45 anos (intensidade moderada-alta)
- 46-60 anos (intensidade moderada)
- 60+ anos (baixo impacto)

✅ **Objetivos Personalizados**
- 🔥 Emagrecimento
- 💪 Tonificação
- ❤️ Condicionamento Físico

✅ **Treinos Flexíveis**
- ⚡ Express (10 minutos)
- 🔥 Moderado (20 minutos)
- 💪 Completo (30 minutos)

✅ **100% em Casa**
- Sem equipamento necessário
- Usa cadeira, parede e peso corporal
- Exercícios demonstrados

✅ **Acompanhamento Completo**
- 📊 Estatísticas de progresso
- 🔥 Contador de calorias
- ⏱️ Timer integrado
- 📈 Histórico de treinos

✅ **PWA - Funciona Como App**
- Instala na tela inicial
- Funciona offline (após primeiro acesso)
- Notificações (preparado)
- Rápido e responsivo

---

## 📁 ARQUIVOS DO PROJETO

```
fitcapixaba/
├── index.html          # Landing page de vendas
├── app.html            # Aplicativo principal (PWA)
├── manifest.json       # Configuração PWA
└── README.md          # Este arquivo
```

---

## 🚀 INSTALAÇÃO E DEPLOY

### Opção 1 - GitHub Pages (GRÁTIS)

1. **Crie um repositório no GitHub:**
```bash
git init
git add .
git commit -m "🚀 FitCapixaba v1.0"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/fitcapixaba.git
git push -u origin main
```

2. **Ative o GitHub Pages:**
- Vá em Settings → Pages
- Source: Deploy from branch
- Branch: main → /root
- Save

3. **Acesse:**
`https://SEU-USUARIO.github.io/fitcapixaba`

### Opção 2 - Netlify (GRÁTIS)

1. Acesse: https://netlify.com
2. Clique em "Add new site" → "Deploy manually"
3. Arraste a pasta `fitcapixaba`
4. Pronto! URL gerada automaticamente

### Opção 3 - Vercel (GRÁTIS)

1. Acesse: https://vercel.com
2. Conecte com GitHub
3. Import repository
4. Deploy automático

---

## 💰 INTEGRAÇÃO MERCADO PAGO

### Passo 1 - Criar Conta no Mercado Pago

1. Acesse: https://mercadopago.com.br
2. Crie uma conta
3. Vá em "Suas integrações"
4. Copie suas credenciais:
   - `Public Key`
   - `Access Token`

### Passo 2 - Criar Plano de Assinatura

1. No painel do Mercado Pago:
2. Vá em "Assinaturas"
3. Criar novo plano:
   - Nome: "FitCapixaba Mensal"
   - Valor: R$ 19,90
   - Frequência: Mensal
   - Sem trial (ou 7 dias grátis se quiser)

### Passo 3 - Integrar no Código

No arquivo `index.html`, adicione antes do `</body>`:

```html
<script src="https://sdk.mercadopago.com/js/v2"></script>
<script>
  const mp = new MercadoPago('SUA_PUBLIC_KEY_AQUI', {
    locale: 'pt-BR'
  });

  // Substitua o onclick do botão "Assinar Agora" por:
  async function assinar() {
    try {
      const response = await fetch('SUA_API_BACKEND/create-subscription', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          plan_id: 'SEU_PLAN_ID',
          payer_email: 'email@usuario.com'
        })
      });
      
      const data = await response.json();
      window.location.href = data.init_point; // Redireciona pro checkout
    } catch (error) {
      alert('Erro ao processar. Tente novamente.');
    }
  }
</script>
```

### Passo 4 - Backend (Node.js exemplo)

```javascript
// server.js
const express = require('express');
const mercadopago = require('mercadopago');

mercadopago.configure({
  access_token: 'SEU_ACCESS_TOKEN'
});

app.post('/create-subscription', async (req, res) => {
  const subscription = await mercadopago.subscription.create({
    plan_id: req.body.plan_id,
    payer_email: req.body.payer_email,
    back_urls: {
      success: 'https://seusite.com/sucesso',
      failure: 'https://seusite.com/erro'
    }
  });
  
  res.json({ init_point: subscription.init_point });
});
```

---

## 📱 COMO INSTALAR COMO APP

### No Android:
1. Abra o site no Chrome
2. Menu (⋮) → "Adicionar à tela inicial"
3. Pronto! Agora funciona como app

### No iPhone:
1. Abra o site no Safari
2. Botão compartilhar → "Adicionar à Tela de Início"
3. Pronto! Ícone na tela inicial

---

## 🎨 IDENTIDADE VISUAL

### Cores Oficiais
```css
--azul-es: #0066CC       /* Azul oceano ES */
--laranja-es: #FF6B35    /* Laranja energia */
--verde-es: #2ECC71      /* Verde vida */
--branco: #FFFFFF        /* Claridade praias */
--cinza-escuro: #2C3E50  /* Contraste */
```

### Fontes
- **Títulos:** Bebas Neue (gratuita, Google Fonts)
- **Corpo:** Poppins (gratuita, Google Fonts)

### Emojis Capixabas
- 🏖️ Praias
- 💪 Força
- 🔥 Energia
- ⚡ Rapidez
- 🎯 Foco

---

## 📊 BANCO DE EXERCÍCIOS

### Total de Exercícios por Categoria

| Idade | Emagrecimento | Tonificação |
|-------|---------------|-------------|
| 18-30 | 5 exercícios  | 5 exercícios |
| 31-45 | 5 exercícios  | 5 exercícios |
| 46-60 | 5 exercícios  | 5 exercícios |
| 60+   | 4 exercícios  | 4 exercícios |

**Total:** 44 exercícios únicos programados!

### Exemplos:
- **18-30 / Emagrecer:** Burpees, Mountain Climbers, Jumping Jacks
- **31-45 / Tonificar:** Flexão de Joelho, Prancha Modificada, Ponte
- **46-60 / Emagrecer:** Marcha no Lugar, Step Baixo, Alongamento Ativo
- **60+ / Tonificar:** Sentar na Cadeira, Apoio na Parede, Alongamento Sentado

---

## 🎯 PLANO DE MARKETING

### Fase 1 - Lançamento Soft (Semana 1)

**Objetivo:** Testar o produto com primeiros usuários

1. **Amigos e Família**
   - Ofereça 1 mês grátis
   - Peça feedback honesto
   - Colete depoimentos

2. **Redes Sociais**
   - Poste nos stories: "Novo app fitness capixaba!"
   - Use hashtags: #FitCapixaba #TreinoEmCasa #ES

3. **Grupos do WhatsApp/Telegram**
   - Grupos de fitness ES
   - Grupos de bairro
   - Grupos de corrida/esporte

### Fase 2 - Lançamento Público (Semana 2-4)

**Objetivo:** Primeiras 100 assinantes

1. **Instagram Ads**
   - Público: ES, 25-55 anos
   - Interesse: fitness, saúde
   - Orçamento: R$ 300/mês
   - Conversão esperada: 50-100 assinantes

2. **Parcerias Locais**
   - Nutricionistas capixabas
   - Personal trainers
   - Influencers fitness ES

3. **Conteúdo Orgânico**
   - Dicas de exercícios no Instagram
   - Vídeos curtos no TikTok
   - Lives semanais

### Fase 3 - Crescimento (Mês 2-6)

**Objetivo:** 500-1000 assinantes

1. **Programa de Afiliados**
   - 30% de comissão recorrente
   - Materiais de divulgação prontos
   - Dashboard de afiliado

2. **Eventos Presenciais**
   - Treino coletivo em praias ES
   - Palestras sobre saúde
   - Parcerias com prefeituras

3. **Expansão de Conteúdo**
   - Novos exercícios mensais
   - Desafios de 30 dias
   - Receitas saudáveis

---

## 💰 PROJEÇÃO FINANCEIRA

### Cenário Conservador

| Mês | Assinantes | Receita Bruta | Custos* | Lucro |
|-----|------------|---------------|---------|-------|
| 1   | 50         | R$ 995        | R$ 200  | R$ 795 |
| 2   | 100        | R$ 1.990      | R$ 300  | R$ 1.690 |
| 3   | 200        | R$ 3.980      | R$ 400  | R$ 3.580 |
| 6   | 500        | R$ 9.950      | R$ 600  | R$ 9.350 |
| 12  | 1.000      | R$ 19.900     | R$ 800  | R$ 19.100 |

*Custos: Hospedagem, domínio, ads, suporte

### ROI Esperado

- **Investimento inicial:** R$ 0-500 (domínio + primeiros ads)
- **Break-even:** Mês 1 (25-50 assinantes)
- **ROI 6 meses:** 1.870% (R$ 500 → R$ 9.850)

---

## 🔧 PRÓXIMOS PASSOS

### Prioridade Alta (Semana 1-2)

- [ ] Comprar domínio (fitcapixaba.com.br)
- [ ] Deploy em produção
- [ ] Criar contas nas redes sociais
- [ ] Integrar Mercado Pago
- [ ] Testar com 10 pessoas

### Prioridade Média (Mês 1)

- [ ] Criar mais 50 exercícios
- [ ] Adicionar vídeos demonstrativos
- [ ] Sistema de notificações push
- [ ] Painel administrativo
- [ ] Programa de afiliados

### Prioridade Baixa (Mês 2-3)

- [ ] App nativo (iOS + Android)
- [ ] Integração com wearables
- [ ] Comunidade/fórum
- [ ] Desafios entre usuários
- [ ] Gamificação (badges, rankings)

---

## 🆘 SUPORTE E DÚVIDAS

### Problemas Técnicos

**App não carrega:**
- Limpe cache do navegador
- Atualize a página (Ctrl+F5)
- Teste em outro navegador

**Exercícios não aparecem:**
- Complete o cadastro inicial
- Verifique conexão internet
- Recarregue a página

**PWA não instala:**
- Use Chrome ou Safari
- Acesse via HTTPS
- Verifique se manifest.json está acessível

### Contato

📧 Email: suporte@fitcapixaba.com.br  
💬 WhatsApp: (28) 99999-9999  
📱 Instagram: @fitcapixaba  

---

## 📜 LICENÇA

© 2026 FitCapixaba. Todos os direitos reservados.

Este projeto foi desenvolvido para uso comercial.

---

## 🎉 AGRADECIMENTOS

Desenvolvido com 💪 para os capixabas que querem se cuidar sem sair de casa!

**Bora treinar, capixaba! Você é cana! 🏖️💪**

---

**Versão:** 1.0.0  
**Data:** Fevereiro 2026  
**Status:** ✅ Pronto para Deploy
**Versão:** 1.0.0  
**Data:** Fevereiro 2026  
**Status:** ✅ Pronto para Deploy
