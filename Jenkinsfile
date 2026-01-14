pipeline {
    agent any

    stages {
        stage('Build C++ Programs') {
            agent {
                docker {
                    image 'gcc:13'
                    args '-v $PWD:/workspace'
                }
            }
            steps {
                sh '''
                mkdir -p build
                for dir in source/*; do
                  if [ -f "$dir/main.cpp" ]; then
                    name=$(basename $dir)
                    g++ $(find "$dir" -name "*.cpp") -o "build/$name"
                    ./build/$name
                  fi
                done
                '''
            }
        }
    }
}