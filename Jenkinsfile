pipeline 
{
    agent any
    stages
    {
        stage("Build")
        {
            steps
            {
                echo "Building with Maven"
            }
        }

        stage("Unit and Integration Testing")
        {
            steps
            {
                echo "Testing"
            }
        }

        stage("Deploy")
        {
            steps
            {
                echo "Deploying"
            }
        }

        stage("Complete")
        {
            steps
            {
                echo "Project completed"
            }
        }
        
    }
    
    post
    {
        success
        {
            mail to: "mattybravo19@gmail.com",
            subject: "Build Status Email",
            body: "Build was successful"
        }
    }
}
