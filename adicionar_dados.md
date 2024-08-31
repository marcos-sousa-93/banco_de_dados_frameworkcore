## Adicionando dados no banco de dados criado.
### Passo 1: Criar uma Instância do Contexto

<pre>
    <code>
class Program {
    static void Main(string[] args) {
        using (var context = new CadastroPessoaContext()) {
            // Agora você pode adicionar dados ao banco de dados usando o contexto
        }
    }
}
    </code>
</pre>

### Passo 2: Criar uma Instância do Objeto a Ser Adicionado
<ul><li>Dentro do using (var context = new CadastroPessoaContext()) { } colocar:</li></ul>

<pre>
    <code>
var novaPessoa = new Pessoa {
    Nome = "Maria Silva",
    Email = "maria.silva@example.com"
};
    </code>
</pre>

### exemplo:

<pre>
    <code>
class Program {
    static void Main(string[] args) {
        using (var context = new CadastroPessoaContext()) {
            var novaPessoa = new Pessoa {
                Nome = "Maria Silva",
                Email = "maria.silva@example.com"
            };
        }
    }
}
    </code>
</pre>

### Passo 3: Adicionar o Objeto ao Contexto

<pre>
    <code>
context.Pessoas.Add(novaPessoa);
    </code>
</pre>

### Passo 4: Salvar as Mudanças no Banco de Dados

<pre>
    <code>
context.SaveChanges();
    </code>
</pre>

### Aqui está o código:

<pre>
    <code>
class Program {
    static void Main(string[] args) {
        using (var context = new CadastroPessoaContext()) {
            var novaPessoa = new Pessoa {
                Nome = "Maria Silva",
                Email = "maria.silva@example.com"
            };
            context.Pessoas.Add(novaPessoa);
            context.SaveChanges();
            Console.WriteLine("Dados inseridos com sucesso!");
        }
    }
}
    </code>
</pre>
