# AngularApp

This project was generated with Angular CLI version 16.1.5.

## Development Server

To start the development server, run the command `ng serve`. Navigate to http://localhost:4200/ in your browser. The application will automatically reload if you change any of the source files.

## Code Scaffolding

You can generate a new component using the command `ng generate component component-name`. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

To build the project, run the command `ng build`. The build artifacts will be stored in the `dist/` directory.

## Running Unit Tests

To execute the unit tests using Karma, use the command `ng test`.

## Running End-to-End Tests

To execute end-to-end tests using a platform of your choice, use the command `ng e2e`. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Jenkins and Nginx Configuration

This project includes the configuration of Jenkins for Continuous Integration (CI) and Nginx as a web server to expose the Angular application on port 80.

### Jenkins Configuration

1. Ensure that you have Jenkins installed on your server. You can follow the installation instructions on the official Jenkins website.

2. Access the Jenkins web interface and follow the instructions to unlock Jenkins and set up the initial administrative user.

3. Install the necessary plugins in Jenkins to support building and running Angular projects. Some common tools include the Git, Maven, and Node.js plugins.

4. Create a new Jenkins pipeline project and select the "Pipeline" option as the project type.

5. Configure the Jenkins pipeline to monitor the Git repository of the Angular application and execute the `ng serve` command to start the local application server.

6. Test the pipeline manually or set up a webhook to trigger it automatically in response to changes in the Git repository.

### Nginx Configuration

1. Install Nginx on your server using the package manager. On Ubuntu, you can use the following commands:

```bash
sudo apt update
sudo apt install nginx
```

2. Open the Nginx server configuration file:

```bash
sudo nano /etc/nginx/sites-available/default
```
3. Replace the entire contents of the file with the following configuration block:

```bash
server {
    listen 80;
    server_name _;

    location / {
        proxy_pass http://127.0.0.1:4200;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    # Other configurations can be added here if needed.
}
```
4. Check your Nginx configuration for syntax errors:

```bash
sudo nginx -t
```
5. Restart Nginx to apply the changes:

```bash
sudo systemctl restart nginx
```

6. Now, your Angular application is being served by Jenkins and exposed through Nginx on port 80. You can access it in your browser by typing the server address, for example: http://192.168.1.60.

7. Feel free to copy and paste this updated README.md file into your repository to document the steps for configuring Jenkins and Nginx to run and expose the Angular application. If you have any further questions or need additional assistance, please let me know!
