To manage Zookeeper files, you need to set up the zookeeper cli tools:

    unzip /opt/apache-solr-4.0.0/dist/apache-solr-4.0.0.war -d /tmp/solr-war
    mkdir /opt/zkcli
    cp /tmp/solr-war/WEB-INF/lib/* /opt/zkcli/
    echo 'java -classpath ".:/opt/zkcli/*" org.apache.solr.cloud.ZkCLI ${1+"$@"}' > /opt/zkcli/zkcli.sh
    chmod 755 /opt/zkcli/zkcli.sh

Now you can run the following to download the configuration:

    ./zkcli.sh -zkhost localhost -cmd downconfig -confdir /tmp/backup -confname openc

And to upload a new configuration:

    ./zkcli.sh -zkhost localhost -cmd upconfig -confdir /tmp/backup -confname openc
