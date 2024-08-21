# Cifras de Beale - Implementação em C

## Objetivo

Este projeto tem como objetivo implementar o método de codificação e decodificação das **Cifras de Beale**, uma técnica de criptografia que utiliza um livro ou texto como chave para codificar uma mensagem.

## Proposta do Código

O código desenvolvido permite a codificação e decodificação de mensagens utilizando o método das Cifras de Beale. A proposta é fornecer um programa que, dado um livro de cifras e uma mensagem original, gera uma mensagem codificada que pode ser posteriormente decodificada usando o mesmo livro de cifras e uma chave específica.

### Funcionalidades Principais

1. **Codificação de Mensagens**: Utiliza um livro de cifras para converter uma mensagem original em uma sequência de números, que representam as posições de palavras no livro, correspondentes a cada caractere da mensagem.
   
2. **Decodificação de Mensagens**: Reverte o processo de codificação, utilizando o livro de cifras e o arquivo de chaves para reconstruir a mensagem original a partir da sequência codificada.

### Linha de Comando

O programa pode ser executado através da linha de comando com a seguinte sintaxe:

```bash
./beale -e -b LivroCifra -m MensagemOriginal -o MensagemCodificada -c ArquivoDeChaves
```

## Estrutura do Projeto

- **`encode.c` e `encode.h`**: Contêm as funções responsáveis pela codificação da mensagem. A codificação é feita utilizando uma lista simplesmente encadeada, onde cada nodo contém um caractere da mensagem e uma lista de chaves associadas a esse caractere.

- **`decode.c` e `decode.h`**: Implementam a funcionalidade de decodificação, onde a mensagem codificada é revertida ao seu estado original usando o livro de cifras e as chaves.

- **`beale.c` e `beale.h`**: Contêm a lógica principal que integra as funções de codificação e decodificação, gerenciando a interação com o usuário via linha de comando.

- **`arq_chave.c` e `arq_chave.h`**: Responsáveis pelo gerenciamento dos arquivos de chaves, incluindo a leitura e armazenamento das chaves utilizadas no processo de codificação e decodificação.

## Decisões de Implementação

- **Estrutura de Dados**: Os caracteres foram armazenados em uma lista simplesmente encadeada alocada dinamicamente. Cada nodo da lista contém um caractere e uma lista de chaves associadas a ele. Essa abordagem permite uma manipulação eficiente dos dados durante a codificação e decodificação.

- **Geração de Chaves**: A geração de chaves é realizada através de uma varredura pelo Livro de Cifras. Cada caractere do livro é associado à sua posição na sequência, permitindo a criação de uma lista de chaves que podem ser usadas para codificar a mensagem.

- **Busca e Inserção**: Para cada caractere da mensagem original, o programa realiza uma busca na lista de caracteres do Livro de Cifras, identificando a posição da palavra correspondente. Essa posição é então armazenada como parte da chave de codificação.

## Como Compilar e Executar

### Compilação

Utilize o Makefile incluído para compilar o projeto. No terminal, dentro do diretório do projeto, execute:

```bash
make 
```
Este comando irá compilar todos os arquivos .c e gerar o executável beale.

### Execução

#### Para codificar uma mensagem:

```bash
./beale -e -b LivroCifra -m MensagemOriginal -o MensagemCodificada -c ArquivoDeChaves
```

#### Para decodificar uma mensagem:
```bash
./beale -d -b LivroCifra -m MensagemCodificada -o MensagemDecodificada -c ArquivoDeChaves
```


