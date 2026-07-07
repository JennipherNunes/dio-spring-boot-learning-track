# DIO Spring Boot - Final Project 05: Spring AI (budgeting)

## Introduction

This final module applies Spring AI in a budgeting API while preserving the same layered architecture used across the track.

The goal is to integrate AI capabilities without bypassing domain and use case boundaries.

## Code Context

The project processes voice commands to create and query financial transactions.

Primary flow:

1. Client uploads an audio file.
2. Audio is transcribed into text.
3. The model selects an application tool/use case.
4. The use case persists or queries transaction data.
5. The final response is converted to audio.

## Project Structure

- `src/main/java/dio/budgeting/domain`
  - Domain model and repository contract.
- `src/main/java/dio/budgeting/application`
  - Use cases used by both REST and AI tool calling.
- `src/main/java/dio/budgeting/infrastructure`
  - HTTP adapters, JPA adapters, and integration glue.

## Module-Specific Topics

### Speech-to-text

- Uses `TranscriptionModel` for audio transcription.
- Model settings are configured in `application.properties`.

### Tool calling

- `ChatClient` registers use-case tools.
- `@Tool` methods expose business capabilities to the model.

### Text-to-speech

- `TextToSpeechModel` produces MP3 output from final text.
- AI endpoint returns generated audio.

## Spring AI Documentation

- Spring AI Reference: https://docs.spring.io/spring-ai/reference/index.html
- ChatModel API: https://docs.spring.io/spring-ai/reference/api/chatmodel.html
- ChatClient API: https://docs.spring.io/spring-ai/reference/api/chatclient.html
- Tools API: https://docs.spring.io/spring-ai/reference/api/tools.html
- Audio Transcriptions API: https://docs.spring.io/spring-ai/reference/api/audio/transcriptions.html
- Audio Speech API: https://docs.spring.io/spring-ai/reference/api/audio/speech.html

## Shared Architecture References

Common architecture concepts are documented in the root README:

- [DDD layers](../README.md#ddd-layered-architecture)
- [Class vs record](../README.md#java-class-vs-java-record-in-domain-modeling)
- [Strong typed identifiers](../README.md#strong-typed-identifiers)
- [Repository pattern](../README.md#repository-pattern)
- [Use cases and Clean Architecture](../README.md#use-cases-and-clean-architecture)
- [Docker Compose support](../README.md#docker-compose-support-in-development)

## How to Run

Set your OpenAI API key:

```bash
export OPENAI_API_KEY="your_api_key_here"
```

Run the application and tests:

```bash
./gradlew bootRun
./gradlew test
```

## Notes

- Educational final project focused on AI plus architectural discipline.
- External provider integration tests may require active credentials.

# Minha Evolução no Projeto

## O que o projeto faz

Este projeto é uma API de orçamento desenvolvida com Spring Boot e Spring AI.  
A aplicação recebe comandos financeiros por áudio, transforma o áudio em texto, interpreta a intenção com IA e executa ações relacionadas a transações financeiras.

## Como executar a aplicação

Para executar o projeto completo, é necessário ter:

- Java instalado;
- Gradle;
- Docker Desktop;
- uma chave da OpenAI configurada na variável `OPENAI_API_KEY`.

O projeto utiliza Docker para subir o banco de dados MySQL e Spring AI para integração com os modelos de IA.

Durante meus testes, consegui importar o projeto no Eclipse, configurar o Gradle, instalar o Lombok e executar a aplicação até a etapa em que foi identificado que o Docker Desktop era necessário.

## Melhoria implementada

Como evolução simples do projeto, foi adicionada uma documentação mais clara sobre o funcionamento da aplicação, seus requisitos e o fluxo principal.

Também foi proposta uma melhoria de validação para o fluxo de transações financeiras: impedir o cadastro de transações com valor menor ou igual a zero, evitando dados financeiros inválidos.

## Tecnologias usadas

- Java
- Spring Boot
- Spring AI
- Gradle
- Lombok
- Docker
- MySQL
- OpenAI API

## Como testar o fluxo principal

O fluxo principal esperado é:

1. Enviar um arquivo de áudio para a API.
2. O áudio é transcrito para texto.
3. A IA interpreta o comando.
4. A aplicação executa a ação solicitada.
5. A resposta é retornada ao usuário.

Para testar completamente, é necessário configurar o Docker Desktop e a variável `OPENAI_API_KEY`.

## O que aprendi

Durante este desafio, aprendi sobre:

- estrutura de projetos Spring Boot;
- importação de projetos Gradle no Eclipse;
- configuração do Lombok;
- uso de Docker para banco de dados;
- integração de IA com aplicações Java;
- importância da documentação em projetos no GitHub.
