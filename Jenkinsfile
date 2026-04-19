pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: alpine
            image: alpine:latest
            command:
            - cat
            tty: true
        '''
    }
  }
  stages {
    stage('拉取代码 (Checkout)') {
      steps {
        // 这行代码是魔法，它会让 Jenkins 自动拉取当前仓库的所有代码
        checkout scm 
        echo "代码拉取成功！"
      }
    }
    stage('构建与测试 (Build)') {
      steps {
        container('alpine') {
          echo "开始执行环境检查..."
          sh 'ls -al'
          sh 'cat README.md'
        }
      }
    }
  }
}
