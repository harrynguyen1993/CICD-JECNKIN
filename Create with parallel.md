node("master") {
    stage("Stage 1") {
        echo "Stage 1 : Hello word demo"
        echo  "Stage param ${debug}"
    }
    stage("Parallel builds")
    parallel(
        "Thread 1 " : {
            node("master"){
                stage("Stage thread 1"){
                    echo 'Running on master'
                    sh 'echo ---------------; echo Hostname is $(hostname); echo Time is $(date); sleep 5; touch file.master'
                }
            }
        },
        "Thread 2 " : {
            node("auto_luan"){
                stage("Stage thread 2"){
                     echo 'Running on agent1'
                    sh 'echo ---------------; echo Hostname is $(hostname); echo Time is $(date); sleep 5; touch file.agent1'
                }
            }
        }
    )
    
    stage ('Closeup on master'){
        echo "Finish work done on master"
        sh 'echo Time is: $(date)'
    }
    
}
