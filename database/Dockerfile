FROM docker.elastic.co/elasticsearch/elasticsearch:8.15.4

# Switch to root to handle permissions
USER root

# Add your custom configuration file
COPY elasticsearch.yml /usr/share/elasticsearch/config/

# Set environment variables
ENV discovery.type=single-node \
    xpack.security.enabled=false \
    ES_JAVA_OPTS="-Xms512m -Xmx512m" \
    bootstrap.memory_lock=true \
    network.host=0.0.0.0

# Create data directory and set permissions
RUN mkdir -p /usr/share/elasticsearch/data && \
    chown -R elasticsearch:elasticsearch /usr/share/elasticsearch/config/elasticsearch.yml && \
    chown -R elasticsearch:elasticsearch /usr/share/elasticsearch/data && \
    chmod -R 777 /usr/share/elasticsearch/data

# Expose Elasticsearch ports
EXPOSE 9200 9300

# Switch back to elasticsearch user for security
USER elasticsearch

# Set default command
CMD ["elasticsearch"]