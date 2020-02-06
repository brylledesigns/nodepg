# Database Implementation on a Node JS enviroment

### Initializing your repository
    This initializes your repository to be ready to be added with npm

    CLI command: npm init -y

### Installing dependencies
    It is a requirment to install the dependencies of the PostgreSQL because obviuosly you are using Postgre as your server-side language.

    CLI command: npm install --save pg

### Create an index.js file in youor reposityory
    > Create a variable Pool that requires to integrate with the Postgre

        const { Pool } = require('pg')

    >Setup your pool variable with the credentials of your database

        const pool = new Pool({
        user: `${process.env.DB_USER}`,
        host: `${process.env.DB_HOST}`,
        database: `${process.env.DB_DATABASE}`,
        password: `${process.env.DB_PASSWORD}`,
        port: `${process.env.DB_PORT}`,
        ssl: true
    })

    >Now you create a query

        pool.query('SELECT * FROM books', (error, results) => {
            if(error) {
                throw error
            }
            console.log(results.rows)
        })