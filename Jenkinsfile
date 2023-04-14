node {
  stage('Checkout') {
    // Checkout the source code from the repository
    git 'https://github.com/sumant039/Spring-Boot-Project.git'
  }
  
  stage('Build') {
    // Build the Java project using Maven
    sh 'mvn clean install'
  }
  
  stage('Test') {
    // Run unit tests using Maven
    sh 'mvn test'
  }
  
  stage('Deploy') {
  
  }
}

