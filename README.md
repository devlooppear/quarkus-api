# 🛠️ quarkus-api

Este projeto utiliza **Quarkus**, o framework Java **Supersônico** e **Subatômico**.

![Quarkus](https://img.shields.io/badge/Quarkus-v2.6.0-orange?style=flat-square)
![Java](https://img.shields.io/badge/Java-17-brightgreen?style=flat-square)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue?style=flat-square)

## 🌟 O que é Quarkus?

Quarkus é um framework desenvolvido para facilitar a criação de aplicações Java otimizadas para ambientes em nuvem e microserviços. Ele se destaca por sua **inicialização rápida** e **menor consumo de memória**, sendo ideal para aplicações nativas em contêineres.

Por isso, eu fiz uma base para meus projetos futuros, onde deixei mais acessível a configuração, misturando o `.env` e o `src/main/resources/application.properties`. Dessa forma, consigo proteger mais as variáveis de ambiente e trocar de maneira fácil entre os ambientes, como **dev**, **prod** e **testes**.

Também coloquei um **Docker Compose** para que vocês possam setar facilmente o Dockerfile que desejarem, feito pelo Quarkus. Além disso, configurei um ambiente mais facilitado para APIs REST, incluindo as bibliotecas de **JPA** e **Hibernate** para ORM, e **Lombok** para não ter que escrever um monte de getters e setters. Hahahah.

Eu achei o Quarkus muito da hora e espero que gostem também! Quando começo um projeto, pode ser meio complicado, então gosto de primeiro deixar um bom ambiente para desenvolver. Imagino que muita gente passe pelo mesmo, por isso fiz esse projeto aqui e estou tentando deixar a documentação bem acessível.

### 🚀 Principais Vantagens do Quarkus em Relação ao Spring Boot

- **Desempenho**: Inicialização mais rápida e uso reduzido de memória.
- **Compilação Nativa**: Suporte à GraalVM para criar executáveis nativos que melhoram ainda mais o desempenho.
- **Live Coding**: Modo de desenvolvimento que permite ver mudanças no código em tempo real, sem reiniciar a aplicação.
- **Facilidade de Integração**: Extensões para conectar facilmente com bancos de dados, serviços REST, entre outros.

## 🛠️ Rodando a Aplicação em Modo de Desenvolvimento

Antes de rodar a aplicação, copie o arquivo de exemplo de variáveis de ambiente para um novo arquivo `.env`. Você pode fazer isso com o seguinte comando:

```bash
cp .env.example .env
```

Depois, para rodar sua aplicação em modo de desenvolvimento que habilita o live coding, use:

```bash
./mvnw compile quarkus:dev
```

- Após iniciar a aplicação, você pode acessá-la em http://localhost:8080/hello.

- NOTA: Quarkus agora inclui uma Dev UI, que está disponível apenas em modo de desenvolvimento em http://localhost:8080/q/dev/.

📦 Empacotando e Rodando a Aplicação
A aplicação pode ser empacotada usando:

```bash
./mvnw package
```

Isso produz o arquivo quarkus-run.jar no diretório target/quarkus-app/. Você pode rodar a aplicação usando:

```bash
java -jar target/quarkus-app/quarkus-run.jar
```

Se você quiser criar um über-jar, execute o seguinte comando:

```bash
./mvnw package -Dquarkus.package.jar.type=uber-jar
```

A aplicação empacotada como um über-jar pode ser executada com:

```bash
java -jar target/*-runner.jar
```

🥇 Criando um Executável Nativo
Você pode criar um executável nativo usando:

```bash
./mvnw package -Dnative
```

Ou, se não tiver o GraalVM instalado, você pode construir o executável nativo em um contêiner:

```bash
./mvnw package -Dnative -Dquarkus.native.container-build=true
```

O executável nativo pode ser executado com:

```bash
./target/quarkus-api-1.0.0-SNAPSHOT-runner
```

Para mais informações sobre a criação de executáveis nativos, consulte a documentação do Quarkus.

🚀 Rodar a Aplicação
Para executar a aplicação, utilize:

```bash
./mvnw quarkus:dev
```

## 🐳 Dockerfiles

No diretório `src/main/docker`, você encontrará vários **Dockerfiles** que facilitam o empacotamento e a execução da sua aplicação Quarkus:

### 📦 Dockerfiles Disponíveis:

- **`Dockerfile.jvm`**:  
  Para rodar a aplicação na JVM, ideal para desenvolvedores que preferem a execução padrão.

- **`Dockerfile.legacy-jar`**:  
  Para aplicações que requerem o uso de JARs legados.

- **`Dockerfile.native`**:  
  Para construir uma imagem nativa com o GraalVM, proporcionando melhor desempenho e menores tempos de inicialização.

- **`Dockerfile.native-micro`**:  
  Ideal para microserviços, otimizando a imagem para ser leve e eficiente.

## ⚙️ Configuração do Banco de Dados

Para mais informações sobre como configurar o banco de dados PostgreSQL, consulte as seguintes guias:

- **[Hibernate ORM com Panache](https://quarkus.io/guides/hibernate-orm-panache)**: Simplifique seu código de persistência com o Hibernate ORM.
- **[Driver JDBC - PostgreSQL](https://quarkus.io/guides/datasource)**: Conecte-se ao banco de dados PostgreSQL via JDBC.
- **[RESTEasy Classic](https://quarkus.io/guides/resteasy)**: Framework para implementar serviços REST.

## 📚 Código Fornecido

- **[Hibernate ORM](https://quarkus.io/guides/hibernate-orm)**: Crie sua primeira entidade JPA. [Mais informações](https://quarkus.io/guides/hibernate-orm).
- **[RESTEasy JAX-RS](https://quarkus.io/guides/resteasy)**: Inicie facilmente seus serviços RESTful. [Mais informações](https://quarkus.io/guides/resteasy).

## 🧹 Limpeza e Execução

`Nota`: Caso você mude as configurações, talvez seja necessário rodar:

```bash
./mvnw clean
```
