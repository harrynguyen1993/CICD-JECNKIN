node {
    stage("Stage 1") {
        echo "Stage 1 : Hello word demo"
        echo  "Stage param ${debug}"
    }
     stage ("Stage 2") {
        echo "Stage 2 : Hello word stage 2"
    }
     stage("Stage 3") {
        echo "Stage 3 : Hello word stage 3"
    }
    
}
node ('auto_luan'){
    stage ('Build on agent1'){
        echo 'Running on agent1'
        sh 'hostname; touch file.agent1'
    }
}

node ('auto_luan2'){
    stage ('Build on agent2'){
        echo 'Running on agent2'
        sh 'hostname; touch file.agent2'
    }
}
