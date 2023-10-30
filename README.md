
# Vue.js Project for Department and User Management

manage departments of a company and associate users with them. Use Vue.js to create an interactive and dynamic user interface that facilitates the management of departments and users in your organization, it is the consumption of the services created with the LARAVEL 10 project.

## Characteristics
- Creation, editing, deletion of departments.
- Association of users to departments.
- User login.
- Attractive and easy to use user interface.
- Communication with a backend API created in Laravel 10 for data storage

## System Requirements
Before you start working with this project, make sure you have the following installed:

- Node.js 
- Vue CLI (you can install it globally with npm install -g @vue/cli)

# Facility
Follow these steps to configure the project in your local environment:

1. Clone the repository from GitHub:

        https://github.com/YONFRV/VUE.git
        cd VUE
2. Install the project dependencies:

        npm install

# Setting
Before running the application, you must configure the Laravel 10 backend API URL that the Vue.js application will communicate to. Open the src/main.js file and set the window.axios.defaults.baseURL variable with the URL of your Laravel API:

        window.axios.defaults.baseURL = 'http://localhost:8000'

# Use
Once you have configured the project and the Laravel API URL, you can start the application:

        npm run dev

This will start a development server and provide you with a local URL where you can view the app in your browser. The Vue.js application will communicate with the Laravel API to perform department and user management operations.

# License

This project is distributed under the MIT license. See the LICENSE file for more details.
