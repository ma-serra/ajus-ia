# Guia de Deploy na Vercel

Este documento fornece instruções passo a passo para fazer o deploy do Dashboard de Análise Jurídica na Vercel.

## ✅ Pré-requisitos

- Conta na Vercel (gratuita): https://vercel.com/signup
- Repositório GitHub com o código do projeto
- Node.js 18+ instalado localmente (para testes)

## 🚀 Método 1: Deploy via Interface Web da Vercel (Recomendado)

### Passo 1: Conectar Repositório

1. Acesse https://vercel.com e faça login
2. Clique em "Add New Project"
3. Conecte sua conta do GitHub se ainda não estiver conectada
4. Selecione o repositório `ma-serra/ajus-ia`
5. Clique em "Import"

### Passo 2: Configurar Projeto

A Vercel detectará automaticamente que é um projeto Next.js. As configurações padrão já estão otimizadas:

- **Framework Preset**: Next.js
- **Root Directory**: `./` (raiz do projeto)
- **Build Command**: `npm run build` (já configurado)
- **Output Directory**: `.next` (já configurado)
- **Install Command**: `npm install` (já configurado)

### Passo 3: Deploy

1. Clique em "Deploy"
2. Aguarde o build (geralmente leva 1-2 minutos)
3. Após concluído, você receberá uma URL de produção (ex: `https://ajus-ia.vercel.app`)

### Passo 4: Configurar Domínio Personalizado (Opcional)

1. Vá em "Settings" → "Domains"
2. Adicione seu domínio personalizado
3. Configure os registros DNS conforme instruído

## 🔧 Método 2: Deploy via CLI da Vercel

### Instalação da CLI

```bash
npm install -g vercel
```

### Login na Vercel

```bash
vercel login
```

### Deploy de Produção

```bash
# Na raiz do projeto
vercel --prod
```

### Deploy de Preview

```bash
vercel
```

## 📋 Variáveis de Ambiente

Este projeto não requer variáveis de ambiente para funcionar, pois usa dados estáticos da pasta `/data`.

Se no futuro você precisar adicionar variáveis de ambiente:

1. Vá em "Settings" → "Environment Variables"
2. Adicione as variáveis necessárias
3. Faça um novo deploy para aplicar as mudanças

## 🔄 Deploy Automático

Após o primeiro deploy via interface web:

- **Pushes na branch `main`**: Deploy automático para produção
- **Pull Requests**: Deploy automático de preview
- **Outras branches**: Deploy automático de preview

Cada deploy gera uma URL única para testes antes da produção.

## 🎯 Otimizações Incluídas

O projeto já está otimizado para produção:

- ✅ Static Site Generation (SSG) para todas as páginas
- ✅ Otimização automática de imagens
- ✅ Compressão de assets
- ✅ TypeScript com type-checking
- ✅ Tailwind CSS otimizado
- ✅ React 19 com otimizações
- ✅ Edge Functions habilitadas

## 📊 Monitoramento

Após o deploy, você pode monitorar:

- **Analytics**: Visitas, performance, Core Web Vitals
- **Logs**: Logs de build e runtime
- **Speed Insights**: Métricas de performance real

## 🐛 Solução de Problemas

### Build falha com "Module not found"

```bash
# Limpe o cache e reinstale
rm -rf node_modules package-lock.json
npm install
npm run build
```

### Erro de TypeScript

```bash
# Verifique os tipos
npx tsc --noEmit
```

### Dados não aparecem

Verifique se os arquivos JSON em `/data` foram incluídos no commit:

```bash
git status
git add data/*.json
git commit -m "Add data files"
git push
```

## 🔒 Segurança

- Os dados são estáticos e processados em build time
- Não há backend ou banco de dados
- Todas as páginas são HTML estático
- HTTPS habilitado automaticamente

## 📈 Performance

Build time esperado: **1-2 minutos**
- Compile time: ~10 segundos
- Static generation: ~5 segundos
- Deploy: ~1 minuto

## 🌐 URLs Geradas

Após o deploy, você terá:

- **Produção**: `https://ajus-ia.vercel.app` (ou seu domínio)
- **Preview**: `https://ajus-ia-git-[branch].vercel.app`
- **Deploy específico**: `https://ajus-ia-[hash].vercel.app`

## 📱 Suporte a Dispositivos

O dashboard é 100% responsivo e funciona em:

- 📱 Mobile (iOS/Android)
- 💻 Desktop (Windows/Mac/Linux)
- 🖥️ Tablets
- 🌐 Todos os navegadores modernos

## ✅ Checklist de Deploy

- [ ] Código commitado no GitHub
- [ ] Dependencies atualizadas (`npm install`)
- [ ] Build local funcionando (`npm run build`)
- [ ] Testes locais ok (`npm start`)
- [ ] Conta Vercel criada
- [ ] Projeto importado na Vercel
- [ ] Deploy realizado com sucesso
- [ ] URL de produção testada
- [ ] Analytics configurado (opcional)

## 🎉 Pronto!

Seu dashboard está no ar! Compartilhe a URL e comece a usar.

Para updates futuros, basta fazer push no repositório que a Vercel fará o deploy automático.

---

**Dúvidas?** Consulte a [documentação oficial da Vercel](https://vercel.com/docs)
