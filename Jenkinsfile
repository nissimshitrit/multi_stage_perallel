def stages = 10
def parallelStage = 25
def run = [:]

for (int i = 0; i < stages; i++) {
  stage("stage_$i") {
    for (int j = 0; j < parallelStage; j++) {
      run["parallel_$j"] = {    
        node(){
          dockerImage =docker.image("alpine:3.16.2")
          dockerImage.pull()
          dockerImage.inside(){
            sh("sleep 2s")
          }
          return null
        }    
      }    
    }
    parallel run

  }
  run = [:]
}
