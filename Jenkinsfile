   /* groovylint-disable-next-line CompileStatic */
 pipeline {
      agent { node { label 'Windows' } }

      environment {
                  dotnet = 'C:\\Program Files\\dotnet\\'
      }

      triggers {
               pollSCM '* * * * *'
      }

      stages {
            stage('Checkout') {
                  steps {
                        git url:'https://github.com/igho4j/msbuild_project.git', branch: 'Master'
                  }
            }
            stage('Restore packages') {
                  steps {
                        bat 'dotnet restore C:\\jenkins_agent\\workspace\\MsBuild_Windows2\\ConsoleApp\\ConsoleApp\\ConsoleApp.csproj'
                  }
            }

            stage('Build') {
                  steps {
                        bat 'dotnet build C:\\jenkins_agent\\workspace\\MsBuild_Windows2\\ConsoleApp\\ConsoleApp\\ConsoleApp.csproj --configuration Release'
                  }
            }
            stage('Test: Unit Test') {
                  steps {
                        bat 'dotnet test C:\\jenkins_agent\\workspace\\MsBuild_Windows2\\ConsoleApp\\UnitTestProject\\UnitTestProject.csproj'
                  }
            }

            stage('Publish') {
                  steps {
                        bat 'dotnet publish C:\\jenkins_agent\\workspace\\MsBuild_Windows2\\ConsoleApp\\ConsoleApp\\ConsoleApp.csproj'
                  }
            }
      }
 }
