FROM maven as build 
WORKDIR /app
COPY . .
RUN  mvn install

FROM openjdk
WORKDIR /app
COPY --from=build /app/target/payment-o.0.1-SNAPSHOT.jar /app
EXPOSE 8081
CMD ["java","-jar","payment-o.0.1-SNAPSHOT.jar"]

