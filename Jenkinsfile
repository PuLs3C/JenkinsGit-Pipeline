pipeline 
{
    agent any
    stages
    {
        stage("1: Build")
        {
            steps
            {
                echo "Utilise Maven to Compile and package the code"
            }
        }

        stage("2. Unit and Integration Testing")
        {
            steps
            {
                echo "Perform unit and integration tests using JUnit and Selenium"
            }

            post
            {
                failure
                {
                    emailext body: 'Unit and integration tests have failed',
                    subject: 'Project Testing: Failed',
                    to: 'mattybravo19@gmail.com'
                }

                success
                {
                    emailext body: 'Unit and integration tests were successful',
                    subject: 'Project Testing: Successful',
                    to: 'mattybravo19@gmail.com'
                 }
            }
        }

        stage("3. Code Analysis")
        {
            steps
            {
                echo "Use SonarQube to perform static code analysis that adheres to industry standards"
            }
        }

        stage("4. Security Scan")
        {
            steps
            {
                echo "Scan the code for any vulnerabilities or security issues using the plugins on SonarQube "
            }

            post
            {
                failure
                {
                    emailext body: 'Security scans complete, vulnerabilites or security issues were identified',
                    subject: 'Project Security Scan: Hazardous',
                    to: 'mattybravo19@gmail.com'
                }

                success
                {
                    emailext body: 'Security scans complete, no vulnerabilities or security risks were identified',
                    subject: 'Project Security Scan: Safe',
                    to: 'mattybravo19@gmail.com'
                }
            }

        }

        stage("5. Deploy to staging")
        {
            steps
            {
                echo "Deploy the application to the Ansible staging server "
            }
        }

        stage("6. Integration tests on staging")
        {
            steps
            {
                echo "Run integration tests in the staging environment to validate that all components work well together on Selenium "
            }
        }

        stage("7. Deploy to production")
        {
            steps
            {
                echo "Deploy the application to production with Docker"
            }
        }
    }
 
    post
    {
        failure
        {
            mail to: "mattybravo19@gmail.com",
            subject: "Project Pipeline: Failed",
            body: "The holistic pipeline package has failed"
        }

        success
        {
            mail to: "mattybravo19@gmail.com",
            subject: "Project Pipeline: Successful",
            body: "The holistic pipeline package was successful"
        }
    }
}

