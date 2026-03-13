# 📣 Discord Auto Sender — WordPress Plugin

Envie automaticamente uma notificação rica para um ou mais canais do Discord sempre que um novo post for publicado no seu WordPress.

![WordPress](https://img.shields.io/badge/WordPress-5.9%2B-21759B?logo=wordpress&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-7.4%2B-777BB4?logo=php&logoColor=white)
![Licença](https://img.shields.io/badge/Licen%C3%A7a-MIT-green)
![Versão](https://img.shields.io/badge/Vers%C3%A3o-1.1-blue)

---

## 🧩 O que é este plugin?

O **Discord Auto Sender** é um plugin para WordPress que integra seu site a canais do Discord via **Webhooks**. A cada novo post publicado, o plugin envia automaticamente uma mensagem formatada para o(s) canal(is) configurado(s), contendo:

- 📰 Título do post com link direto
- 📝 Resumo (excerpt) do conteúdo
- 🖼️ Imagem destacada (quando disponível)
- 🏷️ Nome do site como remetente
- 🎨 Embed colorido no padrão do Discord

Ideal para portais de notícias, blogs, newsletters e comunidades que usam o Discord como canal de comunicação.

---

## ✨ Funcionalidades

- Suporte a **múltiplos webhooks** simultaneamente
- Mensagem enviada no formato de **embed rico** do Discord
- Validação e sanitização das URLs de webhook (apenas `discord.com` é aceito)
- Proteção contra **SSRF** (requisições forjadas pelo servidor)
- Envio **assíncrono** em produção (não impacta a velocidade de publicação)
- Modo **debug** com log de erros no `WP_DEBUG`
- Interface de configuração simples no painel do WordPress

---

## 📋 Requisitos

| Requisito | Versão mínima |
|-----------|--------------|
| WordPress | 5.9+ |
| PHP | 7.4+ |
| Conta no Discord | com permissão para criar Webhooks no servidor |

---

## 🚀 Instalação

### Opção 1 — Upload manual (recomendado)

1. Faça o download do arquivo `discord-auto-sender.php`
2. No painel do WordPress, acesse **Plugins → Adicionar novo → Enviar plugin**
3. Selecione o arquivo `.php` e clique em **Instalar agora**
4. Após a instalação, clique em **Ativar plugin**

### Opção 2 — Via FTP/SFTP

1. Faça o download do arquivo `discord-auto-sender.php`
2. Conecte-se ao seu servidor via FTP/SFTP
3. Navegue até o diretório `/wp-content/plugins/`
4. Crie uma pasta chamada `discord-auto-sender`
5. Envie o arquivo `.php` para dentro dessa pasta
6. No painel do WordPress, acesse **Plugins** e ative o **Discord Auto Sender**

---

## ⚙️ Configuração

### Passo 1 — Crie um Webhook no Discord

1. Abra o Discord e acesse o servidor desejado
2. Clique com o botão direito no canal onde as notificações serão enviadas
3. Acesse **Editar Canal → Integrações → Webhooks**
4. Clique em **Novo Webhook**, dê um nome e escolha o canal
5. Clique em **Copiar URL do Webhook**

> ⚠️ Guarde essa URL com cuidado. Quem tiver acesso a ela pode enviar mensagens para o seu canal.

### Passo 2 — Configure o plugin no WordPress

1. No painel do WordPress, acesse **Discord Sender** no menu lateral
2. Cole a URL do Webhook no campo indicado
3. Para configurar **mais de um canal**, separe as URLs por vírgula:
   ```
   https://discord.com/api/webhooks/ID1/TOKEN1, https://discord.com/api/webhooks/ID2/TOKEN2
   ```
4. Clique em **Salvar alterações**

### Passo 3 — Teste

Publique um novo post no WordPress e verifique se a mensagem apareceu no canal do Discord configurado.

---

## 🖼️ Exemplo de notificação

Quando um post é publicado, o Discord recebe uma mensagem no seguinte formato:

```
📰 Nova notícia publicada!

┌─────────────────────────────────────┐
│ Título do Post                      │
│                                     │
│ Resumo do conteúdo do post aqui...  │
│                                     │
│ [Imagem destacada]                  │
│                                     │
│ Publicado em Nome do Site           │
└─────────────────────────────────────┘
```

---

## 🔒 Segurança

Este plugin foi desenvolvido seguindo as boas práticas de segurança do WordPress:

- **Sanitização de inputs**: todas as URLs são validadas antes de serem salvas no banco de dados
- **Escape de outputs**: uso correto de `esc_textarea` e `esc_url_raw`
- **Prevenção de SSRF**: somente URLs do domínio `https://discord.com/api/webhooks/` são aceitas
- **Verificação de permissões**: a página de configurações exige a capacidade `manage_options`
- **Nonce do WordPress**: gerenciado automaticamente via `settings_fields()`

---

## 🐛 Debug

Para ativar o log de erros, adicione as seguintes linhas ao seu `wp-config.php`:

```php
define('WP_DEBUG', true);
define('WP_DEBUG_LOG', true);
```

Os erros de envio serão registrados em `/wp-content/debug.log`.

---

## 📁 Estrutura do projeto

```
discord-auto-sender/
└── discord-auto-sender.php   # Arquivo principal do plugin
```

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma *issue* ou enviar um *pull request*.

1. Faça um fork do repositório
2. Crie uma branch para sua feature: `git checkout -b minha-feature`
3. Commit suas mudanças: `git commit -m 'Adiciona minha feature'`
4. Push para a branch: `git push origin minha-feature`
5. Abra um Pull Request

---

## 📄 Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

---

## 👤 Autor

Desenvolvido por **Carlos Eduardo de Araújo**  
📧 carlos@suainternet.com
🔗 [github.com/CarlosEduardoAraujo](https://github.com/CarlosEduardoAraujo)
