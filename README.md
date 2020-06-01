# Continuous Intergration on Amazon EKS
<br />

## Prerequisites
To implement the instructions in this post, you will need the following accounts:

* An AWS account – [how to create a new AWS account](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)
* A Docker hub account – [how to register for docker id](https://success.docker.com/article/how-do-you-register-for-a-docker-id)
* A GitHub account – [sign up for a new GitHub account](https://help.github.com/en/github/getting-started-with-github/signing-up-for-a-new-github-account)








### Understanding the Spring Petclinic application with a few diagrams


### Running petclinic locally
Petclinic is a [Spring Boot](https://spring.io/guides/gs/spring-boot) application built using [Maven](https://spring.io/guides/gs/maven/). You can build a jar file and run it from the command line:


```
git clone https://github.com/anillaghuvarapu/amazon-eks-jenkins-terraform
cd amazon-eks-jenkins-terraform
./mvnw package
java -jar target/*.jar
```

Or you can run it from Maven directly using the Spring Boot Maven plugin. If you do this it will pick up changes that you make in the project immediately (changes to Java source files require a compile as well - most people use an IDE for this):

```
./mvnw spring-boot:run
```

Reference from AWS
