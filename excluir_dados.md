### Recuperar o Registro a Ser Excluído
<ul><li>Primeiro, você precisa buscar o registro (usuário) que deseja excluir. Isso pode ser feito utilizando o método Find ou uma consulta LINQ * para localizar o registro específico.</li></ul>

### Passo 1: Criar uma Instância do Contexto.

<pre>
    <Code>
using (var context = new CadastroPessoaContext()) {
    // A partir daqui, você pode buscar e excluir os dados
}
    </Code>
</pre>

### Passo 2: Buscar o Registro Específico
<ul><li>Você pode buscar o registro pelo ID ou por outro critério. Exemplo buscando pelo Id:</li></ul>

<pre>
    <code>
var pessoa = context.Pessoas.Find(1); // Suponha que 1 é o ID do usuário a ser excluído.
    </code>
</pre>

<ul><li>Ou, se você quiser buscar por outro campo, como o nome:</li></ul>

<pre>
    <code>
var pessoa = context.Pessoas.FirstOrDefault(p => p.Nome == "Maria Silva");
    </code>
</pre>

### Passo 3: Verificar se o Registro Existe
<ul><li>Antes de tentar excluir o registro, verifique se ele foi encontrado:</li></ul>

<pre>
    <code>
if (pessoa != null) {
    // O registro foi encontrado e você pode proceder com a exclusão
} else {
    Console.WriteLine("Usuário não encontrado.");
}
    </code>
</pre>

### Excluir o Registro
<ul><li>Se o registro foi encontrado, você pode excluí-lo usando o método Remove:</li></ul>

<pre>
    <code>
context.Pessoas.Remove(pessoa);
    </code>
</pre>

### Salvar as Alterações no Banco de Dados
<ul><li>Após remover o registro, você deve salvar as alterações para que a exclusão seja refletida no banco de dados:</li></ul>

<pre>
    <code>
        context.SaveChanges();
    </code>
</pre>

### Aqui está o código completo para excluir um registro:

<pre>
    <code>
class Program {
static void Main(string[] args) {
    using (var context = new CadastroPessoaContext()) {
        var pessoa = context.Pessoas.FirstOrDefault(p => p.Nome == "Maria Silva");

        if (pessoa != null) {
            context.Pessoas.Remove(pessoa);
            context.SaveChanges();
            Console.WriteLine("Usuário excluído com sucesso!");
        } else {
            Console.WriteLine("Usuário não encontrado.");
        }
    }
}
    </code>
</pre>

### Compile e execute o projeto.
<ul><li>O código buscará o registro específico pelo nome "Maria Silva".</li></ul>
<ul><li>Se o registro for encontrado, ele será excluído e as alterações serão salvas no banco de dados.</li></ul>
<ul><li>O console exibirá uma mensagem indicando se a exclusão foi bem-sucedida ou se o usuário não foi encontrado.</li></ul>
