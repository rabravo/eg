alias java23='export JAVA_HOME=$(/usr/libexec/java_home -v 23)'
alias java20='export JAVA_HOME=$(/usr/libexec/java_home -v 20)'
alias java19='export JAVA_HOME=$(/usr/libexec/java_home -v 19)'
alias java17='export JAVA_HOME=$(/usr/libexec/java_home -v 17)'
alias java11='export JAVA_HOME=$(/usr/libexec/java_home -v 11)'
alias java8='export JAVA_HOME=$(/usr/libexec/java_home -v 1.8)'

# List all installed JVMs
/usr/libexec/java_home -V

# Switch manually to a specific version
export JAVA_HOME=$(/usr/libexec/java_home -v 23)

# Verify active version
java -version
