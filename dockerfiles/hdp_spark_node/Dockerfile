#
#
#
FROM hwxu/hdp_python27_node
MAINTAINER Rich Raposa, rich@hortonworks.com

#Install Fortran package needed by Spark MLLib
RUN yum -y install gcc-gfortran --enablerepo=updates 

#Install Spark
RUN wget http://public-repo-1.hortonworks.com/spark/centos6/tar/spark-1.0.1.2.1.3.0-563-bin-2.4.0.2.1.3.0-563.tgz -O /tmp/spark.tgz
RUN tar -C /usr/lib -zxvf /tmp/spark.tgz
RUN ln -s /usr/lib/spark-1.0.1.2.1.3.0-563-bin-2.4.0.2.1.3.0-563/ /usr/lib/spark
RUN rm -f /tmp/spark.tgz

# Set environment variables needed to run Spark on YARN
RUN echo "export YARN_CONF_DIR=/etc/hadoop/conf" >> /etc/bashrc
RUN echo "export SPARK_JAR=/usr/lib/spark/lib/spark-assembly-1.0.1.2.1.3.0-563-hadoop2.4.0.2.1.3.0-563.jar" >> /etc/bashrc
RUN echo "export SPARK_WORKER_MEMORY=512m" >> /etc/bashrc
RUN echo "export SPARK_MASTER_MEMORY=512m" >> /etc/bashrc
RUN echo "export MASTER=yarn-client" >> /etc/bashrc
RUN echo "export SPARK_HOME=/usr/lib/spark" >> /etc/bashrc
RUN echo "export PYTHONPATH=\$SPARK_HOME/python/:\$PYTHONPATH" >> /etc/bashrc
RUN echo "export PYTHONPATH=\$SPARK_HOME/python/lib/py4j-0.8.1-src.zip:\$PYTHONPATH" >> /etc/bashrc
RUN echo "export SPARK_YARN_USER_ENV=\"PYTHONPATH=/usr/lib/spark/python/lib/py4j-0.8.1-src.zip:/usr/lib/spark/python/:\$PYTHONPATH\"" >> /etc/bashrc
RUN echo "export PYSPARK_PYTHON=/usr/local/bin/python2.7" >> /etc/bashrc
RUN echo "export PATH=\$PATH:/usr/lib/spark/bin" >> /etc/bashrc

