# Database Population Script

This script automates the process of creating tables and inserting mock data into a PostgreSQL database. It prompts the user for details such as the number of rows to insert and database connection information.

## Prerequisites

1. **Clone the repository** to your local machine:

   ```bash
   $ git clone https://github.com/CreoWis/propilot-backend-app.git
   ```

2. Navigate to the directory containing the script files and install required Node packages

   ```bash
   $ cd database-population-script
   $ npm install pg readline uuid
   ```

## Usage

1. Run the Script:

   - Execute the script using Node.js
     ```bash
     $ node main.js
     ```

2. After executing, follow the prompts:

   - Enter the number of rows/data to insert into the database.
   - Please provide the following database connection details: user, host, database name, password, and port. If you choose to skip any connection detail, the script will assign the default value for that particular detail.

3. Script Execution:
   - The script creates tables defined in CreateQueries.js.
   - It generates mock data using GenerateMockData.js and inserts it into the tables.
   - You can observe in the terminal that the script successfully executes queries for all tables without any errors.

## Files Description

### main.js file:

This script connects to a PostgreSQL database, creates tables based on predefined SQL queries, generates mock data for each table, and inserts the generated data into the respective tables.

The script consists of the following components:

<b>1. Database Connection Setup:</b> Prompts the user for database connection details such as username, host, database name, password, and port number.

<b>2. Table Creation and Data Insertion:</b> Utilizes predefined SQL queries stored in the CreateQueries.js module to create tables in the database schema. Then, it generates mock data using the GenerateMockData.js module and inserts this data into the corresponding tables.

<b>3. Input Handling:</b> Includes functions to get user input for the number of rows of mock data to insert and database connection details.

<b>4. Execution:</b> The main() function coordinates the entire process by calling the necessary functions in sequence. Upon completion, it closes the database connection.

The script facilitates database initialization and population, making it convenient for setting up a database for development or testing purposes.

### CreateQueries.js file:

This module contains a collection of SQL queries for creating database tables in a PostgreSQL database schema. Each query is defined as a template string within an object, with the table name dynamically generated based on predefined mappings.

Usage:

<b>1. Importing the Module:</b> Import the module into your main.js file using require or import statements.

<b>2. Accessing Queries:</b> Access the desired table creation query by referencing the corresponding key in the createQueries object.

<b>3. Executing Queries:</b> Execute the retrieved query using your preferred database client or ORM library.

Notes:

1.  Ensure that the necessary database connection is established before executing these queries.

2.  Customize the data types, constraints, and table definitions as per your specific database schema requirements.

3.  This module assumes the usage of PostgreSQL as the database management system.

### GenerateMockData.js file:

The mock data generation file provides functionality for generating simulated data to populate a PostgreSQL database. It includes functions to create mock data for different tables within the database schema, facilitating development, testing, and demonstration tasks.

Usage:

1.  Import the 'generateMockDataForTable' and 'mockData' objects from the file.

2.  Utilize the 'generateMockDataForTable' function to create mock data for specific tables by providing the table name and the desired number of rows.

3.  Access the generated mock data through the 'mockData' object, which contains simulated data for various tables.

### TableNames.js file:

The file contains mappings between table names and their corresponding index numbers, facilitating bidirectional conversion between table names and their numeric representations. This mapping aids in referencing database tables programmatically using numeric indices or human-readable table names.

Usage:

1.  Import the 'tableToIndex' and 'indexToTable' objects from the file.

2.  Access the 'tableToIndex' object to retrieve the numeric index of a table by providing its name.

3.  Utilize the 'indexToTable' object to obtain the name of a table based on its numeric index.

Notes:

1.  Ensure consistency between table names and their respective indices to prevent mapping errors.

2.  Use these mappings to streamline database operations and enhance code readability when working with tables in a PostgreSQL database.

3.  Validate input and handle edge cases when converting between table names and indices to prevent unexpected behavior.

## Customization

1.  If you want to add your table, first go to the TableNames.js file and add your file name with index in the tabletoIndex object and indexToTable object.
2.  Following the specifications, please make sure to add your table definition in the CreateQueries.js file with the required format.
3.  If your table relies on relationships with other tables through foreign keys, ensure to include these foreign key definitions within the designated section and table definition above the respective tables. This allows tables dependent on this particular table to utilize primary keys as foreign keys.
4.  It's essential to properly define your table structure to avoid errors like ReferenceError after executing the script.
5.  Additionally, remember to include the necessary function inside the GenerateMockData.js file, formatted correctly, to facilitate the addition of data/rows into your newly created tables.

## Additional Information

1.  This script uses the 'pg' package for PostgreSQL database connectivity, the 'readline' module for user input, and the 'uuid' package for generating universally unique identifiers.
2.  Error handling is implemented to handle exceptions during table creation and data insertion gracefully.

## Contact

For any inquiries or support, please feel free to reach out via email at pratyaksh22official@gmail.com
