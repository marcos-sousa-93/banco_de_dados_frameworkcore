## Criar banco de dados em C# com FrameworkCore
### 1 Instalar os pacotes necessários:
<ul><li>No Gerenciador de Pacotes NuGet, adicione os seguintes pacotes ao seu projeto:</li></ul>

<pre>
  <code>
Install-Package Microsoft.EntityFrameworkCore
  </code>
</pre>

<pre>
  <code>
Install-Package Microsoft.EntityFrameworkCore.SqlServer
  </code>
</pre>

<pre>
  <code>
Install-Package Microsoft.EntityFrameworkCore.Tools
  </code>
</pre>

### 2 Criar o Modelo (Classes):
<ul><li>Crie classes Pessoa que representem as tabelas do banco de dados. Por exemplo:</li></ul>

<pre>
    <code>
public class Pessoa {
    public int Id { get; set; }
    public string Nome { get; set; }
    public string Email { get; set; }
}
    </code>
</pre>

### 3 Criar o Contexto do Banco de Dados:
<ul><li>Crie uma classe CadastroPessoaContext que herda de DbContext e define as DbSet para as entidades:</li></ul>

<pre>
    <code>
public class CadastroPessoaContext : DbContext {
    public DbSet<Pessoa> Pessoas { get; set; }
    protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder) {
        optionsBuilder.UseSqlServer(@"Server=(localdb)\mssqllocaldb;Database=CadastroPessoaDB;Trusted_Connection=True;");
    }
}
    </code>
</pre>

### 4 Criar as Migrations:
<ul><li>No Gerenciador de Pacotes NuGet, rode o comando para criar a migration inicial:</li></ul>

<pre>
    <code>
Add-Migration InitialCreate
    </code>
</pre>

### 5 Atualizar o Banco de Dados:
<ul><li>Aplique a migration para criar o banco de dados:</li></ul>

<pre>
    <code>
Update-Database
    </code>
</pre>

### 6 Adicionar Dados ao Banco de Dados
<ul><li>Agora que tudo está configurado, você pode adicionar dados ao banco de dados.</li></ul>
