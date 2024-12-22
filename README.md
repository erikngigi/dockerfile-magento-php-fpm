# Magento Dockerfile Readme

## Overview

This repository contains a Dockerfile designed to create a containerized environment for running a Magento application. The image is based on PHP 8.1-FPM and includes all necessary dependencies, PHP extensions, and tools to facilitate Magento development and deployment.

---

## Features

- **Base Image**: Built on `php:8.1-fpm`.
- **Dependencies**: Includes libraries and tools required for Magento, such as `libgd`, `libxml2-dev`, `nodejs`, and `npm`.
- **PHP Extensions**: Pre-configured and installed extensions including `bcmath`, `mysqli`, `pdo_mysql`, `intl`, `soap`, and many others.
- **Composer**: Installed globally to manage Magento dependencies.
- **Yarn**: Added globally for front-end asset management.
- **Non-root User**: Application runs as a non-root user (`app`) for enhanced security.
- **Port 9100**: Configured for PHP-FPM to handle requests.

---

## How to Use

### Build the Docker Image

1. Clone this repository to your local machine:
   ```bash
   git clone <repository_url>
   cd <repository_directory>
   ```

2. Build the Docker image:
   ```bash
   docker build -t magento-image .
   ```

### Run the Container

1. Start a container using the built image:
   ```bash
   docker run -d --name magento-container -p 9000:9000 magento-image
   ```

2. Access the container shell:
   ```bash
   docker exec -it magento-container bash
   ```

---

## File Structure

- **Working Directory**: `/var/www/magento`
  - All Magento application files should be located in this directory.

---

## Installed Tools

- **Utilities**: `curl`, `vim`, `unzip`, `git`, `mycli`
- **Front-end**: `nodejs`, `npm`, `yarn`
- **PHP Extensions**: `bcmath`, `mysqli`, `pdo_mysql`, `gd`, `intl`, `soap`, `zip`, etc.
- **Other Extensions**: `imagick`, `apcu`, `swoole`

---

## Customization

- **PHP Configuration**: Modify the PHP settings as needed by creating a custom `php.ini` file and mounting it in the container.
- **Additional Extensions**: Add more PHP extensions by editing the `RUN docker-php-ext-install` section in the Dockerfile.

---

## Exposed Port

- **9100**: Default port for PHP-FPM. You can map it to a different port on your host machine if needed.

---

## Security Note

The container uses a non-root user (`app`) with limited privileges to run the application, enhancing security by minimizing the risk of privilege escalation.

---

## Troubleshooting

- **Permission Issues**: Ensure file ownership is set to the `app` user and group (`uid: 1000, gid: 1000`).
- **Dependencies Missing**: Update the Dockerfile to add any missing libraries or tools.

---

## Conclusion

This Dockerfile provides a robust, pre-configured environment for running Magento, making it easier to develop and deploy the application. Feel free to modify it as per your specific requirements.
