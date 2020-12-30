node {
    stage('代码拉取'){
     echo '代码拉取';
     checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '80cdc0d2-dbc3-4705-9396-65d339b5e9da', url: 'https://github.com/weienbulisi/crossgate-gateway.git']]])
    }
    stage('代码构建'){
      bat '''mvn clean '''
      bat '''mvn clean install'''
    }
    stage('镜像制作'){
      bat '''docker build -t test:v2 .'''  
    }
    stage('容器启动'){
      bat '''docker run -d  -p 8888:8888 test:v2'''  
    }

}
