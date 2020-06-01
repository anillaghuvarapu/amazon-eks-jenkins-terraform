Continuous Intergration on Amazon EKS

Prerequisites
To implement the instructions in this post, you will need the following accounts:

An AWS account – how to create a new AWS account
A Docker hub account – how to register for docker id
A GitHub account – sign up for a new GitHub account

Sample Application Build Status
Understanding the Spring Petclinic application with a few diagrams
Running petclinic locally
Petclinic is a Spring Boot application built using Maven. You can build a jar file and run it from the command line:

git clone https://github.com/anillaghuvarapu/amazon-eks-jenkins-terraform
cd amazon-eks-jenkins-terraform
./mvnw package
java -jar target/*.jar
You can then access petclinic here: http://localhost:8080/
Or you can run it from Maven directly using the Spring Boot Maven plugin. If you do this it will pick up changes that you make in the project immediately (changes to Java source files require a compile as well - most people use an IDE for this):

./mvnw spring-boot:run
