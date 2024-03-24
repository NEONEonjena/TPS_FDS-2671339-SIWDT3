# Use a base image with PHP and Apache
FROM php:8.0.26-apache

# Set the working directory to /var/www/html
WORKDIR /var/www/html

# Copy the CodeIgniter 3 application to the working directory
COPY . /var/www/html

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Enable Apache rewrite module
RUN a2enmod rewrite

# Install PHP extensions required by CodeIgniter
RUN docker-php-ext-install mysqli

# Copy the FPDF class file to the CodeIgniter application directory
COPY ./application/third_party/fpdf/fpdf.php /var/www/html/application/third_party/fpdf/fpdf.php

# Expose port 80
EXPOSE 80

# Start Apache web server
CMD ["apache2-foreground"]
