# jenkins-in-a-box

This is an example of testing Jenkins in Kubernetes with Jenkins helm chart

What was done was:

1. adding custom agents in additionalAgents
2. adding docker in docker additionalContainers. This might be useful for building images, even if I'm not sure that it's really necessary, so I've commented it
3. added some missing plugins. The alternatice is creating a custom jenkins image and install them there.
4. added some examples of pipelines in examples/pipelines

## How to start it. 

```bash
helm install jenkins jenkins
```

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
