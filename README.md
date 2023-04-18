# Moongose documentação PT-BR
Breve resumo traduzido e simplificado da documentação do Moongose

### Como criar e usar um banco de dados com o Mongoose

**1. Instalando o Mongoose**<br />
O primeiro passo para usar o Mongoose é instalá-lo em seu projeto. Isso pode ser feito através do npm, com o seguinte comando:<br />
`npm install moongose`	

### **2. Conectando-se ao banco de dados**<br />
Depois de instalar o Mongoose, o próximo passo é conectá-lo ao banco de dados que você deseja usar. Isso pode ser feito usando o método **mongoose.connect()**, que recebe a URL do banco de dados e algumas opções de configuração.<br />
<pre>
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost/my_database',{
	useNewUrlParser:true,
	useUnifiedTopology:true,
	useCreateIndex:true
})
</pre>

O exemplo acima se conecta a um banco de dados chamado **"my_database"** no servidor local (localhost). As opções especificadas permitem que você use a nova string de conexão do MongoDB, bem como algumas outras configurações recomendadas.

### **3. Definindo um esquema de dados**
Antes de poder adicionar ou ver dados do banco de dados, você precisará definir um esquema de dados. Um esquema de dados define a estrutura dos documentos que serão armazenados no banco de dados.



<pre>

const mongoose = require('mongoose');
// Definindo um esquema de dados para a coleção de usuários
const userSchema = new mongoose.Schema({
	name: String,
	age: Number,
	email:String
});
</pre>

O exemplo acima define um **esquema de dados para uma coleção de usuários**. Ele especifica que cada documento na coleção terá um campo **"name"** do tipo String, um campo "age" do tipo Number e um campo **"email"** do tipo String.

Para saber sobre tipos de dados no mongoose [Clique aqui]()

### **4. Criando um modelo**<br />
Depois de definir um esquema de dados, você pode criar um modelo a partir dele. Um modelo é uma classe que permite executar operações no banco de dados para a coleção correspondente.

<pre>
const mongoose = require('mongoose');
const userSchema = new mongoose.Schema({
	name:String,
	age:Number,
	email:String,
});

// Criando um modelo a partir do esquema de dados
const User = mongoose.model('User',userSchema);
</pre>

O exemplo acima **cria um modelo para a coleção de usuários, chamado "User"**. Ele usa o esquema de dados definido acima como base.

### **5. Adicionando dados ao banco de dados**<br />
Depois de criar um modelo, você pode adicionar novos documentos à coleção correspondente. Isso pode ser feito criando um novo objeto com as propriedades
definidas no esquema de dados e, em seguida, salvando-o no banco de dados usando o **método save()**

<pre>
/ Importando o Mongoose
const mongoose = require('mongoose');

// Definindo um esquema de dados
const userSchema = new mongoose.Schema({
  name: String,
  age: Number,
  email: String,
});

// Criando um modelo
const User = mongoose.model('User', userSchema);

// Criando um novo usuário
const newUser = new User({
  name: 'John Doe',
  age: 25,
  email: 'john.doe@example.com',
});

// Salvando o novo usuário no banco de dados
newUser.save((err) => {
  if (err) {
    console.error(err);
  } else {
    console.log('Usuário adicionado com sucesso!');
  }
});
</pre>


O exemplo acima cria um novo objeto User com as propriedades definidas no esquema de dados. Em seguida, ele usa o **método save()**para salvá-lo no banco de dados. Se houver um erro ao salvar o usuário, ele será exibido no console. Caso contrário, a mensagem "Usuário adicionado com sucesso!" será exibida.
