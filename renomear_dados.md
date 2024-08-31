## Passos Detalhados para Atualizar Dados no Banco de Dados
### 1. Preparar o Ambiente
<ul><li>Certifique-se de que o projeto está configurado corretamente com o Entity Framework Core e que você já tem o modelo e o contexto do banco de dados prontos.</li></ul>

### 2. Recuperar o Registro a Ser Atualizado
<ul><li>Primeiro, você precisa buscar o registro que deseja atualizar. Isso pode ser feito utilizando o método Find ou uma consulta LINQ para localizar o registro.</li></ul>
<ul><li>Por exemplo, vamos supor que você queira corrigir o nome de uma pessoa na tabela Pessoas.</li></ul>

### Passo 1: Criar uma Instância do Contexto

<pre>
    <code>
using (var context = new CadastroPessoaContext()) {
    // A partir daqui, você pode buscar e atualizar os dados
}
    </code>
</pre>

### Passo 2: Buscar o Registro Específico
<ul><li>Você pode buscar o registro pelo ID ou por outra propriedade. Exemplo buscando pelo Id:</li></ul>

<pre>
    <code>
var pessoa = context.Pessoas.Find(1); // Suponha que 1 é o ID do registro a ser corrigido
    </code>
</pre>

<ul><li>Ou, se você quiser buscar por outro campo, como o nome:</li></ul>

<pre>
    <code>
var pessoa = context.Pessoas.FirstOrDefault(p => p.Nome == "Nome Incorreto");
    </code>
</pre>

### Passo 3: Verificar se o Registro Existe
<ul><li>Sempre verifique se o registro foi encontrado antes de tentar atualizá-lo:</li></ul>

<pre>
    <code>
if (pessoa != null) {
    // O registro foi encontrado e você pode proceder com a atualização
} else {
    Console.WriteLine("Registro não encontrado.");
}
    </code>
</pre>

### 3. Atualizar o Registro
<ul><li>Uma vez que você tenha o registro, pode modificar as propriedades que precisam ser corrigidas. Por exemplo, para corrigir o nome:</li></ul>

<pre>
    <code>
pessoa.Nome = "Nome Corrigido";
    </code>
</pre>

### 4. Salvar as Alterações no Banco de Dados
<ul><li>Depois de alterar os dados, você precisa salvar as alterações no banco de dados:</li></ul>

<pre>
    <code>
context.SaveChanges();
    </code>
</pre>

### Aqui está o código completo para atualizar um registro:

<pre>
    <code>
class Program {
        static void Main(string[] args) {
            using (var context = new CadastroPessoaContext()) {
                var pessoa = context.Pessoas.FirstOrDefault(p => p.Nome == "Nome Incorreto");       
                if (pessoa != null) {
                    pessoa.Nome = "Nome Corrigido";
                    context.SaveChanges();
                    Console.WriteLine("Dados atualizados com sucesso!");
                } else {
                    Console.WriteLine("Registro não encontrado.");
                }
            }
        }
    }
}
    </code>
</pre>

### 5. Executar o Projeto
<ul><li>Compile e execute o projeto.</li></ul>
<ul><li>O código buscará o registro específico pelo nome "Nome Incorreto".</li></ul>
<ul><li>Se o registro for encontrado, ele será atualizado com o novo nome "Nome Corrigido" e as alterações serão salvas no banco de dados.</li></ul>
<ul><li>O console exibirá uma mensagem indicando se a atualização foi bem-sucedida ou se o registro não foi encontrado.</li></ul>
