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
                always
                {
                     // Capture the console log and save it to a file
                    def testLogs = currentBuild.rawBuild.getLog(1000).join("\n")
                    writeFile file: 'test-stage-log.txt', text: testLogs
                    archiveArtifacts artifacts: 'test-stage-log.txt'
                }
               

                failure
                {
                    emailext(
                        to 'mattybravo19@gmail.com',
                        subject 'Project Testing: Failed',
                        body 'Unit and integration tests have failed',
                        attachmentsPattern 'test-stage-log.txt'
                    )
                }

                success
                {
                    emailext(
                        to: 'mattybravo19@gmail.com',
                        subject: 'Project Testing: Successful',
                        body: 'Unit and integration tests were successful',
                        attachmentsPattern: 'test-stage-log.txt'
                    )

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
                always
                {
                    // Capture the console log and save it to a file
                    def securityLogs = currentBuild.rawBuild.getLog(1000).join("\n")
                    writeFile file: 'security-stage-log.txt', text: securityLogs
                    archiveArtifacts artifacts: 'security-stage-log.txt'
                }
           
                failure
                {
                    emailext(
                        to: 'mattybravo19@gmail.com',
                        subject: 'Project Security Scan: Hazardous',
                        body: 'Security scans complete, vulnerabilites or security issues were identified',
                        attachmentsPattern: 'security-stage-log.txt'
                    )
                }

                success
                {
                    emailext(
                    to: 'mattybravo19@gmail.com',
                    subject: 'Project Security Scan: Safe',
                    body: 'Security scans complete, no vulnerabilities or security risks were identified',
                    attachmentsPattern: 'security-stage-log.txt'   
                    ) 
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

