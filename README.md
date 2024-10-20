# jenkins-in-a-box

This is an example of testing Jenkins in Kubernetes with Jenkins helm chart

What was done was:

1. adding custom agents in additionalAgents
2. adding docker in docker additionalContainers (might be useful for building images, even if I'm not sure that it's really necessary)

## Examples of pipeline

### Maven

#### jdk 21
```
pipeline {
    agent {label "maven21"}
    stages {
        stage('Build') {
          steps {
            container('maven') {
              sh 'mvn --version'
                }
            }
        }
    }
}
```

#### jdk 17
```
pipeline {
    agent {label "maven"}
    stages {
        stage('Build') {
          steps {
            container('maven') {
              sh 'mvn --version'
                }
            }
        }
    }
}
```

### Python

```
pipeline {
    agent {label "python"}
    stages {
        stage('Build') {
          steps {
            container('maven') {
              sh 'python --version'
                }
            }
        }
    }
}
```
