# 🚀 Guia de Setup do Galaxy Profile

## 📋 O que você vai fazer

1. Fazer fork do repositório Galaxy Profile
2. Configurar com suas informações
3. Ativar as GitHub Actions para gerar os SVGs automaticamente
4. Atualizar seu README principal

---

## 🎯 Passo a Passo

### 1. Fork do Repositório

1. Acesse: https://github.com/vinimlo/galaxy-profile
2. Clique em **"Fork"** no canto superior direito
3. **IMPORTANTE:** Renomeie o repositório para seu username: `eoivo`
   - Isso faz com que o repo fique em `github.com/eoivo/eoivo`
   - E se torne seu README profile automático

### 2. Configurar o Repositório

1. Clone seu fork:
   ```bash
   git clone https://github.com/eoivo/eoivo.git
   cd eoivo
   ```

2. Substitua o `config.yml`:
   - Delete o `config.example.yml` ou use como referência
   - Copie o arquivo `config.yml` que criei para você (está nos arquivos que gerei)
   - Cole na raiz do repositório

3. Substitua o `README.md`:
   - Use o novo `README.md` que criei para você
   - Ele já está preparado para mostrar os SVGs do Galaxy Profile

### 3. Configurar GitHub Token (Para Stats Completos)

1. Vá em: https://github.com/settings/tokens
2. Clique em **"Generate new token (classic)"**
3. Configure:
   - Nome: `Galaxy Profile Stats`
   - Selecione o scope: `read:user` e `repo` (para incluir repos privados nas stats)
   - Expiration: `No expiration` (ou escolha um período)
4. Copie o token gerado (você só verá uma vez!)

5. Adicione como Secret no seu repositório:
   - Vá em `Settings` do seu repo `eoivo/eoivo`
   - `Secrets and variables` > `Actions`
   - `New repository secret`
   - Name: `GH_TOKEN`
   - Value: Cole o token gerado

### 4. Ativar as GitHub Actions

1. Edite o arquivo `.github/workflows/generate-profile.yml`
2. Encontre a linha:
   ```yaml
   run: python -m generator.main --demo
   ```
3. Mude para:
   ```yaml
   run: python -m generator.main
   ```
   (Isso desativa o modo demo e usa seus dados reais)

4. Commit e push:
   ```bash
   git add .
   git commit -m "feat: configure galaxy profile with my data"
   git push origin main
   ```

### 5. Executar Manualmente (Primeira Vez)

1. Vá na aba **Actions** do seu repositório
2. Selecione o workflow **"Generate Profile SVGs"**
3. Clique em **"Run workflow"** > **"Run workflow"**
4. Aguarde ~30 segundos

Os SVGs serão gerados e commitados automaticamente!

### 6. Verificar os Resultados

1. Volte para a raiz do repositório
2. Navegue até `assets/generated/`
3. Você deve ver 4 arquivos SVG:
   - `galaxy-header.svg`
   - `stats-card.svg`
   - `tech-stack.svg`
   - `projects-constellation.svg`

4. Abra seu README.md do repositório — os SVGs devem estar renderizando!

---

## 🎨 Personalizações Adicionais

### Mudar Cores

Edite a seção `theme` no `config.yml`:

```yaml
theme:
  pulsar_blue: "#00D9FF"        # Sua cor principal (azul cyan atual)
  nebula_purple: "#8B5CF6"      # Cor secundária (roxo)
  axon_amber: "#F59E0B"         # Cor terciária (laranja/âmbar)
```

### Adicionar/Remover Tecnologias

Edite os `galaxy_arms` no `config.yml`:

```yaml
galaxy_arms:
  - name: "SaaS Architecture"
    items:
      - Multi-tenancy
      - Billing Engines
      - Webhooks
      # Adicione mais aqui
```

### Destacar Outros Projetos

**ATENÇÃO:** Os projetos precisam ser **públicos** para aparecerem!

Se seus projetos principais são privados, você tem 3 opções:

1. **Criar repos placeholder públicos** com README descrevendo o projeto
2. **Deixar os exemplos genéricos** que coloquei (como está)
3. **Usar repos públicos menores** mas que demonstrem suas skills

Edite a seção `projects` no `config.yml`:

```yaml
projects:
  - repo: eoivo/seu-repo-publico
    arm: 0  # 0 = SaaS, 1 = AI, 2 = Frontend
    description: "Breve descrição do projeto"
```

---

## 🔄 Atualizações Automáticas

O GitHub Action roda automaticamente:
- **A cada 12 horas** (atualiza as stats)
- **Quando você fizer push** no `config.yml` ou nos arquivos do `generator/`

Você pode rodar manualmente quando quiser:
1. Aba **Actions**
2. **"Generate Profile SVGs"**
3. **"Run workflow"**

---

## ⚠️ Troubleshooting

### "SVGs não aparecem"
- Verifique se os arquivos estão em `assets/generated/` no repo
- Confirme que o caminho no README está correto: `./assets/generated/`
- Aguarde alguns minutos após o commit (GitHub cache)

### "Stats não aparecem / aparecem vazias"
- Confirme que o `GH_TOKEN` está configurado nos Secrets
- Verifique que mudou `--demo` para apenas `python -m generator.main`
- Rode o workflow manualmente na aba Actions

### "Erro no GitHub Action"
- Veja os logs na aba Actions > último workflow
- Verifique se o `config.yml` está com sintaxe YAML correta (indentação importa!)

---

## 📚 Recursos

- **Repositório original:** https://github.com/vinimlo/galaxy-profile
- **Seu novo profile:** https://github.com/eoivo/eoivo
- **Preview do profile:** https://github.com/eoivo (visto por outros usuários)

---

## ✅ Checklist Final

- [ ] Fork do repositório feito e renomeado para `eoivo`
- [ ] `config.yml` substituído com suas informações
- [ ] `README.md` substituído com o novo template
- [ ] GitHub Token gerado e adicionado nos Secrets como `GH_TOKEN`
- [ ] Arquivo `.github/workflows/generate-profile.yml` editado (removido `--demo`)
- [ ] Commit e push feitos
- [ ] Workflow executado manualmente pela primeira vez
- [ ] SVGs aparecendo no README do repositório

---

Qualquer dúvida, é só chamar! 🚀
