node {
    // Define a list of parameters
    def parametersList = ['param1', 'param2', 'param3']

    def parametersMap = [:]
    parametersMap['param1'] = ['var': 'value1']
    parametersMap['param2'] = ['var': 'value2']
    parametersMap['param3'] = ['var': 'value3']
    
    
    // checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/nadavamitay/tests.git']])
    
    // Iterate over each parameter and create a stage for it
    parametersList.each { param ->
        stage("Process ${param}") {
            echo "Processing ${param}"
            
            // Use Groovy environment variables to pass data to the shell script
            def parameterValue = parametersMap[param]?.var
            env."PARAM_${param}" = parameterValue
            
            sh """
                #!/bin/bash
                echo "Parameter is ${param}"
                echo "Parameter value from map: \$PARAM_${param}"
                # Additional commands can be added here
            """
        }
    }
}
