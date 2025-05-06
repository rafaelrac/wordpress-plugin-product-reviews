FROM wordpress:latest

# Enable Apache mod_rewrite
RUN a2enmod rewrite

# Ensure Apache allows .htaccess overrides
RUN sed -i 's/AllowOverride None/AllowOverride All/' /etc/apache2/apache2.conf

# No need to copy post-init.sh as it's mounted as a volume in docker-compose.yml

# Restart Apache to apply changes
RUN service apache2 restart

# Set the user to root temporarily to avoid permission issues when running scripts
USER root

# Set executable permission for post-init.sh during container startup
RUN echo 'chmod +x /post-init.sh' >> /docker-entrypoint.sh

# Switch back to the default user
USER www-data
