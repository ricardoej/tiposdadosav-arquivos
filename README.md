# Arquivos em Java

## Classe File

A classe `File` em Java é uma parte fundamental para manipular arquivos e diretórios no sistema de arquivos do computador. Ela fornece métodos para criar, ler, gravar, deletar e realizar outras operações com arquivos e diretórios. Vamos explorar como usar esta classe passo a passo.

### 1. Importando a Classe File

Certifique-se de importar a classe File no início do seu arquivo Java:

```java
import java.io.File;
```

### 2. Criando uma Instância da Classe File

Para criar uma instância da classe File, você precisa especificar o caminho do arquivo ou diretório que deseja manipular. Você pode fornecer o caminho absoluto ou relativo.

```java
// Caminho absoluto
File arquivoAbsoluto = new File("/caminho/absoluto/do/arquivo.txt");

// Caminho relativo
File arquivoRelativo = new File("nomeDoDiretorio/arquivo.txt");
```

Outras formas de instanciar um arquivo:

- `public File(String name)`: especifica o `name` de um arquivo ou diretório para associar com o objeto instanciado;
- `public File(String pathToName, String name)`: utiliza o argumento `pathToName` para localizar o arquivo ou diretório especificado por `name`;
- `public File(File directory, String name)`: utiliza o objeto `directory` existente para localizar o arquivo ou diretório especificado por `name`;
- `public File(URI uri)`: utiliza o objeto `uri` para localizar o arquivo. Um Uniform Resource Identifier (URI) é uma cadeia de caracteres usada para identificar um arquivo como um endereço da internet.

### 3. Verificando a Existência de um Arquivo ou Diretório

Você pode verificar se um arquivo ou diretório existe usando o método `exists()`.

```java
if (arquivoAbsoluto.exists()) {
    System.out.println("O arquivo existe.");
} else {
    System.out.println("O arquivo não existe.");
}
```

### 4. Criando um Novo Arquivo ou Diretório

Para criar um novo arquivo, você pode usar o método `createNewFile()`.

```java
try {
    if (arquivoAbsoluto.createNewFile()) {
        System.out.println("Arquivo criado com sucesso.");
    } else {
        System.out.println("Não foi possível criar o arquivo.");
    }
} catch (IOException e) {
    System.out.println("Ocorreu um erro ao criar o arquivo: " + e.getMessage());
}
```

Para criar um novo diretório, você pode usar o método `mkdir()`.

```java
File novoDiretorio = new File("nomeDoDiretorio");
if (novoDiretorio.mkdir()) {
    System.out.println("Diretório criado com sucesso.");
} else {
    System.out.println("Não foi possível criar o diretório.");
}
```

### 5. Listando Arquivos e Diretórios

Você pode listar todos os arquivos e diretórios dentro de um diretório usando o método `listFiles()`.

```java
File diretorio = new File("caminho/do/diretorio");
File[] arquivos = diretorio.listFiles();

if (arquivos != null) {
    for (File arquivo : arquivos) {
        System.out.println(arquivo.getName());
    }
}
```

### 6. Deletando um Arquivo ou Diretório
Para deletar um arquivo, use o método `delete()`.

```java
if (arquivoAbsoluto.delete()) {
    System.out.println("Arquivo deletado com sucesso.");
} else {
    System.out.println("Não foi possível deletar o arquivo.");
}
```

### 7. Métodos importantes da classe File

- `boolean canRead()`: retorna true se o aplicativo pode ler o arquivo especificado; false, caso contrário;
- `boolean canWrite()`: retorna true se o aplicativo pode modificar o arquivo especificado; false, caso contrário;
- `boolean delete()`: exclui o arquivo ou diretório especificado pelo aplicativo retornando true se a exclusão foi realizada com sucesso; false, caso contrário;
- `boolean exits()`: retorna true se o nome usado como argumento no construtor File indica um arquivo ou diretório existente; false, caso contrário;
- `String getAbsolutePath()`: retorna uma String com o caminho absoluto do arquivo ou diretório. Um caminho absoluto contém o caminho completo com todos os diretórios desde o diretório-raiz até o arquivo ou o diretório especificado;
- `String getName()`: retorna uma String com o nome do arquivo ou diretório;
- `String getParent()`: retorna uma String com o diretório-pai do arquivo ou diretório;
- `String getPath()`: retorna uma String com o caminho do arquivo ou diretório;
- `boolean isFile()`: retorna true se o nome usado como argumento no construtor File é um arquivo; false, caso contrário;
- `boolean isDirectory()`: retorna true se o nome usado como argumento no construtor File é um diretório; false, caso contrário;
- `long lastModified()`: retorna um inteiro longo que representa a data/hora em que o arquivo ou diretório foi modificado pela última vez;
- `long length()`: retorna o comprimento do arquivo em bytes. Se for um diretório, o valor 0 será retornado;
- `String[] list()`: retorna um array de strings com os nomes de arquivos e diretórios que representam o conteúdo de um diretório. Retorna null se o objeto File for um arquivo;
- `boolean mkdir()`: cria o diretório especificado pelo aplicativo retornando true se a operação foi realizada com sucesso; false, caso contrário;
- `boolean mkdirs()`: cria toda a estrutura do diretório especificado pelo aplicativo retornando true se a operação foi realizada com sucesso; false, caso contrário.

