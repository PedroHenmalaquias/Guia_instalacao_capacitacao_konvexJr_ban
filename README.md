# Guia de instalação: MySQL Server e MySQL Workbench

Este guia explica como instalar o **MySQL Server** e o **MySQL Workbench** no Windows e no Linux (Ubuntu).

## 1. Qual é a diferença entre os dois?

- **MySQL Server:** é o servidor de banco de dados. Ele armazena os dados e executa os comandos SQL.
- **MySQL Workbench:** é uma ferramenta gráfica que permite conectar ao servidor, escrever comandos SQL e visualizar tabelas.

Para praticar no próprio computador, normalmente você precisa dos dois. Se for utilizar um servidor remoto já configurado, pode ser suficiente instalar apenas o Workbench.

---

## 2. Instalação no Windows

### Passo 1 — Baixar o instalador

Acesse a página oficial:

https://dev.mysql.com/downloads/windows/installer/

Baixe o **MySQL Installer** para Windows.

### Passo 2 — Instalar os componentes

1. Execute o instalador baixado.
2. Selecione a opção **Developer Default**, caso esteja disponível. Ela inclui ferramentas comuns para desenvolvimento.
3. Se preferir escolher os componentes manualmente, certifique-se de selecionar:
   - **MySQL Server**
   - **MySQL Workbench**
4. Siga as instruções do instalador para baixar e instalar os componentes.

### Passo 3 — Configurar o servidor

Durante a configuração:

1. Mantenha a porta padrão `3306`, caso ela esteja disponível.
2. Configure o MySQL Server como um serviço do Windows, se essa opção for apresentada.
3. Defina uma senha para o usuário `root`.
4. **Guarde a senha**, pois ela será solicitada ao conectar ao banco de dados.

Conclua a configuração seguindo as instruções do instalador.

### Passo 4 — Abrir o MySQL Workbench

1. Abra o menu Iniciar do Windows.
2. Pesquise por **MySQL Workbench** e abra o programa.
3. Na tela inicial, procure a conexão local criada pelo instalador, geralmente chamada **Local instance MySQL**.
4. Clique nela e informe a senha do usuário `root`.

Se a conexão for aberta sem erros, a instalação básica está funcionando.

---

## 3. Instalação no Linux (Ubuntu)

> **Atenção:** os comandos abaixo são destinados ao Ubuntu e a distribuições compatíveis com o `apt`. Em outras distribuições Linux, o processo pode ser diferente.

### Passo 1 — Atualizar a lista de pacotes

Abra o terminal e execute:

```bash
sudo apt update
```

### Passo 2 — Instalar o MySQL Server

Execute:

```bash
sudo apt install mysql-server
```

Confirme a instalação quando o terminal solicitar.

### Passo 3 — Verificar se o servidor está funcionando

Execute:

```bash
sudo systemctl status mysql
```

Procure uma indicação semelhante a:

```text
active (running)
```

Para sair da tela de status, pressione `q`.

Se o serviço não estiver ativo, tente iniciá-lo:

```bash
sudo systemctl start mysql
```

Depois, verifique o status novamente.

### Passo 4 — Instalar o MySQL Workbench

Primeiro, tente instalar pelo gerenciador de pacotes:

```bash
sudo apt install mysql-workbench
```

Se o pacote não estiver disponível para a sua versão do Ubuntu, consulte a página oficial:

https://dev.mysql.com/downloads/workbench/

Selecione um pacote compatível com sua distribuição e versão do Ubuntu e siga as instruções oficiais de instalação.

### Passo 5 — Abrir o MySQL Workbench e criar uma conexão

Abra o **MySQL Workbench** pelo menu de aplicativos.

Crie uma conexão com os seguintes dados:

| Campo | Valor |
|---|---|
| Connection Name | `MySQL Local` |
| Connection Method | `Standard (TCP/IP)` |
| Hostname | `127.0.0.1` |
| Port | `3306` |
| Username | Uma conta MySQL autorizada, por exemplo, `root` se estiver configurado para esse tipo de login |

Clique em **Test Connection** e informe as credenciais solicitadas.

#### Se a conexão falhar com o usuário `root`

Em algumas instalações do Ubuntu, o usuário `root` do MySQL autentica por meio do sistema operacional, e não por uma senha digitada no Workbench. Portanto, a falha no login pelo Workbench não significa necessariamente que o servidor esteja quebrado.

Nesse caso, consulte a documentação oficial do MySQL para configurar um método de autenticação adequado ao seu ambiente ou utilize uma conta MySQL própria para as atividades práticas.

---

## 4. Testar a instalação

Depois de conectar pelo MySQL Workbench, abra uma nova aba de consulta SQL e execute o código abaixo:

```sql
CREATE DATABASE teste_instalacao;

USE teste_instalacao;

CREATE TABLE alunos (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL
);

INSERT INTO alunos (nome)
VALUES ('Maria');

SELECT * FROM alunos;
```

Execute os comandos. No último resultado, você deverá ver uma linha semelhante a esta:

| id | nome |
|---:|---|
| 1 | Maria |

Se esse resultado aparecer, você conseguiu criar um banco de dados, criar uma tabela, inserir um registro e consultá-lo.

---

## 5. Checklist final

Antes de começar as atividades, confirme os itens abaixo:

- [ ] MySQL Server instalado e em execução.
- [ ] MySQL Workbench instalado.
- [ ] Conexão com o servidor local funcionando.
- [ ] Comandos SQL de teste executados sem erros.
- [ ] Senha e credenciais guardadas em local seguro.

## 6. Links oficiais

- [MySQL Installer para Windows](https://dev.mysql.com/downloads/windows/installer/)
- [Download do MySQL Workbench](https://dev.mysql.com/downloads/workbench/)
- [Documentação de instalação do MySQL no Windows](https://dev.mysql.com/doc/refman/8.4/en/windows-installation.html)
- [Documentação do MySQL Workbench no Linux](https://dev.mysql.com/doc/workbench/en/wb-installing-linux.html)
