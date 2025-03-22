#etapa de construção
FROM maven:3.4.3-openjdk-21 AS build
#FROM ubuntu: latest AS build


# definir o diretorio dentro do controller
WORKDIR /app


#copiar o pom.xml para o container
COPY pom.xml .
COPY src ./src

# compialr o mavem para compilar projeto e gerar o JAR file 
RUN mvn clean package -DskipTests


#etapa de execução
FROM openjdk:21-slim


#definir o diretorio de trabalho para a aplicação
WORKDIR /app


#copiar o jar construido na etapa anterior 
COPY --from=build /app/target/*.jar app.jar


#definir a porta que sera utilozada na aplicação
EXPOSE 8080


#comando para executar a aplicacao
ENTRYPOINT [ "java", "-jar", app.jar ]