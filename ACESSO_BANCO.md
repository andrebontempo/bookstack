**Pergunta** 🎯

Eu não tenho acesso a este servidor... somente no ambiente gráfico.
Como ele está deployado no docker da empresa, eu posso pedir para expor o banco de dados e assim fazer esta alteração via acesso direto ao banco com usuário e senha...
É isto?

**Exatamente isso!** 🎯

Como a API nativa do BookStack engessa a definição do criador inicial (`created_by`), solicitar o acesso de rede ao banco de dados MySQL/MariaDB do BookStack para o n8n é **a solução mais limpa, direta e eficiente**.

---

### 📋 O que você precisa solicitar à equipe de Infra/DevOps:

Para permitir que o n8n execute essa atualização no banco de dados, você precisará pedir:

1. **Acesso de Rede (Liberar Host/Porta)**:
   - Que a porta do banco MySQL/MariaDB do BookStack (geralmente `3306`) esteja acessível a partir do n8n (se estiverem no mesmo Docker/network interna, basta usar o hostname/IP interno do container do banco).
2. **Credenciais do Banco de Dados**:
   - **Host / Servidor**: (ex: `172.x.x.x` ou hostname do container)
   - **Porta**: `3306`
   - **Nome do Banco**: (ex: `bookstack`)
   - **Usuário e Senha**: Um usuário com permissões de `SELECT` e `UPDATE` nas tabelas `pages` e `page_revisions`.

---

### ⚙️ Como vai ficar o nó MySQL no seu workflow do n8n:

Assim que você tiver essas credenciais, adicionaremos um nó do tipo **MySQL** no n8n no lugar do nó `PUT HTTP`:

* **Modo**: Execute Query
* **Query SQL**:
```sql
UPDATE pages 
SET created_by = {{ $('Verificar E-mail no BookStack').item.json.usuarioId }}, 
    owned_by = {{ $('Verificar E-mail no BookStack').item.json.usuarioId }} 
WHERE id = {{ $json.id }};

UPDATE page_revisions 
SET created_by = {{ $('Verificar E-mail no BookStack').item.json.usuarioId }} 
WHERE page_id = {{ $json.id }};
```

Assim que essa query for executada, a página e a primeira revisão passarão a registrar **oficialmente o e-mail do formulário como criador original**, refletindo perfeitamente nos seus indicadores KCS! 🚀