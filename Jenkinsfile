pipeline{
    agent {
        label 'default'
    }
    tools {
        terraform 'terraform-11'
    }
    
    stages{
        stage('Git Checkout'){
            steps{
                git 'https://github.com/momomohag/terraform-project.git'
            }
        }
        stage('Get Directory') {
            steps{
                println(WORKSPACE)
            }
        }
        stage('Terraform init'){
            steps{
                sh 'terraform init'
            }
        }
        stage('Terraform Apply'){
            steps{
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: "mohamed",
                    accessKeyVariable: 'AKIAZNPLOABYSHBYHKXG',
                    secretKeyVariable: '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']]) {
                sh 'terraform apply --auto-approve'
                }
            }
        }
    }
}
