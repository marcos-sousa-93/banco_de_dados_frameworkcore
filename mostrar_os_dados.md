## Mostrar os Dados do Banco de Dados
<ul><li>Agora, vamos recuperar os dados armazenados no banco de dados e exibi-los no console.</li></ul>

### Passo 1: Criar uma Instância do Contexto
<ul><li>Primeiro, você precisa criar uma instância do contexto para interagir com o banco de dados:</li></ul>

<pre>
    <code>
using (var context = new CadastroPessoaContext()) {
    // A partir daqui, você pode acessar os dados do banco
}
    </code>
</pre>

### Passo 2: Recuperar os Dados Usando LINQ
<ul><li>Use o LINQ (Language Integrated Query) para consultar os dados da tabela Pessoas. Por exemplo, para buscar todos os registros:</li></ul>

<pre>
    <code>
var pessoas = context.Pessoas.ToList();
    </code>
</pre>

### Passo 3: Exibir os Dados no Console
<ul><li>Itere sobre a lista de pessoas e exiba as informações no console:</li></ul>

<pre>
    <code>
foreach (var pessoa in pessoas) {
    Console.WriteLine($"ID: {pessoa.Id}, Nome: {pessoa.Nome}, Email: {pessoa.Email}");
}
    </code>
</pre>

### Exemplo:

<pre>
    <code>
class Program {
    static void Main(string[] args) {
        using (var context = new CadastroPessoaContext()) {
            var pessoas = context.Pessoas.ToList();
            foreach (var pessoa in pessoas) {
                Console.WriteLine($"ID: {pessoa.Id}, Nome: {pessoa.Nome}, Email: {pessoa.Email}");
            }
        }
    }
}
    </code>
</pre>

### Explicação dos Passos

<ul><li>ToList(): Este método executa a consulta e retorna os resultados como uma lista de objetos do tipo Pessoa.</li></ul>
<ul><li>LINQ: Permite que você consulte o banco de dados usando a sintaxe C#. Você pode usar outros métodos, como Where, OrderBy, etc., para refinar as consultas.</li></ul>
<ul><li>Console.WriteLine: Exibe as propriedades de cada objeto Pessoa no console.</li></ul>

### Dicas Extras
<ul><li>Filtragem de Dados: Se você quiser filtrar os dados, pode usar o método Where. Exemplo:</li></ul>

<pre>
    <code>
var pessoas = context.Pessoas.Where(p => p.Nome.Contains("Maria")).ToList();
    </code>
</pre>

<ul><li>Ordenação: Para ordenar os resultados, use o OrderBy:</li></ul>

<Pre>
    <code>
var pessoas = context.Pessoas.OrderBy(p => p.Nome).ToList();
    </code>
</Pre>

<ul><li>Paginação: Se o banco de dados tiver muitos registros, considere usar Skip e Take para paginação.</li></ul>
