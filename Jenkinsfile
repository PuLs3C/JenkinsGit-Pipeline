pipeline 
{
    agent any
    stages
    {
        stage("Build")
        {
            echo "Building..."
        }
        post
        {
            success
            {
                mail to: "mattybravo19@gmail.com"
                subject: "Build Status Email"
                body: "Build was successful"
            }
        }
    }


}