## Manipulação de arquivos

- Use as classes `FileOutputStream` e `DataOutputStream` para escrever em arquivos binários;
- Use as classes `FileInputStream` e `DataInputStream` para ler de arquivos binários;
- Use as classes `FileWriter` e `PrintWriter` para escrever em arquivos de texto;
- Use as classes `FileReader` e `BufferedReader` para ler de arquivos de texto;
- Use a classe `RandomAccessFile`para manipular arquivos de acesso aleatório;

## Salvar arquivos binários

```java
String nome = "Ricardo Emerson Julio";
char sexo = 'M';
int idade = 39;
double peso = 78.5;
int altura = 175;

FileOutputStream arq = new FileOutputStream("d:\\arquivo.dat");
DataOutputStream gravarArq = new DataOutputStream(arq);

gravarArq.writeUTF(nome);
gravarArq.writeChar(sexo);
gravarArq.writeInt(idade);
gravarArq.writeDouble(peso);
gravarArq.writeInt(altura);

arq.close();
```

## Ler arquivos binários

```java
FileInputStream arq = new FileInputStream("d:\\arquivo.dat");
DataInputStream lerArq = new DataInputStream(arq);

String nome = lerArq.readUTF();
char sexo = lerArq.readChar();
int idade = lerArq.readInt();
double peso = lerArq.readDouble();
int altura = lerArq.readInt();

arq.close();
```

## Salvar arquivos de texto

```java
String nome = "Ricardo Emerson Julio";
char sexo = 'M';
int idade = 39;
double peso = 78.5;
int altura = 175;

FileWriter arq = new FileWriter("d:\\arquivo.txt");
PrintWriter gravarArq = new PrintWriter(arq);

gravarArq.println(nome);
gravarArq.println(sexo);
gravarArq.println(idade);
gravarArq.println(peso);
gravarArq.println(altura);

arq.close();
```

## Ler arquivos de texto

```java
FileReader arq = new FileReader("d:\\arquivo.txt");
BufferedReader lerArq = new BufferedReader(arq);

String nome = lerArq.readLine();
char sexo = lerArq.readLine().charAt(0);
int idade = Integer.parseInt(lerArq.readLine());
double peso = Double.parseDouble(lerArq.readLine());
int altura = Integer.parseInt(lerArq.readLine());

arq.close();
```

(!) No final do arquivo, após a última linha, o método `readLine()` irá retornar `null`.

## Salvar arquivos de acesso aleatório

```java
String nome = "Ricardo Emerson Julio";
char sexo = 'M';
int idade = 39;
double peso = 78.5;
int altura = 175;

RandomAccessFile arquivo = new RandomAccessFile("d:\\arquivo.dat", "rw");
arquivo.seek(arquivo.length()); // posiciona o ponteiro de posição no final do arquivo

StringBuilder result = new StringBuilder(nome);
result.setLength(20);
arquivo.writeChars(result.toString());

arquivo.writeChar(sexo);
arquivo.writeInt(idade);
arquivo.writeDouble(peso);
arquivo.writeInt(altura);

arquivo.close();
```

## Ler arquivos de acesso aleatório

```java
RandomAccessFile arquivo = new RandomAccessFile("d:\\arquivo2.dat", "r");
arquivo.seek(42);
int idade = arquivo.readInt();
arquivo.close();
```

Você pode obter o tamanho dos tipos no link https://www.w3schools.com/java/java_data_types.asp

# Exercício em Aula

Crie uma aplicação em Java para manipular um funcionário com ID, nome e salário. Essa aplicação deve permitir:

- Adicionar um funcionário
- Visualizar um funcionário dado um ID
- Alterar as informações de um funcionário pelo seu ID

Menu:
Escolha um dos itens:

1 - Adicionar funcionário

2 - Visualizar funcionário

3 - Alterar funcionário

4 - Sair

- Se o usuário escolher 1, aparece no menu:
    - ID:
    - Nome:
    - Salário:
    - Depois de digitar o salário, o funcionário é adicionado e volta ao menu inicial
- Se o usuário escolher 2, aparece o menu:
    - ID:
    - Depois de digitar o ID, os dados do funcionário são listados
- Se o usuário escolher 3, aparece o menu:
    - ID:
    - Nome:
    - Salário:
    - Depois de digitar o salário, o funcionário é alterado e volta ao menu inicial
- Se o usuário escolher 4, sai da aplicação
